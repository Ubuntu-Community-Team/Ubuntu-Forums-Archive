---
title: "Add Logix EchoView Wireless Video Adapter...."
date: 2007-07-03
forum: Multimedia &amp; Video
---

### Post by arashiko28 on 2007-07-03
I have an HP Pavilion ze2000, with a Broadcom 4306 802.11 b/g wireless card. I have wireless network and don't exactly know where to put this post, but it does have a little of wireless.

In my university there are wireless projectors, using windows, you connect to the projector signal, open a web browser and it would download a software to control the projector and pc. Now the thing is that when i connect, it does not download the software, I need the wireless video adapter driver of the EchoView device from AddLogix, it is not available at the AddLogix web page, or at least not under the same name. The part number is MA-WL-DVI. I desperately need this!!! Please help!!!:confused:](*,)

---

### Post by arashiko28 on 2008-07-04
I have been working this thing around, got tired, disappointed and took it back. So, Now... I downloaded the program again, tried to install it through wine, but got an error message about missing DLL file mfc42.dll. I downloaded the file but now have this message:
> ~/Desktop$ wine AddLogixSetup.exe 
fixme:powrprof:DllMain (0x7e310000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
err:module:map_image Could not map section .text, file probably truncated
err:module:import_dll Loading library MFC42.DLL (which is needed by L"Z:\\home\\****\\Desktop\\AddLogixSetup.exe") failed (error c000007b).
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\****\\Desktop\\AddLogixSetup.exe" failed, status c0000135
****@****-laptop:~/Desktop$ fixme:powrprof:DllMain (0x7e310000, 0, 0x1) not fully implemented
wine: Call from 0x7b844cd0 to unimplemented function rpcrt4.dll.I_RpcExceptionFilter, aborting


Any ideas this time?

---

