---
title: "Random logoffs"
date: 2010-10-28
forum: Mythbuntu
---

### Post by griffinuum on 2010-10-28
I recently upgraded to 10.10 and ever since I have had random events that throw me back to a logon screen, closing my active programs. It happens with or without mythfrontend running, with or without typing, sometimes after a few minutes, or sometimes after a couple hours. I've checked syslog and can't nail it down to anything specific. Anyone else have this issue? Everything was stable under 10.04 and older. The only other change I made was to change to auto builds (0.23.1). Any suggestions on where to look?
Thanks.

---

### Post by wangsuda on 2010-10-29
I, too, have the same problem. I notice it more frequently when trying to print from Adobe Reader 9 and loading Firefox. However, sometimes it never happens and sometimes it can happen 2-3 times when the computer is idle.

---

### Post by NightStorm on 2010-10-29
Same here.  Originally I did took the dist-upgrade path from 32 bit 10.04 to 10.10 and as soon as I tried to play either live TV or a recording I'd abort out to the login prompt.  So then I downloaded / burned a CD and did a new install (twice)  Same thing.  Next I tried installing Ubuntu 10.10 then installed the whole MythTV system.  Same thing.

While I was trying the second install of Mythbuntu I discovered that I could play live TV with the default, non-proprietary drivers.  However since the driver would not support my 1080p TV (would max out at 1024x720) this did not look good.  The NVidia drivers look great, but once installed I get the logouts.

I tried uninstalling the NVidia drivers and then installing them direct from the nvidia site but then the system would hang during boot.

    - Bruce

---

### Post by NightStorm on 2010-10-29
Just tried 64 bit version of Mythbuntu.  Same failure

---

### Post by ian dobson on 2010-10-29
Hi,

After it happens, login,go to the terminal prompt and type dmesg and have a look if any process has segfaulted.

I had a box that showed very similar problems and it turned out to be a screwed up BIOS (a BIOS update fixed it) causing X to crash/segfault and restart.

Regards
Ian Dobson

---

### Post by NightStorm on 2010-10-29
After the unexpected logout the last few lines of dmesg show:

[   11.387981] nvidia 0000:02:00.0: PCI INT A -> Link[SGRU] -> GSI 20 (level, low) -> IRQ 20
[   11.387988] nvidia 0000:02:00.0: setting latency timer to 64
[   11.387993] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   11.388241] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.06  Mon Sep 13 04:29:19 PDT 2010
[   11.976280] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0
[   15.014560] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.6.114.fw)...
[   15.016508] xc5000: firmware read 12401 bytes.
[   15.016511] xc5000: firmware uploading...
[   21.491265] eth0: no IPv6 routers present
[   22.830020] xc5000: firmware upload complete...
[   23.303872] ftdi_sio ttyUSB0: Unable to write latency timer: -32
[   72.510022] Clocksource tsc unstable (delta = -153682772 ns)
[  100.042813] show_signal_msg: 3 callbacks suppressed
[  100.042824] mythfrontend.re[2141]: segfault at 40f12320 ip 00007f4688437445 sp 00007f4668980850 error 4 in libc-2.12.1.so[7f46883fe000+17a000]
[  102.481994] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro,commit=0

---

### Post by NightStorm on 2010-10-29
Oops .. looks like it is already being discussed here: [http://ubuntuforums.org/showthread.php?t=1592588](http://ubuntuforums.org/showthread.php?t=1592588)

---

