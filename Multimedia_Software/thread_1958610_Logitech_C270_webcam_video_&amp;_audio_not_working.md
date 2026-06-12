---
title: "Logitech C270 webcam video &amp; audio not working in cheese"
date: 2012-04-14
forum: Multimedia Software
---

### Post by Merlins on 2012-04-14
My C270 Logitech webcam is recognised as a USB device, but neither sound or video is working.  Am running 12.04 beta2 (Kernel Linux 3.2.0-23-generic-pae), but same problems started happening for me in Oneric from March time (I upgraded to Precise beta in hope it would fix ;-)).  Some symptoms:

1. When I plug in webcam C270 usb device, all hardware lists in Sound Settings are blank! As soon as I remove the device, the hardware devices in Sound Settings reappear.
2. cheese hangs on start when device is plugged in.  As soon as I remove device, cheese starts up but displays "no device found".

The following is the output from dmesg.  Any ideas?

[   55.357074] usb 2-1.7: new high-speed USB device number 4 using ehci_hcd
[   55.608487] Linux video capture interface: v2.00
[   55.630079] uvcvideo: Found UVC 1.00 device <unnamed> (046d:080c)
[   55.657254] input: UVC Camera (046d:080c) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.7/2-1.7:1.0/input/input11
[   55.657422] usbcore: registered new interface driver uvcvideo
[   55.657426] USB Video Class driver (1.1.1)
[   56.016795] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 2: -110 (exp. 2).
[   56.316537] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 2: -110 (exp. 2).
[   56.616402] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 2: -110 (exp. 2).
[   56.660402] 4:3:1: cannot set freq 8000 to ep 0x86
[   56.916288] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 2: -110 (exp. 2).
[   57.216132] uvcvideo: Failed to query (GET_DEF) UVC control 3 on unit 2: -110 (exp. 2).
[   57.515999] uvcvideo: Failed to query (GET_DEF) UVC control 3 on unit 2: -110 (exp. 2).
[   57.815863] uvcvideo: Failed to query (GET_DEF) UVC control 3 on unit 2: -110 (exp. 2).
[   57.915753] 4:3:2: cannot set freq 11025 to ep 0x86
[   58.115584] uvcvideo: Failed to query (GET_DEF) UVC control 7 on unit 2: -110 (exp. 2).
[   58.415467] uvcvideo: Failed to query (GET_DEF) UVC control 7 on unit 2: -110 (exp. 2).
[   58.715330] uvcvideo: Failed to query (GET_DEF) UVC control 7 on unit 2: -110 (exp. 2).
[   59.015037] uvcvideo: Failed to query (GET_DEF) UVC control 11 on unit 2: -110 (exp. 1).
[   59.115198] 4:3:3: cannot set freq 16000 to ep 0x86
[   59.315063] uvcvideo: Failed to query (GET_DEF) UVC control 11 on unit 2: -110 (exp. 1).
[   59.614804] uvcvideo: Failed to query (GET_DEF) UVC control 11 on unit 2: -110 (exp. 1).
[   59.914669] uvcvideo: Failed to query (GET_DEF) UVC control 4 on unit 2: -110 (exp. 2).
[   60.214514] uvcvideo: Failed to query (GET_DEF) UVC control 4 on unit 2: -110 (exp. 2).
[   60.314372] 4:3:4: cannot set freq 22050 to ep 0x86
[   60.514403] uvcvideo: Failed to query (GET_DEF) UVC control 4 on unit 2: -110 (exp. 2).
[   60.814234] uvcvideo: Failed to query (GET_DEF) UVC control 5 on unit 2: -110 (exp. 1).
[   61.114005] uvcvideo: Failed to query (GET_DEF) UVC control 5 on unit 2: -110 (exp. 1).
[   61.413857] uvcvideo: Failed to query (GET_DEF) UVC control 5 on unit 2: -110 (exp. 1).
[   61.513853] 4:3:5: cannot set freq 24000 to ep 0x86
[   61.713831] uvcvideo: Failed to query (GET_DEF) UVC control 10 on unit 2: -110 (exp. 2).
[   62.013567] uvcvideo: Failed to query (GET_DEF) UVC control 10 on unit 2: -110 (exp. 2).
[   62.313433] uvcvideo: Failed to query (GET_DEF) UVC control 10 on unit 2: -110 (exp. 2).
[   62.613199] uvcvideo: Failed to query (GET_DEF) UVC control 8 on unit 2: -110 (exp. 2).
[   62.713194] 4:3:6: cannot set freq 32000 to ep 0x86
[   62.913100] uvcvideo: Failed to query (GET_DEF) UVC control 8 on unit 2: -110 (exp. 2).
[   63.212919] uvcvideo: Failed to query (GET_DEF) UVC control 8 on unit 2: -110 (exp. 2).
[   63.512786] uvcvideo: Failed to query (GET_DEF) UVC control 1 on unit 2: -110 (exp. 2).
[   63.812672] uvcvideo: Failed to query (GET_DEF) UVC control 1 on unit 2: -110 (exp. 2).
[   63.912543] 4:3:7: cannot set freq 44100 to ep 0x86
[   64.112532] uvcvideo: Failed to query (GET_DEF) UVC control 1 on unit 2: -110 (exp. 2).
[   65.112003] 4:3:8: cannot set freq 48000 to ep 0x86
[   65.112514] usbcore: registered new interface driver snd-usb-audio
[   66.159469] 4:3:7: cannot set freq 44100 to ep 0x86
[   67.158910] 4:3:7: cannot set freq 44100 to ep 0x86
[   68.158385] 4:3:7: cannot set freq 44100 to ep 0x86
[   69.157872] 4:3:7: cannot set freq 44100 to ep 0x86
[   70.157340] 4:3:7: cannot set freq 44100 to ep 0x86
[   71.156799] 4:3:7: cannot set freq 44100 to ep 0x86
[   72.156274] 4:3:7: cannot set freq 44100 to ep 0x86
[   73.155740] 4:3:7: cannot set freq 44100 to ep 0x86
[   74.155206] 4:3:7: cannot set freq 44100 to ep 0x86
[   75.154654] 4:3:7: cannot set freq 44100 to ep 0x86
[   76.154133] 4:3:7: cannot set freq 44100 to ep 0x86
[   77.153609] 4:3:7: cannot set freq 44100 to ep 0x86
[   78.153098] 4:3:7: cannot set freq 44100 to ep 0x86
[   79.152515] 4:3:7: cannot set freq 44100 to ep 0x86
[   79.372540] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 2: -110 (exp. 2).
[   79.672280] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 2: -110 (exp. 2).
[   79.972146] uvcvideo: Failed to query (GET_DEF) UVC control 3 on unit 2: -110 (exp. 2).
[   80.152028] 4:3:7: cannot set freq 44100 to ep 0x86
[   80.272009] uvcvideo: Failed to query (GET_DEF) UVC control 7 on unit 2: -110 (exp. 2).
[   80.572001] uvcvideo: Failed to query (GET_DEF) UVC control 11 on unit 2: -110 (exp. 1).
[   80.871740] uvcvideo: Failed to query (GET_DEF) UVC control 4 on unit 2: -110 (exp. 2).
[   81.171493] uvcvideo: Failed to query (GET_DEF) UVC control 5 on unit 2: -110 (exp. 1).
[   81.471369] uvcvideo: Failed to query (GET_DEF) UVC control 10 on unit 2: -110 (exp. 2).
[   81.571364] 4:3:7: cannot set freq 44100 to ep 0x86
[   81.771234] uvcvideo: Failed to query (GET_DEF) UVC control 8 on unit 2: -110 (exp. 2).
[   82.071074] uvcvideo: Failed to query (GET_DEF) UVC control 1 on unit 2: -110 (exp. 2).
[   82.570806] 4:3:7: cannot set freq 44100 to ep 0x86
[   83.570279] 4:3:7: cannot set freq 44100 to ep 0x86
[   84.569748] 4:3:7: cannot set freq 44100 to ep 0x86
[   85.569212] 4:3:7: cannot set freq 44100 to ep 0x86
[   87.068412] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).
[   89.459935] uvcvideo: Failed to set UVC probe control : -71 (exp. 26).

