---
title: "[SOLVED] geforce 4000 lines at startup/shutdown no grub"
date: 2006-10-19
forum: Multimedia &amp; Video
---

### Post by jkroto on 2006-10-19
I recently upgraded to an evga geforce mx 4000 in an old Dell that I'm using to run (and learn) Ubuntu from the integrated video.  I followed the how-to guide on installing such a card with intel integrated video and all seemed to go well.  Problem that I have now is that on startup and shutdown I no longer see the Ubuntu script.  Additionally, prior to the script on startup I did/do have a Grub menu since I'm dual booting with XP (although not very often).  The only thing I see at startup and shutdown now is a bunch of brown (Ubuntu brown) lines.  Any help out there for this noobie?
Thanks in advance for the help.
John

---

### Post by ReaderRat on 2006-10-19
Everywhere I have looked , the eVGA GeForce MX4000 is supposed to be compatible with Linux. In two places, though, it was mentioned as an nVIDIA card. Is it an nVIDIA card? If so, then this might help:  [**Installing Nvidia Drivers**](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
Also, from your post it sounds like you are trying to use **both** this card **and** an onboard integrated graphics solution. I don't believe this can be done. (I may be wrong. I am a newbie too.)
Anyway, good luck....

---

### Post by jkroto on 2006-10-19
Thanks ReaderRat, I had already installed the nvidia drivers following the guide, however, now that this problem occured I'm starting to wonder what I've done.  I'm only using one monitor (hooked up to the geforce card) and if the integrated video is still active it's unintentional on my part.
Everything else seems to work, it's just the big problem of not being able to see the grub menu.

EDIT - to answer your question about the card, as I understand it, evga makes the card but it has an nvidia chip or component.  Based on looking I think there are a lot of video cards and mobo's that have the nvidia chipset but are made by other mfg's.  That's my take on it.

> **ReaderRat said:**
> Everywhere I have looked , the eVGA GeForce MX4000 is supposed to be compatible with Linux. In two places, though, it was mentioned as an nVIDIA card. Is it an nVIDIA card? If so, then this might help:  [**Installing Nvidia Drivers**](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
Also, from your post it sounds like you are trying to use **both** this card **and** an onboard integrated graphics solution. I don't believe this can be done. (I may be wrong. I am a newbie too.)
Anyway, good luck....

---

