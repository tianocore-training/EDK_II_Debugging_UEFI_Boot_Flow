---?image=assets/images/gitpitch-audience.jpg
@title[EDK II UDK Debugger]
<br><br><br><br><br>
## <span class="gold"   >UEFI & EDK II Training</span>

#### EDK II Debugging  through UEFI Boot Flow

<br>
<span style="font-size:0.75em" ><a href='http://www.tianocore.org'>tianocore.org</a></span>
Note:
  PITCHME.md for UEFI / EDK II Training  EDK II Debugging  through UEFI Boot Flow Pres

  Copyright (c) 2019, Intel Corporation. All rights reserved.<BR>

  Redistribution and use in source (original document form) and 'compiled'
  forms (converted to PDF, epub, HTML and other formats) with or without
  modification, are permitted provided that the following conditions are met:

  1) Redistributions of source code (original document form) must retain the
     above copyright notice, this list of conditions and the following
     disclaimer as the first lines of this file unmodified.

  2) Redistributions in compiled form (transformed to other DTDs, converted to
     PDF, epub, HTML and other formats) must reproduce the above copyright
     notice, this list of conditions and the following disclaimer in the
     documentation and/or other materials provided with the distribution.

  THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR
  IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
  MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO
  EVENT SHALL TIANOCORE PROJECT  BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
  SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
  PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
  OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
  WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
  OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF
  ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.



---  
@title[Lesson Objective]
<BR>
### <p align="center"<span class="gold"   >Lesson Objective </span></p><br>

<!---  Add bullets using https://fontawesome.com/cheatsheet certificate
-->
<ul style="list-style-type:none">
 <li>@fa[certificate gp-bullet-magenta]<span style="font-size:0.9em">&nbsp;&nbsp;Debugging commands similar to all debuggers</span> </li><br>
 <li>@fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;Debugging UEFI Platform Initialization Boot Flow</span></li>
</ul>

---?image=assets/images/binary-strings-black2.jpg
@title[Debugging Commands Section]
<br><br><br><br><br><br><br>
### <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Debugging Commands</span>
<span style="font-size:0.9em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;CpuBreakpoint() added to Source</span>

Note:

---
@title[Source Level Debug Features]
<p align="right"><span class="gold" ><b>Source Level Debug Features</b></span></p>
<br>
@ul[no-bullet]
- <span style="font-size:01.0em" >&nbsp;<span style="background-color: #7030a0"><b>&nbsp;&nbsp;View call stack</b> &nbsp;&nbsp;</b></span><span style="background-color: #92d050"><b>&nbsp;Go&nbsp;</b></span></p>
- <span style="font-size:01.0em" >&nbsp;<span style="background-color: #BF5122">&nbsp;&nbsp;<b>Insert <font face="Consolas">CpuBreakpoint()</font></b>&nbsp;&nbsp;</span></span><br><br>
- <span style="font-size:01.0em" >&nbsp;<span style="background-color: #00b0f0">&nbsp;&nbsp;<b>View and edit local/global variables</b>&nbsp;&nbsp;</span></span><br><br>
- <span style="font-size:01.0em" >&nbsp;<span style="background-color: #202020"><b>&nbsp;&nbsp;Set breakpoint</b> &nbsp;&nbsp;</b></span><span style="background-color: #7030a0"><b>&nbsp;Step into/over routines&nbsp;</b></span></p>
- <span style="font-size:01.0em" >&nbsp;<span style="background-color: #e49436"><b>&nbsp;&nbsp;Go till</b> &nbsp;&nbsp;</b></span><span style="background-color: #92d050"><b>&nbsp;View disassembled code&nbsp;</b></span></p>
- <span style="font-size:01.0em" >&nbsp;<span style="background-color: #BF5122">&nbsp;&nbsp;<b>View/edit general purpose register values&nbsp;</b>&nbsp;&nbsp;</span></span><br>
@ulend

Note:

- use gdb help to see how to 

