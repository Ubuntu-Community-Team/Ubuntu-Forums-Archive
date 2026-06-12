---
title: "Xorg restarts infinitely on login"
date: 2011-03-21
forum: Multimedia Software
---

### Post by adrine.correya on 2011-03-21
Helo!

I just came back to Ubuntu 10.04 after a few skips over 10.10 and 11.04.  After a recent update, Xorg keeps restarting just after login into normal graphics mode with the following error in /var/log/Xorg.1.log (Xorg.0.log gets no error when logging in with safe gnome).

> ...

(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(WW) intel(0): i830_uxa_prepare_access: bo map failed

Fatal server error:
Failed to submit batchbuffer: Input/output error


Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) USB Optical Mouse: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) AIGLX: Suspending AIGLX clients for VT switch
 ddxSigGiveUp: Closing log

The Xorg.log and xsessions.error files are attached in zip...

Thanks in advance for the help!

---

### Post by adrine.correya on 2011-03-28
bumped!

---

### Post by adrine.correya on 2011-04-12
Ok! now i fresh installed 10.04.. But still Xorg crashes sometime during the screensaver or so after login, for apparently no reason.. please help!

---

