---
title: "X crashing due to input Device"
date: 2011-02-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Therion2011 on 2011-02-15
Hi guys,
it's a bit sad to have my first post be one asking for help, but I hope you bear with me.

I've almost always been using the developer-version and hardly never had any issues I wasn't able to solve myself but now I do have one...

X is crashing due to an input device. That is at least what it seems like judging from the xorg.conf - at the end of the post the (probably) most relevant part of the log.

Now how can I prevent x from trying to use this device?
xsetwacom and xinput was all I could think of for this task - but they of course don't work.
I cannot unplug this device because it's the build in touchscreen ;)

Thank you very much for any help :D

[COLOR=Red][I][B]Edit: Found a way: Just rmmod hd_ntrig. Sorry for the unnecessary post! [Thread can be deleted or whatever]
[/B][/I][/COLOR] 
[  2451.567] (II) config/udev: Adding input device HDA ATI SB Mic (/dev/input/event22)
[  2451.567] (II) No input driver/identifier specified (ignoring)
[  2451.568] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event23)
[  2451.568] (II) No input driver/identifier specified (ignoring)
[  2451.571] (II) config/udev: Adding input device N-Trig Pen (/dev/input/event11)
[  2451.571] (**) N-Trig Pen: Applying InputClass "Wacom N-Trig class"
[  2451.571] (II) LoadModule: "wacom"
[  2451.571] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[  2451.572] (II) Module wacom: vendor="X.Org Foundation"
[  2451.572]     compiled for 1.9.99.901, module version = 0.10.10
[  2451.572]     Module class: X.Org XInput Driver
[  2451.572]     ABI class: X.Org XInput driver, version 12.1
[  2451.572] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[  2451.572] (**) N-Trig Pen: always reports core events
[  2451.572] (**) Option "Device" "/dev/input/event11"
[  2451.580] (EE) PreInit returned 8 for "N-Trig Pen"
[  2451.580] 
Backtrace:
[  2451.581] 0: /usr/bin/X (xorg_backtrace+0x26) [0x4a1586]
[  2451.581] 1: /usr/bin/X (0x400000+0x6078a) [0x46078a]
[  2451.581] 2: /lib/libpthread.so.0 (0x7f8f12b80000+0xfc80) [0x7f8f12b8fc80]
[  2451.581] 3: /usr/lib/xorg/modules/input/wacom_drv.so (0x7f8f0d8d6000+0x8ddf) [0x7f8f0d8deddf]
[  2451.581] 4: /usr/bin/X (0x400000+0x7ace8) [0x47ace8]
[  2451.582] 5: /usr/bin/X (0x400000+0x83679) [0x483679]
[  2451.582] 6: /usr/bin/X (0x400000+0x83d4e) [0x483d4e]
[  2451.582] 7: /usr/bin/X (config_init+0x9) [0x483079]
[  2451.582] 8: /usr/bin/X (InitInput+0x95) [0x46d035]
[  2451.582] 9: /usr/bin/X (0x400000+0x21a86) [0x421a86]
[  2451.583] 10: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7f8f11ae9d1e]
[  2451.583] 11: /usr/bin/X (0x400000+0x21669) [0x421669]
[  2451.583] Segmentation fault at address 0x18
[  2451.583] 
Caught signal 11 (Segmentation fault). Server aborting
[  2451.583] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[  2451.583] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  2451.583] 
[  2451.584] (II) Power Button: Close
[  2451.584] (II) UnloadModule: "evdev"
[  2451.584] (II) Unloading evdev
[  2451.585] (II) Power Button: Close
[  2451.585] (II) UnloadModule: "evdev"
[  2451.585] (II) Unloading evdev
[  2451.585] (II) Sleep Button: Close
[  2451.585] (II) UnloadModule: "evdev"
[  2451.585] (II) Unloading evdev
[  2451.586] (II) CNF8038: Close
[  2451.586] (II) UnloadModule: "evdev"
[  2451.586] (II) Unloading evdev
[  2451.586] (II) AIGLX: Suspending AIGLX clients for VT switch
[  2451.629]  ddxSigGiveUp: Closing log

---

### Post by Harry33 on 2011-02-15
> **Therion2011 said:**
> Hi guys,
it's a bit sad to have my first post be one asking for help, but I hope you bear with me.

I've almost always been using the developer-version and hardly never had any issues I wasn't able to solve myself but now I do have one...

X is crashing due to an input device. That is at least what it seems like judging from the xorg.conf - at the end of the post the (probably) most relevant part of the log.