---
@title[CpuBreakpoint vs CpuDeadLoop  ]
<p align="right"><span class="gold" ><b><font face="Consolas">CpuBreakpoint Vs CpuDeadLoop</font> </b></span></p>

@snap[north-west span-45]
<br>
<br>
@box[bg-green-pp text-white rounded my-box-pad2  ](<p style="line-height:70%" ><span style="font-size:01.1em; font-family:Consolas;" >CpuBreakPoint<br>&nbsp;</span></p>)
<p align="Left" style="line-height:80%"><span style="font-size:0.8em" >When using a Software debugger: </span> </p>
<ul style="list-style-type:disc; line-height:0.7;">
   <li><span style="font-size:0.67em" >Visual Studio</span></li>
   <li><span style="font-size:0.67em" >GDB (<font face="Consolas">OvmfPkg</font> w/ qemu)</span></li>
   <li><span style="font-size:0.67em" >Intel<sup>&reg; </sup> UDK Debugger</span></li>
   <li><span style="font-size:0.67em" ><a href="https://www.windriver.com/">Windriver</a> Simics</span></li>
   <li><span style="font-size:0.67em" >Debug agent - <font face="Consolas">SourceLevelDebugPkg</font></span></li>
 </ul>
<br>
@snapend



@snap[north-east span-45]
<br>
<br>
@box[bg-green-pp text-white rounded my-box-pad2  ](<p style="line-height:70%" ><span style="font-size:01.1em; font-family:Consolas;" >CpuDeadLoop<br>&nbsp;</span></p>)
<p align="Left" style="line-height:80%"><span style="font-size:0.8em" >When using a Hardware debugger: </span> </p>
<ul style="list-style-type:disc; line-height:0.7;">
   <li><span style="font-size:0.67em" >In-Target Probe(ITP) - <a href="https://software.intel.com/en-us/system-studio/system-debugger">Intel<sup>&reg;</sup> System Studio</a></span></li>
   <li><span style="font-size:0.67em" >Intel<sup>&reg;</sup> SVT DCI Cable</span></li>
   <li><span style="font-size:0.67em" >Intel<sup>&reg;</sup> SVT Closed Chassis Adapter (CCA)</span></li>
   <li><span style="font-size:0.67em" >other 3<sup>rd</sup> party Hardware (i.e. <a href="http://www.lauterbach.com">Lauterbach</a> w/ JTAG)
</span></li>
</ul>
<br>
@snapend

@snap[south-west span-100]
<p style="line-height:70%" align="left"><span style="font-size:0.7em" >
The functions <font color="#A8ff60"><font face="Consolas">CpuBreakpoint()</font></font> and  <font color="#A8ff60"><font face="Consolas">CpuDeadLoop()</font></font> are part of the EDK II Base Libraries 
and can be compiled with any UEFI or PI Module at any phase of the boot flow (SEC, PEI, DXE, BDS, TSL)
</span> </p>
@snapend



Note:
---
@title[Special DCI Breakpoint w/ HW Debugger  ]
<p align="right"><span class="gold" ><b>Special DCI Breakpoint with HW Debugger </b></span></p>

@snap[north-west span-45]
<br>
<br>
@box[bg-green-pp text-white rounded my-box-pad2  ](<p style="line-height:70%" ><span style="font-size:01.1em; font-weight: bold;" ><font face="Consolas">CpuIceBreakPoint</font><br>&nbsp;</span></p>)
@snapend

@snap[north-west span-100]
<br>
<br>
<br>
<br>
<p align="Left" style="line-height:80%"><span style="font-size:0.8em" >
The Intel Architecture has a special op-code for a breakpoint:	<font face="Consolas">int1 </font><br>
Better than a <font face="Consolas">CpuDeadLoop()</font> since it halts the processor. 
</span> </p>
<ul style="list-style-type:disc; line-height:0.7;">
   <li><span style="font-size:0.67em" >Better trace information</span></li>
   <li><span style="font-size:0.67em" >Requires a HW Debugger w/ DCI capabilities to intercept the <font face="Consolas">int1</font> op code</span></li>
   <li><span style="font-size:0.67em" >Works with Intel<sup>&reg;</sup> System Studio Debugger:  <a href="https://software.intel.com/en-us/system-studio/choose-download"> Download </a> </span></li>
   <li><span style="font-size:0.67em" >There is no “C” equivalent – needs to be assembly code   </span></li>