---

### Post by Merlins on 2012-04-15
I notice that the log is showing that the Logitech C270 has a device id of 046d:080c, whereas when I look at [http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/), it has:

046d:0825	Logitech HD Webcam C270

Is it possible that this is a clue?  If its wrong, is there any way to edit some table or something to get the C270 to be recognised correctly?

---

### Post by Merlins on 2012-04-15
When I search round the net, I find some people have C270 webcams with id 046d:080c, and some with 046d:0825 - yet, when I check my usb.ids file, only 046d:0825 is there.  Am I barking up the wrong tree here, or is this a bug?

---

### Post by Merlins on 2012-04-16
Hi, I hope someone can offer some help, I'm really not sure what to do next :-(.  I've posted some more output from dmesg below, after just plugging in the webcam.  It seems similar to the opening post, but maybe someone will spot something for a clue.  I don't know if its relevant, but I'm really lost as to why the device id 046d:080c is returned rather than 046d:0825.  I had this webcam working fine in 11.10 until around early March (then PC broke and had to be rebuilt).  I loaded 11.10 first, but webcam had problems as below, so I loaded 12:04 in hope that newer kernel would fix, but it didn't.  Now I'm lost.

[   88.607719] usb 2-1.7: new high-speed USB device number 4 using ehci_hcd
[  128.215245] usb 2-1.7: USB disconnect, device number 4
[ 2550.729910] usb 2-1.8: new high-speed USB device number 5 using ehci_hcd
[ 2550.992224] Linux video capture interface: v2.00
[ 2551.993789] 5:3:2: cannot set freq 11025 to ep 0x86
[ 2552.990387] 5:3:3: cannot set freq 16000 to ep 0x86
[ 2553.987311] 5:3:4: cannot set freq 22050 to ep 0x86
[ 2554.984043] 5:3:5: cannot set freq 24000 to ep 0x86
[ 2555.980796] 5:3:6: cannot set freq 32000 to ep 0x86
[ 2556.977550] 5:3:7: cannot set freq 44100 to ep 0x86
[ 2557.974304] 5:3:8: cannot set freq 48000 to ep 0x86
[ 2557.974856] usbcore: registered new interface driver snd-usb-audio
[ 2557.974902] uvcvideo: Found UVC 1.00 device <unnamed> (046d:080c)
[ 2562.958062] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[ 2563.954939] 5:3:7: cannot set freq 44100 to ep 0x86
[ 2564.951567] 5:3:7: cannot set freq 44100 to ep 0x86
[ 2565.948319] 5:3:7: cannot set freq 44100 to ep 0x86
[ 2566.945197] 5:3:7: cannot set freq 44100 to ep 0x86
[ 2567.941950] uvcvideo: Failed to query (129) UVC probe control : -110 (exp. 26).
[ 2567.941956] uvcvideo: Failed to initialize the device (-5).
[ 2567.941979] 5:3:7: cannot set freq 44100 to ep 0x86
[ 2567.942019] usbcore: registered new interface driver uvcvideo
[ 2567.942022] USB Video Class driver (1.1.1)
[ 2568.938669] 5:3:7: cannot set freq 44100 to ep 0x86
[ 2569.935330] 5:3:7: cannot set freq 44100 to ep 0x86
[ 2570.932205] 5:3:7: cannot set freq 44100 to ep 0x86
[ 2571.928957] 5:3:7: cannot set freq 44100 to ep 0x86

---

### Post by Merlins on 2012-04-23
Hooray!  I took the webcam back to Currys/PC World and replaced it for another C270.  This one worked first time, and when I checked the device id it showed 046d:0825.  I suspect there is a ?batch? of these C270s with the wrong device id.  Hopefully this series of posts will save someone else spending ages trying to diagnose the problem - when all they need to do is get another webcam.  Now back to 12:04, which I absolutely love.

---