Now how can I prevent x from trying to use this device?
xsetwacom and xinput was all I could think of for this task - but they of course don't work.
I cannot unplug this device because it's the build in touchscreen ;)

Thank you very much for any help :D

[COLOR=Red][I][B]Edit: Found a way: Just rmmod hd_ntrig. Sorry for the unnecessary post! [Thread can be deleted or whatever]
[/B][/I][/COLOR] 
[  2451.567] (II) config/udev: Adding input device HDA ATI SB Mic (/dev/input/event22)
[  2451.567] (II) No input driver/identifier specified (ignoring)
[  2451.568] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event23)
[  2451.568] (II) No input driver/identifier specified (ignoring)
[  2451.571] (II) config/udev: Adding input device N-Trig Pen (/dev/input/event11)
[  2451.571] (**) N-Trig Pen: Applying InputClass "Wacom N-Trig class"
[  2451.571] (II) LoadModule: "wacom"
[  2451.571] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[  2451.572] (II) Module wacom: vendor="X.Org Foundation"
[  2451.572]     compiled for 1.9.99.901, module version = 0.10.10
[  2451.572]     Module class: X.Org XInput Driver
[  2451.572]     ABI class: X.Org XInput driver, version 12.1
[  2451.572] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[  2451.572] (**) N-Trig Pen: always reports core events
[  2451.572] (**) Option "Device" "/dev/input/event11"
[  2451.580] (EE) PreInit returned 8 for "N-Trig Pen"
[  2451.580] 
Backtrace:
[  2451.581] 0: /usr/bin/X (xorg_backtrace+0x26) [0x4a1586]
[  2451.581] 1: /usr/bin/X (0x400000+0x6078a) [0x46078a]
[  2451.581] 2: /lib/libpthread.so.0 (0x7f8f12b80000+0xfc80) [0x7f8f12b8fc80]
[  2451.581] 3: /usr/lib/xorg/modules/input/wacom_drv.so (0x7f8f0d8d6000+0x8ddf) [0x7f8f0d8deddf]
[  2451.581] 4: /usr/bin/X (0x400000+0x7ace8) [0x47ace8]
[  2451.582] 5: /usr/bin/X (0x400000+0x83679) [0x483679]
[  2451.582] 6: /usr/bin/X (0x400000+0x83d4e) [0x483d4e]
[  2451.582] 7: /usr/bin/X (config_init+0x9) [0x483079]
[  2451.582] 8: /usr/bin/X (InitInput+0x95) [0x46d035]
[  2451.582] 9: /usr/bin/X (0x400000+0x21a86) [0x421a86]
[  2451.583] 10: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7f8f11ae9d1e]
[  2451.583] 11: /usr/bin/X (0x400000+0x21669) [0x421669]
[  2451.583] Segmentation fault at address 0x18
[  2451.583] 
Caught signal 11 (Segmentation fault). Server aborting
[  2451.583] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[  2451.583] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  2451.583] 
[  2451.584] (II) Power Button: Close
[  2451.584] (II) UnloadModule: "evdev"
[  2451.584] (II) Unloading evdev
[  2451.585] (II) Power Button: Close
[  2451.585] (II) UnloadModule: "evdev"
[  2451.585] (II) Unloading evdev
[  2451.585] (II) Sleep Button: Close
[  2451.585] (II) UnloadModule: "evdev"
[  2451.585] (II) Unloading evdev
[  2451.586] (II) CNF8038: Close
[  2451.586] (II) UnloadModule: "evdev"
[  2451.586] (II) Unloading evdev
[  2451.586] (II) AIGLX: Suspending AIGLX clients for VT switch
[  2451.629]  ddxSigGiveUp: Closing log

Right it is these lines:
```
[  2451.572] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[  2451.572] (**) N-Trig Pen: always reports core events
[  2451.572] (**) Option "Device" "/dev/input/event11"
[  2451.580] (EE) PreInit returned 8 for "N-Trig Pen"

  2451.583] Segmentation fault at address 0x18
[  2451.583] 
Caught signal 11 (Segmentation fault). Server aborting
[  2451.583] 
```

What happens if you uninstall wacom driver (xserver-xorg-input-wacom)?

---

### Post by Favux on 2011-02-16
Hi Therion2011,

That looks like it may be the same single finger touch bug in the Maverick hid-ntrig.ko, not enough information to tell.  What firmware are you using?  Do you just have single finger touch on evdev or multitouch?

The bug was addressed by jayhawk and pushed to the Utouch ppa stack by Henrik Ryberg:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/643212](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/643212)

So I'm concerned if it is still showing up in the Natty hid-ntrig.ko.  If so you should file a bug report.

---