</ul>
<br>
@snapend

---?image=assets/images/binary-strings-black2.jpg
@title[Debugging Thru Boot FlowSection]
<br><br><br><br><br><br><br>
### <span class="gold"  >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Debugging Thru Boot Flow</span>
<span style="font-size:0.9em" >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Add Breakpoints to Firmware Source Code</span>

Note:



---?image=/assets/images/slides/Slide8.JPG
<!-- .slide: data-transition="none" -->
@title[Debugging the Boot Phases]
<p align="center"><span class="gold" ><b>Debugging the Boot Phases</b></span></p>


Note:


+++?image=/assets/images/slides/Slide9.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Debugging the Boot Phases 02]
<p align="center"><span class="gold" ><b>Debugging the Boot Phases</b></span></p>


Note:


+++?image=/assets/images/slides/Slide10.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Debugging the Boot Phases 03]
<p align="center"><span class="gold" ><b>Debugging the Boot Phases</b></span></p>


Note:


+++?image=/assets/images/slides/Slide11.JPG
<!-- .slide: data-background-transition="none" -->
<!-- .slide: data-transition="none" -->
@title[Debugging the Boot Phases 04]
<p align="center"><span class="gold" ><b>Debugging the Boot Phases</b></span></p>


Note:


---?image=/assets/images/slides/Slide12.JPG
@title[Debugging the Boot Phases SEC]
<p align="center"><span class="gold" ><b>Debugging the Boot Phases - SEC</b></span></p>

<div class="left-2">
<span style="font-size:0.8em" >&nbsp;  </span>
</div>
<div class="right-2">
<p style="line-height:70%" align="left" ><span style="font-size:0.8em;" >
Debugging Sec phase<br>
Hardware debugger capable @color[yellow](only)
</span></p>
<ul style="list-style-type:disc">
 <li><span style="font-size:0.8em" >Break at the Reset Vector</span></li>
 <li><span style="font-size:0.8em" >Check temporary memory – CAR NEM </span></li>
 <li><span style="font-size:0.8em" >Check Intel® FSP API wrapper</span></li>
 <li><span style="font-size:0.8em" >Execute basic chipset & Memory init. </span></li>
 <li><span style="font-size:0.8em" >Enable the “C” Code</span></li>
 <li><span style="font-size:0.8em" >Transfer control to PEI</span></li>
 </ul>
</div>


Note:


SEC Must use hardware debugger, not Intel® UEFI Development Kit Debugger or any software debugger.
Intel® System Studio Debugger with minimum DCI cable will break at reset-vector

---?image=/assets/images/slides/Slide13.JPG
@title[Debugging the Boot Phases PEI]
<p align="center"><span class="gold" ><b>Debugging the Boot Phases - PEI</b></span></p>
<br>
<br>
<div class="left-1">
<span style="font-size:0.8em" >&nbsp;  </span>
</div>
<div class="right-1">
<ul style="list-style-type:disc">
 <li><span style="font-size:0.8em" >Use debugger prior to PEI Main</span></li>
 <li><span style="font-size:0.8em" >Check proper execution of PEI drivers </span></li>
 <li><span style="font-size:0.8em" >Execute basic chipset & Memory init. </span></li>
 <li><span style="font-size:0.8em" >Check memory availability</span></li>
 <li><span style="font-size:0.8em" >Complete flash accessibility</span></li>
 <li><span style="font-size:0.8em" >Execute recovery driver </span></li>
 <li><span style="font-size:0.8em" >Detect DXE IPL</span></li>
 </ul>
</div>


Note:

