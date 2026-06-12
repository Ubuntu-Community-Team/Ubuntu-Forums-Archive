---
title: "X crashes on full screen TV"
date: 2011-05-30
forum: Multimedia Software
---

### Post by wtfai on 2011-05-30
I've just upgraded to Ubuntu 11.04. I have a Hauppauge TV receiver, reported as Bus 001 Device 003: ID 2040:7070 Hauppauge Nova-T Stick 3 which worked fine with 10.10 but which now crashes X every time I go to full screen (X log below).

I've tried Kaffeine and VLC, with Gnome and XFCE and it always behaves the same. It's fine in a window but when I go to full screen the screen shows some static and kicks me back to the login screen

Xorg.0.log.old
[   202.896] 
Backtrace:
[   202.896] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab2b]
[   202.896] 1: /usr/bin/X (0x8048000+0x5fad8) [0x80a7ad8]
[   202.896] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xe5740c]
[   202.896] 3: /usr/lib/xorg/modules/drivers/openchrome_drv.so (0x3c2000+0x26798) [0x3e8798]
[   202.896] 4: /usr/bin/X (0x8048000+0x140c26) [0x8188c26]
[   202.896] 5: /usr/bin/X (0x8048000+0x141682) [0x8189682]
[   202.896] 6: /usr/bin/X (miHandleValidateExposures+0x83) [0x81bc133]
[   202.896] 7: /usr/bin/X (miSlideAndSizeWindow+0x7e3) [0x81bcbf3]
[   202.896] 8: /usr/bin/X (0x8048000+0xa7e28) [0x80efe28]
[   202.896] 9: /usr/bin/X (ConfigureWindow+0xb20) [0x809aa60]
[   202.896] 10: /usr/bin/X (0x8048000+0x22239) [0x806a239]
[   202.897] 11: /usr/bin/X (0x8048000+0x28167) [0x8070167]
[   202.897] 12: /usr/bin/X (0x8048000+0x1a81c) [0x806281c]
[   202.897] 13: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0x14ce37]
[   202.897] 14: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
[   202.897] Segmentation fault at address (nil)
[   202.897] 
Caught signal 11 (Segmentation fault). Server aborting
[   202.897] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   202.897] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   202.897] 
[   202.897] (II) Power Button: Close
[   202.897] (II) UnloadModule: "evdev"
[   202.898] (II) Unloading evdev
[   202.898] (II) Power Button: Close
[   202.898] (II) UnloadModule: "evdev"
[   202.898] (II) Unloading evdev
[   202.898] (II) HOLTEK Wireless TackBall Keyboard: Close
[   202.898] (II) UnloadModule: "evdev"
[   202.898] (II) Unloading evdev
[   202.898] (II) HOLTEK Wireless TackBall Keyboard: Close
[   202.898] (II) UnloadModule: "evdev"
[   202.898] (II) Unloading evdev
[   202.899] Freed 12587008 (pool 1)
[   202.899] Freed 13840384 (pool 1)
[   202.899] (II) CHROME(0): VIALeaveVT
[   202.899] (II) CHROME(0): ViaCursorStore
[   202.899] (II) CHROME(0): VIARestore
[   202.917] (II) CHROME(0): ViaDisablePrimaryFIFO
[   202.918]  ddxSigGiveUp: Closing log

---

