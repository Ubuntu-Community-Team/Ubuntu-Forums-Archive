---
title: "Digital voice editor"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by scottym on 2007-03-29
I have installed the software that came with my sony p320 digital recorder and am trying to get it to run using wine. I get the following message when I do the wine program command:

libGL warning: 3D driver claims to not support visual 0x4b
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:cdrom:CDROM_DeviceIoControl Unsupported IOCTL 2d1400 (type=2d access=0 func=500 meth=0)
fixme:ole:CoRegisterMessageFilter message filter has been registered, but will not be used
wine: Call from 0x7ee6b2d0 to unimplemented function msvcrt.dll._mbsbtype, aborting
wine: Unimplemented function msvcrt.dll._mbsbtype called at address 0x7ee6b2d0 (thread 0015), starting debugger...
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
00000014 (D) (null)
        00000015    0
0000000a 
        0000000c    0
        0000000b    0
00000008 
        0000000d    0
        00000009    0


I don't dual boot so that is not an option for me. Is there anyway to get Digital Voice Editor to work with Ubuntu?

Thanks everyone for any help.

---

### Post by chadpete21 on 2007-05-10
I'm working on the same problem.  I was able to get one step further by overriding msvcrt in winecfg and placing msvcrt.dll in the system32 folder.  Now the program window appears, then shuts down again.  Maybe override every dll that is on the install CD and copy them into system32?

---

### Post by scottym on 2007-05-11
Seems like a lot of work. Let me know if it works. My system32 already has dozens of .dll's, have never tried to use wine for any other programs, so are all of them from the digital cd?

---

### Post by chadpete21 on 2007-05-14
OK, here's my solution: VMware Server.  After installing VMware Server I created a new Win XP virtual machine.  Because this is the only Windows app I need, I set the hard drive to 4GB max and the mem to 256.  Make sure you also enable the usb adapter and the sound adapter.  Once Windows is loaded, be sure to load VMware Tools from the VM menu in VMware Server.  Reboot the VM and then load the voice recorder app and any other Windows apps you need.  In order for the Windows VM to recognize devices, they have to have been plugged into your usb when you turned on the VM.  Then once Windows loads, enable individual devices through the VM menu and Removable Devices.  Windows should detect the device and you should be in business. 

Hope this helps...

---

