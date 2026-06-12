---
title: "Genius Facecam 310 Webcam not working"
date: 2011-05-21
forum: Multimedia Software
---

### Post by Barbalras on 2011-05-21
Hi everyone!

I bought a Genius Facecam 310 Webcam a few months ago and I still cant make it to work with ubuntu.

Actually it does work in Cheese but I can't use it in skype. Skype detects it (under video devices) but the test area remains black.

The webcam comes with a built in mic but I couln't make it to work. Whenever I go to system->preferences->sound and I try to change the configuration of the input related to the webcam mic Pulseaudio crashes... (???)

lsusb gives:
Bus 004 Device 002: ID 0458:7070 KYE Systems Corp. (Mouse Systems) 

any thoughts?

I'm using 11.04 but I had the same issue with 10.10

---

### Post by Jarks on 2011-12-24
Same here - in 11.10. 

The webcam works fine in Cheese, Skype and GoogleTalk.

But the** built-in microphone doesn't work in Skype**. I can see it in pavucontrol but when I turn it on (analog mono input) it works for a little while (5 sec ?) and then freezes. 

Does anyone know how to make it work, please?

Update: the mic works in GoogleTalk because there is the option "FaceCam 310 analog mono". In Skype is "Pulse audio server" only. And it's broken.

---

### Post by andresv on 2012-03-11
Same here (ubuntu 11.10). Facecam 310 does not work. Running gstreamer-properties gives the answer

[FONT="Garamond"][COLOR="Blue"]Video for Linux 2 (v4l2): Error starting streaming on device '/dev/video0'.[/COLOR]
[/FONT]

I wonder what may be going on with this (perhaps the kernel is at fault).

Does anyone have a solution for this (very frustrating) issue?

av

---

