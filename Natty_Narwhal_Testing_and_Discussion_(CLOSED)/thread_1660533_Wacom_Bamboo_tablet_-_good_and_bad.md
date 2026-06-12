---
title: "Wacom Bamboo tablet - good and bad"
date: 2011-01-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by doctordruidphd on 2011-01-05
I have a Wacom Pen & Touch pad, CTH-460. Works great in Maverick.  The good news is that the new kernel for Natty comes with wacom.ko, so no need to go through rebuilding wacom.ko with each kernel update. In fact, no need to build it at all.

The bad news: It almost works. The stylus and eraser work fine, but the finger touch and pad apparently do not. 

```
greenman@Wolfenstein:~$ xinput --list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft SideWinder™ Mouse               id=10   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 2FG 4x5 Finger pad           id=11   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 2FG 4x5 Finger touch         id=12   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 2FG 4x5 Pen eraser           id=13   [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 2FG 4x5 Pen stylus           id=14   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; Chicony Saitek Cyborg Keyboard            id=8    [slave  keyboard (3)]
    &#8627; Chicony Saitek Cyborg Keyboard            id=9    [slave  keyboard (3)]

```

All I had to do was change "BambooFun" in the old xsetwacom.sh to "Bamboo", and the file works, without errors. But no touch or pad.

```
greenman@Wolfenstein:~$ xsetwacom --list
Wacom Bamboo 2FG 4x5 Finger pad PAD       
Wacom Bamboo 2FG 4x5 Finger touch TOUCH     
Wacom Bamboo 2FG 4x5 Pen eraser ERASER    
Wacom Bamboo 2FG 4x5 Pen stylus STYLUS
```

Seems like everything is there.

---

### Post by Favux on 2011-01-05
Hi doctordruidphd,

Do you know what version of the wacom.ko is being used?  Do you know what version of xf86-input-wacom is used?

We could look at your Xorg.0.log in /var/log to answer that and also make sure touch and pad are being placed on the Wacom drivers.  The xsetwacom list sure seems to indicate that they are.

---

### Post by doctordruidphd on 2011-01-05
Here is what I get for Xorg.0.log after plugging the bamboo in. Strange, it seems to be recognizing the touch and pad. They just don't work.