- SEC Must use hardware debugger, not Intel® UEFI Development Kit Debugger
- Begin using debugger prior to PEI Main
- Check proper execution of all PEI drivers 
- Execute basic chipset initialization 
- Execute memory initialization instructions
- Check availability of memory
- Complete flash accessibility
- Execute recovery driver if the recovery jumper is selected, and execution of recovery path if recovery is detected 
- Detection of DXE IPL PEIM which in turn detects and launches the DXE core

---
@title[PEI Phase: Trace Each PEIM]
<p align="center"><span class="gold" ><b>PEI Phase: Trace Each PEIM</b></span></p>
<br>
<span style="font-size:0.8em" >There is a loop function in : </span><br>
@fa[github gp-bullet-gold]<span style="font-size:0.8em">&nbsp;&nbsp;<a href="https://github.com/tianocore/edk2/tree/master/MdeModulePkg/Core/Pei/Dispatcher">MdeModulePkg/Core/Pei/Dispatcher/Dispatcher.c </a></span><br>
<span style="font-size:0.8em" >Add <font face="Consolas">CpuBreakpoint();</font> before launching each PEIM</span>

```c
VOID
PeiDispatcher (
  IN CONST EFI_SEC_PEI_HAND_OFF  *SecCoreData,
  IN PEI_CORE_INSTANCE           *Private
  )
{// ...
        // Call the PEIM entry point
        //
        PeimEntryPoint = (EFI_PEIM_ENTRY_POINT2)(UINTN)EntryPoint;
        PERF_START (PeimFileHandle, "PEIM", NULL, 0);
// Add a call to CpuBreakpoint();  approx. line 1004
        CpuBreakpoint();
        PeimEntryPoint(PeimFileHandle, (const EFI_PEI_SERVICES **) &Private->Ps);
```

Note:


- For Loop in Function: PeiDispatcher()
	- MdeModulePkg/Core/Pei/Dispatcher/Dispatcher.c

- Trace all PEIMs dispatched in PEIMAIN module 
- PeiDispatcher() function - set a break point at the main dispatch loop before each PEIM Entry
	- // Call the PEIM entry point
- 	CpuBreakpoint() ;
	- PeimEntryPoint(PeimFileHandle, (const EFI_PEI_SERVICES **) &Private->Ps);
- On breakpoint, step into function to trace PEIMs

---
@title[Check for transition from PEI to DXE]
<p align="center"><span class="gold" ><b>Check for transition from PEI to DXE</b></span></p>
<br>
<span style="font-size:0.8em" >Critical point before calling DXE in: </span><br>
@fa[github gp-bullet-gold]<span style="font-size:0.8em">&nbsp;&nbsp;<a href="https://github.com/tianocore/edk2/tree/master/MdeModulePkg/Core/Pei/PeiMain">MdeModulePkg/Core/Pei/PeiMain.c </a></span><br>
<span style="font-size:0.8em" >Add <font face="Consolas">CpuBreakpoint();</font> before entering DxeIpl</span>

```c
VOID
EFIAPI
PeiCore (
  IN CONST EFI_SEC_PEI_HAND_OFF        *SecCoreDataPtr,
  IN CONST EFI_PEI_PPI_DESCRIPTOR      *PpiList,
  IN VOID                              *Data
  )
{ // ...
  // Enter DxeIpl to load Dxe core.
  //
  DEBUG ((EFI_D_INFO, "DXE IPL Entry\n"));
// Add a call to CpuBreakpoint();  approx. line 468
  CpuBreakpoint();
  Status = TempPtr.DxeIpl->Entry (
                             TempPtr.DxeIpl,
                             &PrivateData.Ps,
                             PrivateData.HobList
 
```

Note:

There may also be issues with transition from 32 to 64 bit so this makes a good place to add a breakpoint


