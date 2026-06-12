---
title: "Logitech QuickCam Orbit MP not working in Hardy  8.04"
date: 2008-04-28
forum: Multimedia Software
---

### Post by aaronwe on 2008-04-28
I've got a new install of Hardy, and the built-in UVC drivers don't seem to recognize my Logitech QuickCam Orbit MP.

lsusb shows:
```
Bus 003 Device 008: ID 046d:08c2 Logitech, Inc. 
```

but dmesg gives me:
```
[13942.726660] usb 3-5: new high speed USB device using ehci_hcd and address 8
[13943.038616] usb 3-5: configuration #1 chosen from 1 choice
[13943.046712] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c2)
[13944.046025] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -110 (exp. 26).
[13945.045582] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -110 (exp. 26).
[13945.045591] uvcvideo: Failed to initialize the device (-5).
```

Any ideas? Is there an updated UVC I need to build?

---

### Post by thebackslasher on 2008-05-14
Same here.
(I know this doesn't help very much)

My webcam shows up in lsusb as 046d:0994 Logitech, Inc.
dmesg shows the same complaints about failure to query (135)...

I'll be back when I get more info...

---

### Post by lkeyes on 2008-05-16
Hi...same problem, with an Orbit AV. I'm sort of clueless... I installed on a Dell Optiplex, are there additional drivers that need to be installed?

---

### Post by tstack77 on 2008-06-25
Has this been resolved? I'm looking to pick one of these up.

---

### Post by aaronwe on 2008-06-25
Nope. Still not working for me. Don't have a clue what to do next.

---

### Post by ywecker on 2008-07-22
I have the Orbit MP as well and in researching the drivers I came across another forum [http://forums.vnunet.com/message.jspa?messageID=932033](http://forums.vnunet.com/message.jspa?messageID=932033)

There was a link to some guy's page who writes driver for Linux. The Orbit is not on his list, but you can probably keep an eye on it to see if the driver for the camera shows up.  [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

I hope this helps a little and gives hope to the hopelessly frustrated.

---

### Post by cariboo on 2008-07-22
I've got a quickcam Messanger, Logitech has a link on the support page for the spca5xx driver. I would check with logitech to see if this driver will work with your webcam. There is a link to email support on this page:

[http://www.logitech.com/index.cfm/435/245&cl=us,en](http://www.logitech.com/index.cfm/435/245&cl=us,en)

the driver is here:

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

Jim

---

### Post by uverma on 2009-03-17
I don't now if you guys have found a solution to this, but I followed this thread on the uvc-development mailing list, and the camera worked for me.  I am using cheese to see the capture and it works great with support upto 1280x960 at 15 fps.

I was having exactly the same problem as aaronwe.  But I am running 8.10.

[http://lists.berlios.de/pipermail/linux-uvc-devel/2008-July/003889.html](http://lists.berlios.de/pipermail/linux-uvc-devel/2008-July/003889.html)

HTH

---

### Post by limegreenpatato on 2009-09-30
Hey guys.  I'm having a problem with this too.  I'm using Jaunty though.  when i try it on skype, the video works alright but i can't get the sound to work.  Which kind of makes me think i'm missing a setting somewhere.  I changed my audio capture in the sound prefrences to USB device usb audio (ALSA) but that didn't seem to make a difference.

---

