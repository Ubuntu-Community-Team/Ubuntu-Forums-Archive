---
title: "HDMI sound with an Asus M3A78-EM Rig?"
date: 2010-01-20
forum: Mythbuntu
---

### Post by Mike from Beaverton on 2010-01-20
I'm new to linux but not to computers.  My first PC had a Z8 chip in it. (
Boy, that was a long time ago!)

Over the weekend I built up a dual boot system using a barebones M3A78-EM board and a pcTV HD5500 capture card.   Clean install of XP SP3 and the latest rev of Mythbuntu.
No extra boards except the HD5500 capture card.  I want to use only the integrated outputs from the mother board.  

Everything pretty much worked out of the chute on the linux side of things.   Seamless support of the pcTV card.    The video was jerky at 1st but I installed all the Envyng packages and that did a great job of loading the latest ATI driver's and the video got a lot better.  

The myth set up went okay and I was able to get my av reciver hooked up over the optical output on the back of the box.  It even appears to be true Dolbly as well, which I don't get on the Windows side of the box.  

What I can't get going in Myth is HDMI output to my tv.    The HDMI sound works on my TV when I use VLC or a media player, but despite a lot of googling and late nights I can't get myth to play nice with HDMI sound.  

If it helps alsa sees the HDMI at 1,3


It would really help the spousal approval factor if I could get HDMi audio working on this set up.  

Best Regards,

Mike from Beaverton

---

### Post by ian dobson on 2010-01-20
Hi,

Have a look in setup for the audio device that mythtv uses for output. On my frontend (NVidia/SPDIF to HDMI) I had to change the audio device to ALSA:default, the passthough to "ALSA : plughw:0,3" (without spaces before/after : )and unmute the IECxx device.

Have a look what devices alsa knows about with aplay -l and aplay -L (note lower and uppercase "L").

Regards
Ian Dobson

---

### Post by geekyhawkes on 2010-01-21
Have a look here;

[http://ubuntuforums.org/showthread.php?t=1370228](http://ubuntuforums.org/showthread.php?t=1370228)

I have the same board and have hdmi audio working so follow through the points and hopefully this will help.

---

### Post by Mike from Beaverton on 2010-01-24
I want to thank both of you guys for replying.   I'm still not getting any joy with Audio over my HDMI cable in Myth, but I can't complain becasue the optical Dolby pass through is great and that's really what I want.  

Regards,

Mike

---

