---
title: "Nvidia TwinView External monitor refresh rate locked"
date: 2011-03-26
forum: Multimedia Software
---

### Post by motopico on 2011-03-26
Hi everyone!
I'm trying to use an external monitor to watch movies on my linux box (kubuntu maverick) but it results always out of sync. TV-out refresh rate is locked as you can see on the image i've attached right here.

[IMG]http://www.dropmocks.com/iSyzZ[/IMG]

This is the output of the nvidia-settings query about the variable RefreshRate:

```
  Attribute 'RefreshRate' (DeepBlue:0.0; display device: CRT-0): 60.02 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.
  Attribute 'RefreshRate' (DeepBlue:0.0; display device: TV-0): 60.00 Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display device specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

```

as you can see the TV-0 is forced @60 Hz, but the device doesn't support this rate (it's an Olympus eye-trek fmd-200)

I've tried to disable the Gpu scaling but no luck. Whatelse should i do?

Thanks a lot and regards!

P.s.
Nvidia drivers are: 260.19.44
Kernel: 2.6.35-28-generic
Graphic processor: GeForce 6200 w Vbios 05.44.a2.10.81

---

### Post by realzippy on 2011-03-26
Can you click on "1024x768" ?
The refresh rate "auto" should get unlocked then..

---

### Post by motopico on 2011-03-26
Yes i can... but it doesn't unlock

---

### Post by motopico on 2011-03-26
Nevermind i solved editing my xorg.conf like this:

```
        Option "TwinView" "True"
        Option "TwinViewOrientation" "RightOf"
        Option  "TVStandard" "PAL-B"
        Option  "TVOutFormat" "SVIDEO"
        Option  "ConnectedMonitor" "CRT,TV"
        Option "MetaModes" "1280x1024,1024x768"
        Option      "SecondMonitorHorizSync"   "30-50"
        Option      "SecondMonitorVertRefresh" "50"

```

under the device section.

I hope this could help somebody else.

---