```

[   233.658] (II) config/udev: Adding input device Wacom Bamboo 2FG 4x5 Finger (/dev/input/mouse2)
[   233.658] (II) No input driver/identifier specified (ignoring)
[   233.661] (II) config/udev: Adding input device Wacom Bamboo 2FG 4x5 Finger (/dev/input/event7)
[   233.661] (**) Wacom Bamboo 2FG 4x5 Finger: Applying InputClass "evdev touchpad catchall"
[   233.661] (**) Wacom Bamboo 2FG 4x5 Finger: Applying InputClass "touchpad catchall"
[   233.661] (**) Wacom Bamboo 2FG 4x5 Finger: Applying InputClass "Wacom class"
[   233.661] (II) LoadModule: "wacom"
[   233.661] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[   233.686] (II) Module wacom: vendor="X.Org Foundation"
[   233.686]    compiled for 1.8.99.905, module version = 0.10.8
[   233.686]    Module class: X.Org XInput Driver
[   233.686]    ABI class: X.Org XInput driver, version 11.0
[   233.686] (**) Option "Device" "/dev/input/event7"
[   233.750] (II) Wacom Bamboo 2FG 4x5 Finger: type not specified, assuming 'touch'.
[   233.750] (II) Wacom Bamboo 2FG 4x5 Finger: other types will be automatically added.
[   233.750] (**) Wacom Bamboo 2FG 4x5 Finger touch: always reports core events
[   233.750] (--) Wacom Bamboo 2FG 4x5 Finger touch: using pressure threshold of 27 for button 1
[   233.750] (--) Wacom Bamboo 2FG 4x5 Finger touch: Wacom USB Bamboo tablet maxX=0 maxY=0 maxZ=256 resX=2540 resY=2540  tilt=disabled
[   233.750] (II) Wacom Bamboo 2FG 4x5 Finger touch: hotplugging dependent devices.
[   233.750] (**) Wacom Bamboo 2FG 4x5 Finger pad: Applying InputClass "evdev touchpad catchall"
[   233.750] (**) Wacom Bamboo 2FG 4x5 Finger pad: Applying InputClass "touchpad catchall"
[   233.750] (**) Wacom Bamboo 2FG 4x5 Finger pad: Applying InputClass "Wacom class"
[   233.750] (**) Option "Device" "/dev/input/event7"
[   233.810] (**) Wacom Bamboo 2FG 4x5 Finger pad: always reports core events
[   233.810] (--) Wacom Bamboo 2FG 4x5 Finger pad: Wacom USB Bamboo tablet maxX=0 maxY=0 maxZ=256 resX=2540 resY=2540  tilt=disabled
[   233.850] (II) XINPUT: Adding extended input device "Wacom Bamboo 2FG 4x5 Finger pad" (type: PAD)
[   233.850] (--) Wacom Bamboo 2FG 4x5 Finger pad: top X=0 top Y=0 bottom X=0 bottom Y=0 resol X=2540 resol Y=2540
[   234.020] (II) Wacom Bamboo 2FG 4x5 Finger touch: hotplugging completed.
[   234.110] (II) XINPUT: Adding extended input device "Wacom Bamboo 2FG 4x5 Finger touch" (type: TOUCH)
[   234.110] (--) Wacom Bamboo 2FG 4x5 Finger touch: top X=0 top Y=0 bottom X=15360 bottom Y=10240 resol X=2540 resol Y=2540
[   234.112] (II) config/udev: Adding input device Wacom Bamboo 2FG 4x5 Pen (/dev/input/mouse1)
[   234.112] (II) No input driver/identifier specified (ignoring)
[   234.112] (II) config/udev: Adding input device Wacom Bamboo 2FG 4x5 Pen (/dev/input/event6)
[   234.112] (**) Wacom Bamboo 2FG 4x5 Pen: Applying InputClass "evdev tablet catchall"
[   234.112] (**) Wacom Bamboo 2FG 4x5 Pen: Applying InputClass "Wacom class"
[   234.112] (**) Option "Device" "/dev/input/event6"
[   234.200] (II) Wacom Bamboo 2FG 4x5 Pen: type not specified, assuming 'stylus'.
[   234.200] (II) Wacom Bamboo 2FG 4x5 Pen: other types will be automatically added.
[   234.200] (**) Wacom Bamboo 2FG 4x5 Pen stylus: always reports core events
[   234.200] (--) Wacom Bamboo 2FG 4x5 Pen stylus: using pressure threshold of 27 for button 1
[   234.200] (--) Wacom Bamboo 2FG 4x5 Pen stylus: Wacom USB Bamboo tablet maxX=14720 maxY=9200 maxZ=1023 resX=2540 resY=2540  tilt=disabled
[   234.200] (II) Wacom Bamboo 2FG 4x5 Pen stylus: hotplugging dependent devices.
[   234.200] (**) Wacom Bamboo 2FG 4x5 Pen eraser: Applying InputClass "evdev tablet catchall"
[   234.200] (**) Wacom Bamboo 2FG 4x5 Pen eraser: Applying InputClass "Wacom class"
[   234.200] (**) Option "Device" "/dev/input/event6"
[   234.280] (**) Wacom Bamboo 2FG 4x5 Pen eraser: always reports core events
[   234.280] (--) Wacom Bamboo 2FG 4x5 Pen eraser: Wacom USB Bamboo tablet maxX=14720 maxY=9200 maxZ=1023 resX=2540 resY=2540  tilt=disabled
[   234.370] (II) XINPUT: Adding extended input device "Wacom Bamboo 2FG 4x5 Pen eraser" (type: ERASER)
[   234.370] (--) Wacom Bamboo 2FG 4x5 Pen eraser: top X=0 top Y=0 bottom X=14720 bottom Y=9200 resol X=2540 resol Y=2540
[   234.600] (II) Wacom Bamboo 2FG 4x5 Pen stylus: hotplugging completed.
[   234.720] (II) XINPUT: Adding extended input device "Wacom Bamboo 2FG 4x5 Pen stylus" (type: STYLUS)
[   234.720] (--) Wacom Bamboo 2FG 4x5 Pen stylus: top X=0 top Y=0 bottom X=14720 bottom Y=9200 resol X=2540 resol Y=2540
[   234.724] (II) XKB: reuse xkmfile /var/lib/xkb/server-94E894B26EE80D81A9ABC53B73E4442332F0B778.xkm
[   234.744] (II) XKB: reuse xkmfile /var/lib/xkb/server-73AC8D4822B76BE375830D90D9DD145B2CBC4E27.xkm
[   234.758] (II) XKB: reuse xkmfile /var/lib/xkb/server-94E894B26EE80D81A9ABC53B73E4442332F0B778.xkm
[   234.771] (II) XKB: reuse xkmfile /var/lib/xkb/server-73AC8D4822B76BE375830D90D9DD145B2CBC4E27.xkm
[   234.780] (II) XKB: reuse xkmfile /var/lib/xkb/server-94E894B26EE80D81A9ABC53B73E4442332F0B778.xkm
[   234.795] (II) XKB: reuse xkmfile /var/lib/xkb/server-73AC8D4822B76BE375830D90D9DD145B2CBC4E27.xkm
[   234.807] (II) XKB: reuse xkmfile /var/lib/xkb/server-94E894B26EE80D81A9ABC53B73E4442332F0B778.xkm
[   234.815] (II) XKB: reuse xkmfile /var/lib/xkb/server-73AC8D4822B76BE375830D90D9DD145B2CBC4E27.xkm


```