---
@title[Check for transition from DxeIpl to DXE]
<p align="center"><span class="gold" ><b>Check for transition from DxeIpl to DXE</b></span></p>
<span style="font-size:0.8em" >Critical point before calling DXE Core in: </span><br>
@fa[github gp-bullet-gold]<span style="font-size:0.8em">&nbsp;&nbsp;<a href="https://github.com/tianocore/edk2/tree/master/MdeModulePkg/Core/DxeIplPeim">MdeModulePkg/Core/DxeIplPeim/DxeLoad.c </a></span><br>
<span style="font-size:0.7em" >Before entering Dxe Core</span><span style="font-size:0.5em" >&nbsp;&nbsp;(&nbsp;Notice also this is a standalone module - DxeIpl.efi)</span>

```c
EFI_STATUS
EFIAPI
DxeLoadCore (
  IN CONST EFI_DXE_IPL_PPI *This,
  IN EFI_PEI_SERVICES      **PeiServices,
  IN EFI_PEI_HOB_POINTERS  HobList
  )
{ // ...
  // Transfer control to the DXE Core
  // The hand off state is simply a pointer to the HOB list
  //
// Add a call to CpuBreakpoint();  approx. line 790
  CpuBreakpoint();
  HandOffToDxeCore (DxeCoreEntryPoint, HobList);
  //
  // If we get here, then the DXE Core returned.  This is an error
```

Note:
- Check for transition from IPL to DXE

- MdeModulePkg/Core/DxeIplPeim/DxeLoad.c

- Verify address of DXE Core Entry point after IPL from PEI – DxeLoadCore function in DxeIpl->Entry()
- HandOffToDxeCore call (DxeCoreEntryPoint)
<pre>
 // Transfer control to the DXE Core
 // The hand off state is simply a pointer to the HOB list
 //
   CpuBreakpoint() ;
    HandOffToDxeCore (DxeCoreEntryPoint, HobList);
 //
 // If we get here, then the DXE Core returned.  This is an error
</pre>



---?image=/assets/images/slides/Slide17.JPG
@title[Debugging the Boot Phases DXE]
<p align="center"><span class="gold" ><b>Debugging the Boot Phases - DXE</b></span></p>
<br>
<br>
<div class="left-1">
<span style="font-size:0.8em" >&nbsp;  </span>
</div>
<div class="right-1">
<ul style="list-style-type:disc">
 <li><span style="font-size:0.8em" >Search for cyclic dependency check </span></li>
 <li><span style="font-size:0.8em" >Trace ASSERTs caused during DXE execution </span></li>
 <li><span style="font-size:0.8em" >Debug individual DXE drivers </span></li>
 <li><span style="font-size:0.8em" >Check for architectural protocol failure</span></li>
 <li><span style="font-size:0.8em" >Ensure BDS entry call</span></li>
</ul>
</div>


Note:

---
@title[DXE: Trace Each Driver Load]
<p align="center"><span class="gold" ><b>DXE: Trace Each Driver Load</b></span></p>
<br>
<span style="font-size:0.8em" >DXE Dispatcher calls to each driver's entry point in: </span><br>
@fa[github gp-bullet-gold]<span style="font-size:0.8em">&nbsp;&nbsp;<a href="https://github.com/tianocore/edk2/tree/master/MdeModulePkg/Core/Dxe/Image">MdeModulePkg/Core/Dxe/Image/Image.c </a></span><br>
<span style="font-size:0.8em" >Break every time a DXE driver is loaded. </span>

```c
EFI_STATUS
EFIAPI
CoreStartImage (
  IN EFI_HANDLE  ImageHandle,
  OUT UINTN      *ExitDataSize,
  OUT CHAR16     **ExitData  OPTIONAL
  )
{ // ...
    //
    // Call the image's entry point
    //
    Image->Started = TRUE;
// Add a call to CpuBreakpoint();  approx. line 1673
    CpuBreakpoint();
    Image->Status = Image->EntryPoint (ImageHandle, Image->Info.SystemTable);
```

Note:

- MdeModulePkg/Core/Dxe/Image/Image.c
- Image->EntryPoint() call in CoreStartImage
- remember to step "INTO" when it gets to desired module to debug
- Check if control transfers to image entry points
- System breaks here every time a new DXE driver is loaded. Step into this function to trace the driver.

