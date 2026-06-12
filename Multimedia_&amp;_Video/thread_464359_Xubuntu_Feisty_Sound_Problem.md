---
title: "Xubuntu Feisty Sound Problem"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by Raybo on 2007-06-04
I can get sound by using **aplay** from the **command line** in a Virtual Terminal but if I try to play any sound file from the Xfce GUI the machine locks up completely.  Powering off and on is the only way back.

I am running Xubuntu 7.04 on a Dell Inspiron 3200 laptop.  It has a cs4232 sound chip.  I disabled the pnpbios and manually installed the module using alsa module snd-cs4232.  

I've checked /proc/interrupts and /proc/dma and see no conflicts.  I even tried using different interrupt and dma settings to no avail.  The Xfce mixer program see the sound card as a cs4236.

Somewhere I saw suggested that esd should be running but when I try that I get a series of errors about the soundcard being configured improperly.  I am hoping someone out there may have encountered and solved a similar problem.

BTW, I did have the sound card working properly with Dapper 6.06.  Any help or comments are appreciated.  Cheers!

---

### Post by Raybo on 2007-06-07
Replying to my own post:  I gave up on the Feisty Fawn.  After many google searches and trying everything I could think of, I just could not get the sound to work with the GUI.  

So I downgraded.  I did a new install of Xubuntu 6.06 Dapper Drake since it worked with that release and it will be supported till 2009.  The following message helped me configure the OS and the sound card.

[http://ubuntuforums.org/showthread.php?t=282624](http://ubuntuforums.org/showthread.php?t=282624)

My machine Dell Inspiron 3200 has a cs4232 sound card so I substituted snd-cs4232 where he used snd-cs4236.  I set the bios for non-pnp OS, configured the sound card with the appropriate settings and it worked on first reboot.:)

---