---

### Post by doctordruidphd on 2011-01-05
Additional info:  

```
greenman@Wolfenstein:/var/log$ modinfo wacom
filename:       /lib/modules/2.6.37-11-generic/kernel/drivers/input/tablet/wacom.ko
license:        GPL
description:    USB Wacom tablet driver
author:         Vojtech Pavlik <vojtech@ucw.cz>
license:        GPL
description:    USB Wacom tablet driver
author:         Vojtech Pavlik <vojtech@ucw.cz>
srcversion:     404C1FA94C2D4F3BB6E8D80
alias:          usb:v056Ap0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00E3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00E2d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap009Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap009Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0093d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0090d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00CCd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00F0d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00DBd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00DAd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00D8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00D4d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00D3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00D2d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00D1d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00D0d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00CEd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00C7d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00C6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00C5d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00BCd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00BBd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00BAd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00B9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00B8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00B7d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00B5d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00B4d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00B3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00B2d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00B1d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00B0d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0045d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0044d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0043d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00C2d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00C0d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap00C4d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0038d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0037d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0035d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0034d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0033d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0030d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0024d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0023d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0069d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0065d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0064d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0063d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0062d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0061d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0060d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0016d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0015d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0014d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0013d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v056Ap0000d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.37-11-generic SMP mod_unload modversions
```

---

### Post by Favux on 2011-01-05
Sure looks right.  Does Synaptic Package Manager give you anything about the wacom.ko's version?

It seems to be using xf86-input-wacom 0.10.8, or that series before the 0.10.9 point release so that should be OK.  It's usually good to post the whole Xorg.0.log (you can compress it and attach it).  But it doesn't seem likely that another driver is then taking back the pad and touch from wacom, especially since you're seeing it in xsetwacom list.

The usb signal comes in on another channel for pad/touch than the one stylus/eraser is on.  With HAL it was if0 for the stylus and if1 for touch.  But the signal is there because you're seeing it in xinput and xsetwacom.

That seems to leave some bug in the xf86-input-wacom 0.10.8 version Ubuntu is using.  Which must be different somehow from the LWP's version.  You don't have touch turned off do you?

You could try cloning the git repository and putting xf86-input-wacom 0.10.10+ in instead and see if that fixes it.

---

### Post by doctordruidphd on 2011-01-05
The only thing synaptic is telling me is that xserver-xrog-input-wacom is 1.0.10.8-0ubuntu1.

I just enables the xorg-edgers reporitory, and I notice there are a bunch of xserver updates available, however, --input-wacom is not one of them.

I believe wacom.ko is now part of the kernel package, which is:

2.6.37-11-generic #25-Ubuntu SMP Tue Dec 21 23:42:56 UTC 2010 x86_64 GNU/Linux
Not sure how to get info on it beyond modinfo.

I removed and reinserted the wacom usb plug a couple of times, still no touch. Tried toggle-touch.sh, which says it is turning off and on, but the touch and pad don't work, either way.

Xorg.0.log.bz2 attached.

---

