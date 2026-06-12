---
title: "Sound Fix for Intel ICH4"
date: 2005-11-09
forum: Multimedia &amp; Video
---

### Post by bb002 on 2005-11-09
I have a Laptop with the Intel ICH6 sound controller. Sound does't work be default because breezy had enabled an "external amplifier" by default this caused me to have no sound. However simply turning off the external amplifier gave me sound! I'm making this post since I haven't seen this fix anywhere else. Every fix I come across envolved recompiling alsa or the kernel, both of which didn't fix my problem. I'm sure this fix can be applied to other cards as well. Assuming Ubuntu already sees your sound card, atleast.

goto applications -> Sound and Video -> Volume Control.

Then goto edit -> preferences in the volume control. look for "external amplifier" (or just check everything like i did. there is nothing wrong with it. Just that the volume control gets cluttered.) Click close to accept changes. Click the "switches" tab and uncheck "external amplifier", at this point my speakers began to blare since i had all the sound slider's maxed and a video playing... ;) Them blaring wasn't a problem it was the suddeness. I almost needed a clean pair fo shorts. For laptop speakers they are pretty darn loud. Hopefully this will help someone out there.

---

### Post by adduds on 2005-12-01
THANK YYOU SOOOOOOOOOOOOOOOOO MUCH MANG! LOL 5 DAYS IT'S TAKEN ME

THANK YOU 

CHEERS!!!
ad

---

### Post by bb002 on 2005-12-05
No Problem, you're welcome. I was beginning to think I was the only one that suffered this problem.

---

### Post by coderasm on 2005-12-06
OMFG!!!!!!!!!!, you are god.  I was about to shoot myself at not being able to figure this out.  Thanyou so very much.

---

### Post by Mosey on 2005-12-15
You Are A Golden God!

A Golden Friggin God!

Do You Have An Adress Where I Can Send You Cash For Being Such A Relentless Badass?!

Heeeeeeeeeeellllllllllll Yeeeeeeeeeeeaaaaaaaaaaaahhhhhh

---

### Post by anil_robo on 2005-12-16
Weird!

I have an Intel ICH6 soundcard. My sound plays only when I have external amplifier enabled. The sound goes away when I disable external amplifier! Exactly the opposite of what everyone else has observed in this thread! :-/

---

### Post by ArmadaEnder on 2005-12-20
Ether I'm a complete idiot or my version is messed up. I followed your tutorial and the only problem for me was the fact that there is no "external amplifier" option. I Don't know how this is possible but if anyone has an idea as to what I can do, please send me a message. Thank you very much.

---

### Post by tinuviel on 2005-12-25
THANK YOU SO MUCH!!!!! 

Could you find a way to post this in more places?

BTW ArmadaEnder- the first time I clicked "Switches" I didn't get the external amplifier option either, but it was there a few minutes later.

---

### Post by wm_eddie on 2005-12-27
If you are even in Japan within the next 4 months (or Puerto Rico in the next 3 after that (or in Pittsburgh in the next 6 months after that)) send  a PM.  I owe you a beer.

---

### Post by ethan29 on 2005-12-29
Thank you very much!! I'm new at linux ubuntu and this little things make me crazy.

Thank a lot!
Bye:p

---

### Post by AndriusKulikauskas on 2006-01-25
Thank you for your advice!  It's still not quite working for me - sound is only coming from a few places such as Flash pages - but at least I know that my soundcard works.  It's a big step forward.  Thank you!  If anybody might advise I am working further on this at [http://ubuntuforums.org/showthread.php?p=672483#post672483](http://ubuntuforums.org/showthread.php?p=672483#post672483)

---

### Post by sublime on 2006-01-26
i just thought i would bring this thread back from the dead to let you know you are a god amongst men.  ive been trying to get my sound to work for like 3 hours.  thank you

---

### Post by bb002 on 2006-01-30
I completely forgot about this thread and I must say that I am pleased to have help so many people.

You are all welcome.

---

### Post by jsfarrow on 2007-02-27
The details were a bit different, but I used this tip to get my mic working in Edgy on an HP nc6220.  In my case, I had to enable the switches in the Gnome Volume Control for "Microphone Capture" and "Mic Boost".  

Working great with Skype now!  Thanks!!

- Scott

---

### Post by aikishugyo on 2007-08-22
The correct settings are as follows (after much frustration and experimentation):

SWITCHES: Mic Capture ON
                   Mic Boost    ON
                   (Stereo Mic ON)

OPTION:     Mic Select MIC1

RECORDING: Capture must be at some non-zero volume

PLAYBACK: Mic OFF
                    PCM and/or mono and/or other playback should be at some non-zero volume

Mine does now work in SkyPE, yay!

---

### Post by netron on 2007-08-22
i dont see any "external amplifier" option

playback
--------------

Master
PCM
Capture Mux

---

