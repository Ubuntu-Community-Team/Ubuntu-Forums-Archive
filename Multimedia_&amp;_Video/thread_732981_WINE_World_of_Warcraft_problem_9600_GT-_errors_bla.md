---
title: "WINE World of Warcraft problem 9600 GT- errors black screen"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by Kenjitamura on 2008-03-23
Just installed World of Warcraft on WINE and run successfully but with a few threatening problems.  Using an Nvidia 9600 GT with Beta 171.06 drivers.  At first World of Warcraft started up great but I increased the detail levels a little from the video options and on reboot I got a black screen and system froze.  After deleting the Config.wtf file I can get on and play again (haven't been on more than 10 minutes) but at times my FPS drops to a level even lower than the nvidia 5200GO! on my laptop in the same areas.  Starting WINE there is a long list of error most of them related to my AMD 9500+ and some of them have occurred in large problems with other peoples systems.

> fixme:reg:GetSystemInfo unknown cpu family '16', please report ! (-> setting to 386)
fixme:reg:GetSystemInfo unknown cpu family '16', please report ! (-> setting to 386)
fixme:reg:GetSystemInfo unknown cpu family '16', please report ! (-> setting to 386)
fixme:reg:GetSystemInfo unknown cpu family '16', please report ! (-> setting to 386)
fixme:reg:GetSystemInfo unknown cpu family '16', please report ! (-> setting to 386)
fixme:reg:GetSystemInfo unknown cpu family '16', please report ! (-> setting to 386)
fixme:reg:GetSystemInfo unknown cpu family '16', please report ! (-> setting to 386)
fixme:reg:GetSystemInfo unknown cpu family '16', please report ! (-> setting to 386)
err:advapi:service_control_dispatcher pipe connect failed
fixme:reg:GetSystemInfo unknown cpu family '16', please report ! (-> setting to 386)
fixme:reg:GetSystemInfo unknown cpu family '16', please report ! (-> setting to 386)
fixme:reg:GetSystemInfo unknown cpu family '16', please report ! (-> setting to 386)
fixme:reg:GetSystemInfo unknown cpu family '16', please report ! (-> setting to 386)
fixme:reg:GetSystemInfo unknown cpu family '16', please report ! (-> setting to 386)
fixme:reg:GetSystemInfo unknown cpu family '16', please report ! (-> setting to 386)
fixme:reg:GetSystemInfo unknown cpu family '16', please report ! (-> setting to 386)
fixme:reg:GetSystemInfo unknown cpu family '16', please report ! (-> setting to 386)
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d090000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d090000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed78,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x34eccc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f29c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f400,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f57c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f574,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f4fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f4ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34efd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f118,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:reg:GetNativeSystemInfo (0x374027e4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7c5403e4) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmAssociateContextEx (0x20024, (nil), 16): stub


---

### Post by Kenjitamura on 2008-03-24
Update and bump.  WoW works again after driver reinstall (was forced to low graphics mode after wow crashed).  With settings on low the fps is about the same as my laptops 5200 go.  The game freezes if i try to mess with the refresh rate so i just leave it auto.  A 9600 GT shouldn't be performing this poor but I think the beta drivers are just crap and I'll have to wait out Nvidia's next driver release.  I've applied the registry tweak, am running in Opengl with direct rendering enabled, and have settings on low but my fps can still drop all the way down to 10 in shattrath.  Not cool, any tips?

---