### Post by Favux on 2011-01-05
Sure enough:
```
[  1669.460] (EE) Wacom Bamboo 2FG 4x5 Pen stylus: Error reading wacom device : No such device
[  1669.460] (II) config/udev: removing device Wacom Bamboo 2FG 4x5 Pen stylus
[  1669.461] (II) Wacom Bamboo 2FG 4x5 Pen stylus: removing automatically added devices.
[  1669.461] (II) Wacom Bamboo 2FG 4x5 Pen stylus: removing dependent device 'Wacom Bamboo 2FG 4x5 Pen eraser'
[  1669.461] (II) UnloadModule: "wacom"
[  1669.461] (II) UnloadModule: "wacom"
[  1669.650] (EE) Wacom Bamboo 2FG 4x5 Finger touch: Error reading wacom device : No such device
[  1669.650] (II) config/udev: removing device Wacom Bamboo 2FG 4x5 Finger touch
[  1669.651] (II) Wacom Bamboo 2FG 4x5 Finger touch: removing automatically added devices.
[  1669.651] (II) Wacom Bamboo 2FG 4x5 Finger touch: removing dependent device 'Wacom Bamboo 2FG 4x5 Finger pad'
[  1669.651] (II) UnloadModule: "wacom"
[  1669.651] (II) UnloadModule: "wacom"
[  2301.544] (II) config/udev: Adding input device Wacom Bamboo 2FG 4x5 Pen (/dev/input/event6)
[  2301.544] (**) Wacom Bamboo 2FG 4x5 Pen: Applying InputClass "evdev tablet catchall"
[  2301.544] (**) Wacom Bamboo 2FG 4x5 Pen: Applying InputClass "Wacom class"
[  2301.544] (**) Option "Device" "/dev/input/event6"
[  2301.590] (II) Wacom Bamboo 2FG 4x5 Pen: type not specified, assuming 'stylus'.
[  2301.590] (II) Wacom Bamboo 2FG 4x5 Pen: other types will be automatically added.
[  2301.590] (**) Wacom Bamboo 2FG 4x5 Pen stylus: always reports core events
[  2301.590] (--) Wacom Bamboo 2FG 4x5 Pen stylus: using pressure threshold of 27 for button 1
[  2301.590] (--) Wacom Bamboo 2FG 4x5 Pen stylus: Wacom USB Bamboo tablet maxX=14720 maxY=9200 maxZ=1023 resX=2540 resY=2540  tilt=disabled
[  2301.590] (II) Wacom Bamboo 2FG 4x5 Pen stylus: hotplugging dependent devices.
[  2301.590] (**) Wacom Bamboo 2FG 4x5 Pen eraser: Applying InputClass "evdev tablet catchall"
[  2301.590] (**) Wacom Bamboo 2FG 4x5 Pen eraser: Applying InputClass "Wacom class"
[  2301.590] (**) Option "Device" "/dev/input/event6"
[  2301.650] (**) Wacom Bamboo 2FG 4x5 Pen eraser: always reports core events
[  2301.650] (--) Wacom Bamboo 2FG 4x5 Pen eraser: Wacom USB Bamboo tablet maxX=14720 maxY=9200 maxZ=1023 resX=2540 resY=2540  tilt=disabled
[  2301.710] (II) XINPUT: Adding extended input device "Wacom Bamboo 2FG 4x5 Pen eraser" (type: ERASER)
[  2301.710] (--) Wacom Bamboo 2FG 4x5 Pen eraser: top X=0 top Y=0 bottom X=14720 bottom Y=9200 resol X=2540 resol Y=2540
[  2301.840] (II) Wacom Bamboo 2FG 4x5 Pen stylus: hotplugging completed.
[  2301.890] (II) XINPUT: Adding extended input device "Wacom Bamboo 2FG 4x5 Pen stylus" (type: STYLUS)
[  2301.890] (--) Wacom Bamboo 2FG 4x5 Pen stylus: top X=0 top Y=0 bottom X=14720 bottom Y=9200 resol X=2540 resol Y=2540
[  2301.891] (II) config/udev: Adding input device Wacom Bamboo 2FG 4x5 Pen (/dev/input/mouse1)
[  2301.891] (II) No input driver/identifier specified (ignoring)
[  2301.891] (II) config/udev: Adding input device Wacom Bamboo 2FG 4x5 Finger (/dev/input/mouse2)
[  2301.891] (II) No input driver/identifier specified (ignoring)
[  2301.891] (II) config/udev: Adding input device Wacom Bamboo 2FG 4x5 Finger (/dev/input/event7)
[  2301.891] (**) Wacom Bamboo 2FG 4x5 Finger: Applying InputClass "evdev touchpad catchall"
[  2301.891] (**) Wacom Bamboo 2FG 4x5 Finger: Applying InputClass "touchpad catchall"
[  2301.891] (**) Wacom Bamboo 2FG 4x5 Finger: Applying InputClass "Wacom class"
[  2301.892] (**) Option "Device" "/dev/input/event7"
[  2301.940] (II) Wacom Bamboo 2FG 4x5 Finger: type not specified, assuming 'touch'.
[  2301.940] (II) Wacom Bamboo 2FG 4x5 Finger: other types will be automatically added.
[  2301.940] (**) Wacom Bamboo 2FG 4x5 Finger touch: always reports core events
[  2301.940] (--) Wacom Bamboo 2FG 4x5 Finger touch: using pressure threshold of 27 for button 1
[  2301.940] (--) Wacom Bamboo 2FG 4x5 Finger touch: Wacom USB Bamboo tablet maxX=0 maxY=0 maxZ=256 resX=2540 resY=2540  tilt=disabled
[  2301.940] (II) Wacom Bamboo 2FG 4x5 Finger touch: hotplugging dependent devices.
[  2301.940] (**) Wacom Bamboo 2FG 4x5 Finger pad: Applying InputClass "evdev touchpad catchall"
[  2301.940] (**) Wacom Bamboo 2FG 4x5 Finger pad: Applying InputClass "touchpad catchall"
[  2301.940] (**) Wacom Bamboo 2FG 4x5 Finger pad: Applying InputClass "Wacom class"
[  2301.940] (**) Option "Device" "/dev/input/event7"
[  2302.020] (**) Wacom Bamboo 2FG 4x5 Finger pad: always reports core events
[  2302.020] (--) Wacom Bamboo 2FG 4x5 Finger pad: Wacom USB Bamboo tablet maxX=0 maxY=0 maxZ=256 resX=2540 resY=2540  tilt=disabled
[  2302.060] (II) XINPUT: Adding extended input device "Wacom Bamboo 2FG 4x5 Finger pad" (type: PAD)
[  2302.060] (--) Wacom Bamboo 2FG 4x5 Finger pad: top X=0 top Y=0 bottom X=0 bottom Y=0 resol X=2540 resol Y=2540
[  2302.250] (II) Wacom Bamboo 2FG 4x5 Finger touch: hotplugging completed.
[  2302.330] (II) XINPUT: Adding extended input device "Wacom Bamboo 2FG 4x5 Finger touch" (type: TOUCH)
[  2302.330] (--) Wacom Bamboo 2FG 4x5 Finger touch: top X=0 top Y=0 bottom X=15360 bottom Y=10240 resol X=2540 resol Y=2540
```
So for whatever reason the wacom driver isn't working and the "evdev tablet catchall" snippet in 10-evdev.conf is picking up the stylus/eraser.  You probably don't have pressure and can't configure through xsetwacom if the stylus is on the evdev driver.  It looks like the wacom driver then picks touch back up, but since you don't have any touch something must be going wrong there.

