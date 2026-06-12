---
title: "Big Problem With HDA Sound"
date: 2008-08-11
forum: Multimedia Software
---

### Post by Fillivan on 2008-08-11
k, i am new at ubuntu, i tried to install it a few days ago, i had no problems except the Sound... i followed every step on 

[https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=(CategoryHardware](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=(CategoryHardware))

but still no luck...

after running this command:
cat /proc/asound/card0/codec#* | grep Codec

i get this:
Codec: Realtek ALC660-VD
Codec: Motorola Si3054

My sound card is ALC861 but it uses the same codec as the 660 version (i checked it). I did everything and i got no sound at all... i also searched the forum for solutions and still no result(i think i tried most of the solutions :( ) :(

I also noticed that when i run dmesg i don't see anything containing snd_ in the msg i receive in the terminal... can someone help me pls :(

i am using an Asus laptop. :confused:

---

### Post by Kevbert on 2008-08-11
Please take a look at this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=257304")

---

### Post by markbuntu on 2008-08-11
This thread here tells you how to set up just about any hda card/chip:


[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by Kevbert on 2008-08-11
> **markbuntu said:**
> This thread here tells you how to set up just about any hda card/chip:


[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

Good post :)

---