- Image->Started = TRUE;
- CpuBreakpoint() ;
- Image->Status=Image->EntryPoint (ImageHandle, Image->Info.SystemTable);


---?image=/assets/images/slides/Slide19.JPG
@title[Debugging the Boot Phases BDS]
<p align="center"><span class="gold" ><b>Debugging the Boot Phases - BDS</b></span></p>
<br>
<br>
<div class="left-2">
<span style="font-size:0.8em" >&nbsp;  </span>
</div>
<div class="right-2">
<ul style="list-style-type:disc">
 <li><span style="font-size:0.8em" >Detect console devices (input and output) </span></li>
 <li><span style="font-size:0.8em" >Check enumeration of all devices’ preset </span></li>
 <li><span style="font-size:0.8em" >Detect boot policy</span></li>
 <li><span style="font-size:0.8em" >Ensure BIOS BDS “front page” is loaded</span></li>
</ul>
</div>


Note:

---
@title[BDS Phase – Entry Point]
<p align="center"><span class="gold" ><b>BDS Phase – Entry Point</b></span></p>
<br>
<span style="font-size:0.8em" >DXE call to BDS entry point in:</span><br>
@fa[github gp-bullet-gold]<span style="font-size:0.8em">&nbsp;&nbsp;<a href="https://github.com/tianocore/edk2/tree/master/MdeModulePkg/Core/Dxe/DxeMain">MdeModulePkg/Core/Dxe/DxeMain/DxeMain.c </a></span><br>
<span style="font-size:0.8em" >Add <font face="Consolas">CpuBreakpoint();</font> to break before BDS. </span>

```c
VOID
EFIAPI
DxeMain (
  IN  VOID *HobStart
  )
{ // ...
  // Transfer control to the BDS Architectural Protocol
  //
// Add a call to CpuBreakpoint();  approx. line 554
  CpuBreakpoint();
  gBds->Entry (gBds);

  //
  // BDS should never return
  //
  ASSERT (FALSE);
  CpuDeadLoop ();
```

Note:
- MdeModulePkg/Core/Dxe/DxeMain/DxeMain.c
- gBds->Entry (gBds); call in DxeMain
- Verify BDS Phase Entry
<pre>
	CpuBreakpoint();
	gBds->Entry (gBds);
	// BDS should never return
	ASSERT (FALSE);
	CpuDeadLoop ();
</pre>


---?image=/assets/images/slides/Slide21.JPG
@title[Debugging the Boot Phases Pre-Boot]
<p align="center"><span class="gold" ><b>Debugging the Boot Phases - Pre-Boot</b></span></p>
<br>
<br>
<div class="left">
<span style="font-size:0.8em" >&nbsp;  </span>
</div>
<div class="right">
<ul style="list-style-type:disc">
 <li><span style="font-size:0.8em" >“C” source debugging</span></li>
 <li><span style="font-size:0.8em" >UEFI Drivers  </span></li>
 <ul style="list-style-type:disc">
   <li><span style="font-size:0.6em" >Init - entry point</span></li>
   <li><span style="font-size:0.6em" >Supported</span></li>
   <li><span style="font-size:0.6em" >Start</span></li>
 </ul>
 <li><span style="font-size:0.8em" >UEFI Shell Applications</span></li>
 <ul style="list-style-type:disc">
   <li><span style="font-size:0.6em" >Entry point</span></li>
   <li><span style="font-size:0.6em" >Local variables</span></li>
 </ul>
 <li><span style="font-size:0.8em" ><font face="Consolas">CpuBreakpoint();</font></span></li>
 </ul>
</div>


Note:



---?image=/assets/images/slides/Slide22.JPG
@title[Debug in Pre-Boot – UEFI Shell]
<p align="right"><span class="gold" ><b>Debug in Pre-Boot – UEFI Shell Application</b></span></p>
<p style="line-height:75%" align="left" ><span style="font-size:0.8em" >
Add <font face="Consolas">CpuBreakpoint()</font> to SampleApp.c near the entry point
<br>
@size[.8em](Add SampleApp.inf to the platform .dsc file)
</span></p>

