---
title: "Built-in Microphone on Dell Inspiron 1520 works on skype"
date: 2008-06-12
forum: Multimedia Software
---

### Post by felipunk on 2008-06-12
Hi everybody!

I'm posting this message just for those who like me were frustrated trying to make the built-in mic of a Dell Inspiron 1520 to work with skype 2.0.0.68.

I'm not giving any details on the software installation, I just tell you that I got Skype from the non-free repository ([http://packages.medibuntu.org/](http://packages.medibuntu.org/)).

My problem was that I don't have no sound from the microphone (I was testing with Skype test call, with no success) every thread I've found point to the alsamixer configuration and I follow them with no glory. Finally when I was about to quit I found a way to do it (this configuration worked with Ubuntu 8.04 on Gnome).

Locate the Volume Control applet on your panel (generally, close to the system tray), right click it and click on Open Volume Control. Once there chose the File menu and select Change Device, choose "Capture: ALSA PCM on front:0 (STCA92xx Analog) via DMA (PulseAudio Mixer)". Once there I realized that the Master channel (the little speaker icon) was disabled, I just enable it and voila! That's it the sound its working as expected on Skype.

That's it! I hope this can help to anyone on the forum.

If you ave any comments on this please let me know!

See you!

---

### Post by vandorjw on 2008-06-14
Hey thanks for that.
I have the same problem as you did, but with Xubuntu.
Any idea where I can get the fix for that?

I have Dell Inspiron 1520, running Xubuntu 8.04
(My Webcam works using skype, but my built in mic does not)

Cheers and Thanks CC7

---

### Post by kb1lqd on 2008-06-14
Try going into terminal and type ```
alsamixer
```

Then change the option all the way on the right the is labeled "Digital" but above it says analog. Change that option to say Digital. worked in my case...

---

### Post by harrygg on 2008-06-15
Thank you guys. kb1lqd's solution worked with me.

---

### Post by vandorjw on 2008-06-16
I use Xubuntu, and his solution worked for me also.
Thanks and cheers
   -CC7

---

### Post by wangjiaji on 2008-08-17
Yes, that worked, thank you so much!

---

### Post by turbojackie on 2008-09-11
Thanks, worked for me.kb1lqd

---

### Post by qbox on 2008-11-25
Not worked for me
I have Ubuntu 8.04
Any idea?

---

### Post by qbox on 2008-11-25
I make it work
[http://ankurjain.org/2007/11/03/ubuntu-gutsy-microphone-problem-on-dell-inspiron-1520/alsa-gnome-mixer-options-tab/](http://ankurjain.org/2007/11/03/ubuntu-gutsy-microphone-problem-on-dell-inspiron-1520/alsa-gnome-mixer-options-tab/)

---

### Post by figi22 on 2008-11-27
Anybody got a solution for 8.10 and a Dell Studio?   I don't see the same options if I type in alsamixer .

EDIT:

OK no problem, I just tried here:
[http://ubuntuforums.org/showthread.php?t=843012&highlight=microphone](http://ubuntuforums.org/showthread.php?t=843012&highlight=microphone)

and used the Try this first.   Finally managed to get the right Volume Control option by checking all the boxes under preferences, and changing the Digital Input Source from Analog to Digital Mic 1 etc.

---

