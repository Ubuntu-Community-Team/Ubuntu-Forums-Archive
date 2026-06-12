---
title: "NO sound at all..."
date: 2010-05-12
forum: Multimedia Software
---

### Post by learning_ on 2010-05-12
so i just built a comp from the ground up, installed lucid, everything looked great. i set it up at a friends house because he is more experienced in this, and i am just starting out. he had everything working, then i brought it home and hooked my speakers up... nothing came out. he said he installed or activated (not sure which) pulse audio, and told me it was superior to the previous audio managers. also said it should work fine with no problems when i got home. i am using a GIGABYTE mobo, model GA-MA785GMT-UD2H. i have no sound card, so i am using the onboard sound. i dont know what the problem is or could be. can you help me out?

---

### Post by cchhrriiss121212 on 2010-05-12
Pulse is the default audio server in Ubuntu so I don't know what your friend did, possibly installed pavucontrol. First step would be to check if the system recognises your card, which you can do by going to Preferences>Sound and looking under hardware. Also check that you have your speakers are connected to the correct output jack.

---

### Post by Popaul on 2010-05-12
Have you checked the extensive:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound+lucid](http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound+lucid)

I always forgot one or 2 things, and this is the source... well worth a 'favorite' link. Almost everytime I upgrade to a new version of Ubuntu, the sound goes off... and I was always able to restore it with simple tricks from this comprehensive guide.
Not very good for Ubuntu, but a lot of thanks for the guys who put this guide up.

---

### Post by lidex on 2010-05-13
Or try this one:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
Report back to this thread with your progress.

---

### Post by learning_ on 2010-05-14
i have tried this link, didnt help. [http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound+lucid](http://ubuntuforums.org/showthread.php?t=205449&highlight=no+sound+lucid)

any other thoughts?

---

### Post by lidex on 2010-05-14
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. *_Also helpful is the make/model of your PC/Laptop._*

---

### Post by learning_ on 2010-05-17
thank you for the help, i had my friend come over last night and help me figure it out. apparently some driver had been disabled through some series of clicks and keystrokes :oops:

thank you for the help though.

i am currently having a problem with something else though, if you can help direct me to a solution that'd be great.

i installed virtual box from the sun website, got windows xp running through it (for some reason, windows wont install on my hd, it doenst recognize there being an hd installed. im assuming it might be because it is a sata drive). everything runs fine, except i cannot mount any usb or disk to the os. i cannot figure out why. when i click the "mount usb" option, none of them are available (the options are my keyboard, mouse, network adapter, and my flashdrive). do you know what might be the issue?

---