---

### Post by doctordruidphd on 2011-01-05
That may have been due to me unplugging and replugging the device.

I did a reboot, and plugged the device in. Here is Xorg.0.log; I don't offhand see a problem with the wacom module loading here.

Funny thing I just noticed -- I do have some touch functionality. Apparently, a gesture or multiple tapping is working, as when I move my fingers around on the pad, I can get firefox to follow links.  But I cannot get any cursor movement, nor response from the buttons.

---

### Post by Favux on 2011-01-05
That Xorg.0.log looks right.  Of course that begs the question as to why hot plugging fails which is probably another clue.

The wacom.ko with the 2.6.37 kernel should be good.  The xf86-input-wacom 0.10.8 should work Natty's Xserver 1.9.  Did you try a xsetwacom script?

I guess I don't feel it's worth investigating further because Natty is still alpha 1.  Maybe with the alpha 2 or better the alpha 3 it would be worth looking into.  I'm assuming a library is missing or an updated library has broken something.  You have to wonder if they're doing something with the utouch stack.

---

### Post by cariboo on 2011-01-05
I may be well worth your while to create a bug report against the kernel, as the driver is part of the kernel.

---

### Post by doctordruidphd on 2011-01-05
Right, I don't know if it's worth posting a bug report at this point.

I tried commenting out the relevant parts of 10-evdev.conf just to see what would happen.  No change.  The fact that tapping works at all, albeit unreliably, while the cursor does not, suggests to me it is a genuine bug. 

Thanks for looking into it.

---

### Post by doctordruidphd on 2011-01-05
> I may be well worth your while to create a bug report against the kernel, as the driver is part of the kernel.

OK then, I will.

---

### Post by doctordruidphd on 2011-01-05
Bug reported, # 697949

---

### Post by cariboo on 2011-01-05
Thank you

---

### Post by Sashin on 2011-01-06
I have this exact same problem, 'cept I'm using Maverick with the new kernel.

---

