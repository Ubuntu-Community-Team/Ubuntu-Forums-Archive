---
title: "Webcam Creative Notebook PD1170 ID 0572:0041 Conexant  does not work on Hardy Heron"
date: 2008-05-26
forum: Multimedia Software
---

### Post by lamiturri on 2008-05-26
Hello, 

I'm new with Linux and I started with Hardy Heron. I have 2 webcams:

Creative Notebook Pro, model VF0250 -- ID 041e:4051 that works ok
Creative Notebook, model PD1170 -- ID ID 0572:0041 that does not work at all.

I tried with Xawtv, Cheese and Camorama, Ekiga and Mplayer. Webcam light turns on, all these programs DO connect to video device /dev/video0 and the trace is the same with both cameras. It looks like all of them hang with Creative Notebook PD1170.
 
I tried (among other thousand things) installing the latest version of the gspca driver from [http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html) but it did not work.

Finally I tried with a GUTSY GIBBON LiveCD and BOTH cameras worked perfectly :)

I don't if this bug? has to do with Hardy Heron or with gspca driver ... and where should I report this bug? ...

Thanks

---

### Post by lamiturri on 2008-05-28
Hello,

Sorry, I was wrong: PD1170 does work with Hardy ... but ...

I tried Hardy liveCD and Gutsy liveCD wih my laptop HP Compaq nx6125 and boh cameras worked with Ekiga.

I installed Gutsy in my Fujitsu-Siemens PC Esprimo P2411 sempron and PD1170 webcam doesn't work. All programs (Ekiga, camorama ...) hang :( The other webcam (Notebook Pro) works perfectly ... I need both running because I would like to install a video surveillance system at home using Zoneminder ... 

Any ideas? Something to do with my PC's USB or graphic card? I'm lost ...

---

### Post by lamiturri on 2008-06-03
Hello,

I'm trying PD1170 webcam with Hardy LiveCD and it works in some PCs, but it freezes all programs (camorama, ekiga) in others ... I don't know what is going on ... any ideas?

---

### Post by lamiturri on 2008-06-06
Here is syslog output when PD1170 is connected to my PC. There are 2 lines, different from the syslog output in my laptop ... I suppose that the error has to do with the USB controller ... looks like “No space left on device” spca5xx error [http://ubuntuforums.org/showthread.php?t=247646&page=3]("http://ubuntuforums.org/showthread.php?t=247646&page=3") but it was supposed to be fixed in gspca driver ... any ideas?


syslog -- Webcam does not work _________________________________________________________________________

```
Jun  7 00:19:03 nafarrate kernel: [19541.521613] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found. Conexant(CX11646) 

Jun  7 00:19:03 nafarrate NetworkManager: <debug> [1212790743.009436] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_572_41_noserial'). 

[B]Jun  7 00:19:04 nafarrate kernel: [ 8880.219931] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: init isoc: usb_submit_urb(0) ret -28

Jun  7 00:19:04 nafarrate kernel: [ 8880.222985] ohci_hcd 0000:00:0b.0: leak ed df9f7300 (#81) state 2[/B]

Jun  7 00:19:05 nafarrate NetworkManager: <debug> [1212790745.269752] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_572_41_noserial_video4linux'). 

Jun  7 00:19:05 nafarrate NetworkManager: <debug> [1212790745.280652] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_572_41_noserial_if0'). 
```

__________________________________________________________________________

syslog -- Webcam does work
__________________________________________________________________________

```
Jun  7 00:25:36 ubuntu kernel: [  510.567847] usb 2-4: new full speed USB device using ohci_hcd and address 3

Jun  7 00:25:36 ubuntu kernel: [  510.768881] usb 2-4: configuration #1 chosen from 1 choice

Jun  7 00:25:38 ubuntu kernel: [  512.263530] Linux video capture interface: v2.00

Jun  7 00:25:38 ubuntu kernel: [  512.374914] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1
/gspca_core.c: USB GSPCA camera found. Conexant(CX11646)

Jun  7 00:25:38 ubuntu kernel: [  512.377322] usbcore: registered new interface driver gspca

Jun  7 00:25:38 ubuntu kernel: [  512.378286] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
```

---

### Post by lamiturri on 2008-06-06
Sorry, this is the complete "not working output" when I plug the camera in ...

```

Jun  7 01:14:05 nafarrate kernel: [  336.087736] usb 2-7: new full speed USB device using ohci_hcd and address 4
Jun  7 01:14:05 nafarrate kernel: [  336.291377] usb 2-7: configuration #1 chosen from 1 choice
Jun  7 01:14:05 nafarrate NetworkManager: <debug> [1212794045.933151] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_572_41_noserial'). 
Jun  7 01:14:06 nafarrate kernel: [  336.504195] Linux video capture interface: v2.00
Jun  7 01:14:06 nafarrate kernel: [  336.561838] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found. Conexant(CX11646) 
Jun  7 01:14:06 nafarrate kernel: [  336.563223] usbcore: registered new interface driver gspca
Jun  7 01:14:06 nafarrate kernel: [  336.563235] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
Jun  7 01:14:06 nafarrate NetworkManager: <debug> [1212794046.235148] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_572_41_noserial_if0'). 
Jun  7 01:14:07 nafarrate kernel: [  337.934672] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: init isoc: usb_submit_urb(0) ret -28
Jun  7 01:14:07 nafarrate kernel: [  337.937791] ohci_hcd 0000:00:0b.0: leak ed dfade180 (#81) state 2
Jun  7 01:14:08 nafarrate NetworkManager: <debug> [1212794048.519617] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_572_41_noserial_video4linux'). 
```

---

### Post by lamiturri on 2008-07-04
I solved the problem, it has to do with the USB ports of my motherboard. It looks like they don't give enough bandwidth for PD1170 (they do for the VF0250 ...)

I bought a PCI card with 2 USBs and now it works fine! :)

I hope this hepls ...

---

