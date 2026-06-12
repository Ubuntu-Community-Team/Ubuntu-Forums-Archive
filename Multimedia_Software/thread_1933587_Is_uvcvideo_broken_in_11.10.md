---
title: "Is uvcvideo broken in 11.10?"
date: 2012-02-29
forum: Multimedia Software
---

### Post by AndrewWalker on 2012-02-29
I'm trying to get a usb webcam working in ubuntu but it doesn't seem to function. The camera is as follows

Bus 002 Device 002: ID 046d:08c2 Logitech, Inc. QuickCam PTZ

but no device appears in /dev for it. There is also an error in dmesg when it is plugged in



[ 6041.308129] usb 2-4: new high speed USB device number 2 using ehci_hcd
[ 6043.080221] 2:3:3: cannot set freq 16000 to ep 0x86
[ 6043.080791] usbcore: registered new interface driver snd-usb-audio
[ 6043.080859] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c2)
[ 6048.080163] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[ 6048.094828] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[ 6048.094838] uvcvideo: Failed to initialize the device (-5).
[ 6048.094976] usbcore: registered new interface driver uvcvideo
[ 6048.094982] USB Video Class driver (v1.1.0)

Does anyone else experience this? I also have a dual tuner TV card which use /dev/video0 and video1 but this shouldn't affect the webcam should it? I think it should just be called /dev/video2 and just work.

Any guesses?

---

### Post by ajgreeny on 2012-02-29
What are you trying to do with the webcam?  have you installed **cheese** if it is not already installed and seen if the camera works with that?

---

### Post by AndrewWalker on 2012-02-29
Yes, and it doesn't work. The /dev node doesn't get created to start with. I also found that if I boot my machine with the cam connected the x server plays up and I get no audio. It looks like a kernel issue to me but I don't know where to start to fix it.

---

### Post by Merlins on 2012-04-05
Hi Andrew, I think I have started having a similar problem, with very similar messages.  I have Logitech cam which worked fine a fortnight ago on Ubuntu 11.10.  Then my PC broke (don't ask!) and I got a new machine, installed fresh 11.10, and now I get repeating connects/disconnects of the webcam, with multiple "cannot set freq nnnnnn to ep 0x86" and messages like yours.  Too much has changed for me to narrow things.  If you solve, please post.  I'm almost wondering whether to try 12.04 beta.

---

### Post by Merlins on 2012-04-06
Well I just upgraded to 12.04 beta, and I still get the problem.

---

