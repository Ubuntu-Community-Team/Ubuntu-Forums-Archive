---
title: "Webcam Trust wb-3400t, driver problem"
date: 2007-01-25
forum: Multimedia &amp; Video
---

### Post by TADsince1995 on 2007-01-25
Hi guys,

I've just bought a webcam: Trust wb-3400t , use ubuntu edgy eft amd64.

When i plug it into my usb connector, this is what dmesg says:

[  142.935255] usb 1-9: new full speed USB device using ohci_hcd and address 4
[  143.030737] usb 1-9: configuration #1 chosen from 1 choice
[  143.094252] sn9c102: V4L2 driver for SN9C10x PC Camera Controllers v1:1.27
[  143.199987] usb 1-9: SN9C103 PC Camera Controller detected (vid/pid 0x0C45/0x60AF)
[  143.321567] usb 1-9: PAS202BCA image sensor detected
[  143.617885] usb 1-9: Initialization succeeded
[  143.617945] usb 1-9: V4L2 device registered as /dev/video0
[  143.618002] usbcore: registered new driver sn9c102

it seems ok, I can see the /dev/video0 device node, but when I try to view images using Camorama it says:

Could not connect to video device (/dev/video0)

same response from ekiga, it says that no device was found.

Someone can help?

Thank you in advance.

TAD

---

### Post by DigitEyez on 2007-01-26
same here

My dmesg | grep usb
[17179575.696000] usbcore: registered new driver usbhid
[17179575.696000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179700.096000] usb 1-2: new full speed USB device using uhci_hcd and address 3
[17179700.256000] usb 1-2: configuration #1 chosen from 1 choice
[17179700.824000] usb 1-2: SN9C103 PC Camera Controller detected (vid/pid 0x0C45/0x60AF)
[17179700.904000] usb 1-2: PAS202BCA image sensor detected
[17179701.384000] usb 1-2: Initialization succeeded
[17179701.384000] usb 1-2: V4L2 device registered as /dev/video0
[17179701.384000] usbcore: registered new driver sn9c102
[17179701.392000] usbcore: registered new driver snd-usb-audio

Camorama says: "Could not connect to video device (/dev/video0)
Ekige says: "There was an error while opening the device. Please check your permissions and make sure that the appropriate driver is loaded."

But dmesg shows that it is found. I'm kinda lost and could really use some help...

Also when I start camorama with the webcam connected, it crashes. When I then disconnect the webcam and restart camorama the system freezes. The same thing goes when I try to go to /dev/video0 typing cd '/dev/vi' and tab twice. That might be a bug but I don't know were to report it.

thanks

---

### Post by kttrina on 2007-01-26
try this howto
 [http://ubuntuforums.org/showthread.php?t=75284]("http://ubuntuforums.org/showthread.php?t=75284")

now my trust webcam works
i have still problems with camorama (i'm blue!!! :lol: )
but it works on amsn (i can also take photos, and i'm not so blue!!!)

---

### Post by TADsince1995 on 2007-01-29
> **kttrina said:**
> try this howto
 [http://ubuntuforums.org/showthread.php?t=75284]("http://ubuntuforums.org/showthread.php?t=75284")

now my trust webcam works
i have still problems with camorama (i'm blue!!! :lol: )
but it works on amsn (i can also take photos, and i'm not so blue!!!)

Solved installing this: [http://www.angstrom-distribution.org/unstable/sources/sn9c102-1.32.tar.gz](http://www.angstrom-distribution.org/unstable/sources/sn9c102-1.32.tar.gz)

Edgy's sn9c10x driver is buggy. But it complies video4linux2 specifications, so it works only with sonic-snap and ekiga, no amsn or camorama support?

TAD

---

### Post by stijngysemans on 2007-05-25
i've downloaded the file (with another server)
it is full with .c files.
how do I install the driver?
I need to get my webcam working trust wb-3400t in Feisty!

---