@snap[north-west span-50 ]
<br>
<br>
<br><br><br><br>
@box[bg-black text-white rounded my-box-pad2  ](<p style="line-height:60% "><span style="font-size:0.5em;" ><br><br>&nbsp;</span></p>)
@snapend



@snap[north-west span-49]
<br>
<br>
<br>
<br>
<br>
<p style="line-height:45%" align="left" ><span style="font-size:0.7em" ><br></span></p>

<p style="line-height:35%" align="left" ><span style="font-size:0.43em; font-family:Consolas;" >&nbsp;&nbsp;
 bash$ cd &lt;edk2 workspace directory&gt;<br>&nbsp;&nbsp;
 bash$ . edksetup.sh<br>&nbsp;&nbsp;
 bash$ build -m SampleApp/SampleApp.inf<br>&nbsp;&nbsp;
<br><br><br>&nbsp;
</span></p>
<p style="line-height:65%" align="left" ><span style="font-size:0.67em" >
Copy the binary SampleApp.efi to USB drive and run SampleApp.efi from UEFI Shell</span></p>
@snapend

Note:


---  
@title[Summary]
<BR>
### <p align="center"><span class="gold"   >Summary </span></p><br>

<!---  Add bullets using https://fontawesome.com/cheatsheet certificate
-->
<ul style="list-style-type:none">
 <li>@fa[certificate gp-bullet-magenta]<span style="font-size:0.9em">&nbsp;&nbsp;Debugging commands similar to all debuggers</span> </li><br>
 <li>@fa[certificate gp-bullet-cyan]<span style="font-size:0.9em">&nbsp;&nbsp;Debugging UEFI Platform Initialization Boot Flow</span></li>
</ul>


---?image=assets/images/gitpitch-audience.jpg
@title[Questions]
<br>
![Questions](/assets/images/questions.JPG) 

---
@title[return to main]
<p align="center"><span class="gold"   >@size[1.2em](<b>Return to Main Training Page</b>)</span></p>
<br>
<br>
<br>
<br>
<br>
<p align="center"><span style="font-size:0.9em">Return to Training Table of contents for next presentation <a href="https://github.com/tianocore-training/Tianocore_Training_Contents/wiki#schedule--outline">link</a></span></p>

@snap[north span-30 ]
<br>
<br>
<br>
<a href="https://github.com/tianocore-training/Tianocore_Training_Contents/wiki#schedule--outline">
![trainingLogo](/assets/images/returnTrainingLogo.png)</a>
@snapend


---?image=assets/images/gitpitch-audience.jpg
@title[Logo Slide]
<br><br><br>
![Logo Slide](/assets/images/TianocoreLogo.png =10x)


---
@title[Acknowledgements]
#### <p align="center"><span class="gold"   >Acknowledgements</span></p>

```c++
/**
Redistribution and use in source (original document form) and 'compiled' forms (converted
to PDF, epub, HTML and other formats) with or without modification, are permitted provided
that the following conditions are met:

Redistributions of source code (original document form) must retain the above copyright 
notice, this list of conditions and the following disclaimer as the first lines of this 
file unmodified.

Redistributions in compiled form (transformed to other DTDs, converted to PDF, epub, HTML
and other formats) must reproduce the above copyright notice, this list of conditions and 
the following disclaimer in the documentation and/or other materials provided with the 
distribution.

THIS DOCUMENTATION IS PROVIDED BY TIANOCORE PROJECT "AS IS" AND ANY EXPRESS OR IMPLIED 
WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND 
FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL TIANOCORE PROJECT BE 
LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES 
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, 
DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, 
WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) 
ARISING IN ANY WAY OUT OF THE USE OF THIS DOCUMENTATION, EVEN IF ADVISED OF THE POSSIBILITY 
OF SUCH DAMAGE.

Copyright (c) 2019, Intel Corporation. All rights reserved.
**/

```

