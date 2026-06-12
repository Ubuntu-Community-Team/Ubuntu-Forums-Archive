---
title: "Microphone problem with Webcam Quickcam messenger (046d:08f) but video OK"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by timshel on 2007-12-10
Hello,
New French Ubuntu user (7.10 Gutsy), I try to install and configure my Webcam "USB Logitech Quickcam messenger" (046d:08f0). The Webcam is recognized natively under Gutsy (at least for me). The video is OK on the other hand the microphone is not working. 
I tried to install the driver (Driver) QC-USB Messenger as described in the doc ubuntu-fr but problem at installation as to most people. 
I checked on the configuration in the ALSA mixer. In the Sound Control Panel, I have a slider with the title "Video" but only with a speaker (no microphone). Other info, my sound card is a nForce2 and functioning properly (reading CD, MP3, sound system, ...)
I also tried the patch of snd-usb-audio.ko seen on different forums ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93822](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93822)), but without result. 
In the system logs, I have a lot of error messages that I do not understand about snd_usb_audio (see logs in var_log_syslog.txt attach file, the error occurs when I plug the Webcam). 

Could someone help me ? 
Thank you in advance.

---

### Post by timshel on 2007-12-17
Hello,
Am I the unique person having a such problem ?
Bye.

---

### Post by aaron1 on 2007-12-24
Hey, Timshel

I have had the same problem, when installing the camera. I use windows vista. I found reinstalling the program worked, as long as I cancelled any prompt microsoft gave me to install device drivers for the microphone, and just waited for the cd to install logitechs own device drivers. It seems to be a conflict between the two device drivers. 

I can't stop the prompts popping up now, and have to keep dismissing them..... any ideas? 

But at least the mic works. I hope that works for you.

Aaron

---

### Post by Azzco on 2008-05-22
I think that the last reply can be ignored (it doesn't help getting the mic running in ubuntu by using vista does it?)

Anyways I've got the same kind of webcam, running hardy it works, but the quailty is nothing to speak of.. I'm not sure if you still have the problem or not or if you'll even read my reply though.
I think it works due to under the hood improvements and it might also have something to do with using pulseaudio.

I hope that helps ;)

---

