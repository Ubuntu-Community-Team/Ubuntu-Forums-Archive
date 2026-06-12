---
title: "ATI Config tools error reporting xrandr 1.2 running"
date: 2009-05-19
forum: Multimedia Software
---

### Post by LinuxTAd on 2009-05-19
Hello,

 My current system is beyond the out of the box so to speak installation.  And I have been running into this error while working with the ATI Config tool fairly often. Of course you cannot delete the randr, as it would also remove several other things. But perhaps this is a bug in the ATI drivers themselves. To make sure I am posting to see if anyone elese is experiencing this as well.

Error example:  

> thomas@Ubuntu-6600:~$ sudo aticonfig --dtop=horizontal --overlay-on=1
Error: Options, e.g. --dtop and --desktop-setup, are not supported when RandR 1.2 is enabled!
Warning: Failed to set hardware overlay to head 1 immediately.
Using xorg.conf
Saved back-up to xorg.conf.fglrx-1> thomas@Ubuntu-6600:~$ aticonfig --swap-monitor --effective=now
Error: option --swap-monitor is not supported when RandR 1.2 is enabled!> thomas@Ubuntu-6600:~$ sudo aticonfig --swap-monitor --effective=now
Error: option --swap-monitor is not supported when RandR 1.2 is enabled!> thomas@Ubuntu-6600:~$  xrandr -v
Server reports RandR version 1.3I am assuming that xrandr and RandR 1.2 are one in the same...

To assure that some commands via ATI Configtool do work:  

> thomas@Ubuntu-6600:~$ aticonfig --list-powerstates
Error: POWERplay is not supported on your hardware.I am running dual ATI 3870's and just trying to iron out some things as I proceed with caution :) 

Attached are my xorg.conf and my last log got xorg.

I know it is alot to ask, but could I please get some help in locating the error and correcting it/working around it, or validating a bug for a report. 


My Current platform:

Abit AW9D-MAX
(qty.) ATI Visiontek HD3870's in crossfire mode (Crossfire mode and Xinerama are not enabled and the latter simply will not work currently)
4 Gigs ram
750 Watt PSU Logitech G% mouse and G15 keyboard
1-22" monitor as mainand a 20" monitor on the right. Big screen layout is not ebabled as the pop ups show up split in between the screens :-k
Intel Processor Core 2 Duo 2.4 Ghz. (E6600).
Ubuntu is installed on an ATA HDD by itself.


I would appreciate your hellp greatly on this one. Searches have not turned up much of anything usefull as of yet. Still searching tho!):P

Thank you,
TAd

---

### Post by LinuxTAd on 2009-05-20
I believe I located a fix:

[http://ubuntuforums.org/showthread.php?t=1137576](http://ubuntuforums.org/showthread.php?t=1137576)


From ToeBee

> 
Edit /etc/ati/amdpcsdb
In the section labeled [AMDPCSROOT/SYSTEM/DDX]
add this:
 	Code:
 	EnableRandR12=Sfalse 
Also, in /etc/X11/xorg.conf in the "Device" section add:
 	Code:
 	Option      "EnableRandR12" "false" 
Hope that helps.


And it does, thank you!!!!!!!!

---

### Post by LinuxTAd on 2009-05-20
```
thomas@Ubuntu-6600:~$ sudo aticonfig --query-monitor
Default Adapter - ATI Radeon HD 3870
  Connected monitors: tmds1, tmds2i
  Enabled monitors: tmds1, tmds2i

```


> thomas@Ubuntu-6600:~$ sudo aticonfig --swap-monitor --effective=now
thomas@Ubuntu-6600:~$ 

:popcorn:

---

