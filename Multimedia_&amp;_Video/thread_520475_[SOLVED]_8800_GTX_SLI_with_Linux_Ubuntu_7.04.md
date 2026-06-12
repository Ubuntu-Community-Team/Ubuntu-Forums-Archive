---
title: "[SOLVED] 8800 GTX SLI with Linux Ubuntu 7.04"
date: 2007-08-08
forum: Multimedia &amp; Video
---

### Post by astrofra on 2007-08-08
Hi there,

I've got 2 8800 GTX, running on an intel Dual Core, under Ubuntu 7.04.
The SLI is fully functionnal under Windows XP (on this machine), but won't activate on Linux.

Some info about my config' :

> X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux simu-pc 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686

> Driver Version : NVIDIA-Linux-x86-100.14.11

I did some tests, and both GeForce are functionnal under Linux, as X11 is running on the two boards alternatively. BUT, the SLI cannot be enabled.

In the xorg init log file, I get this error message : 

> 
(**) NVIDIA(0): Option "SLI" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): NVIDIA SLI auto-select rendering option.
(WW) NVIDIA(0): DamageEvents are not currently compatible with SLI.  Disabling
(WW) NVIDIA(0):     DamageEvents.
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:3:0:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize one NVIDIA graphics device!
(WW) NVIDIA(0): Failed to initialize SLI configuration.  Reason: One GPU
(WW) NVIDIA(0):     failed to initialize; Only one GPU will be used for this X
(WW) NVIDIA(0):     screen.
(II) NVIDIA(0): NVIDIA GPU GeForce 8800 GTX (G80) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 786432 kBytes
(--) NVIDIA(0): VideoBIOS: 60.80.06.00.02
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8800 GTX at PCI:1:0:0:
(--) NVIDIA(0):     Mitsubishi NFL9905 (CRT-1)
(--) NVIDIA(0): Mitsubishi NFL9905 (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (116, 117); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp


The most puzzling is that X11 is able to use the GeForce in PCI:1:0:0, and the other one in PCI:3:0:0. However, he's not able to activate both of same in SLI.

I went in the "Common problems" section, as suggested, but I admit having reach my Peter's threshold.

Here are a few diagnostic command I tried, according to the NVidia's documentation : 

> linux-user@simu-pc:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0191 (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation Unknown device 0191 (rev a2)


> linux-user@simu-pc:~$ lspci -t
-[0000:00]-+-00.0
           +-00.1
 (... removed blank lines here ...)
           +-02.1
           +-02.2
           +-03.0-[0000:01]----00.0
           +-09.0
           +-0a.0
           +-0a.1
           +-0b.0
           +-0b.1
           +-0d.0
           +-0e.0
           +-0e.1
           +-0e.2
           +-0f.0-[0000:02]----0b.0
           +-0f.1
           +-11.0
           +-12.0
           \-18.0-[0000:03]----00.0


Did anyone experience this issue before ? Is there any report of someone having 2 8800 GTX running under Linux in SLI ? Thanks for your help :)

---

### Post by tseliot on 2007-08-09
I think you should try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by astrofra on 2007-08-09
I did, and went to the SLIZONE forum as well :) 
I got some hints, but the issue is not solved yet. I'm still trying hard to get that SLI working.

In the meantime, please find attached my Nvidia-bug-report-log, that should include all the info relevant to my configuration. If someone is brave / clever enough to have a look, feel free to comment :)

Thanks in advance.

---

### Post by astrofra on 2007-08-10
Any idea someone ? :)

---

### Post by astrofra on 2007-08-10
ISSUE RESOLVED

Setting vmalloc=256MB in the kernel option line (/boot/grub/menu.lst)  solved the problem !
The SLI is enabled now.

More info here : [http://www.nvnews.net/vbulletin/showthread.php?t=93128](http://www.nvnews.net/vbulletin/showthread.php?t=93128)

---

### Post by tseliot on 2007-08-10
Thanks for posting the solution.

---

