---
title: "[Help]nVidia GTX 480 driver with ubuntu 10.10 (boots to command prompt only!)"
date: 2010-10-28
forum: Multimedia Software
---

### Post by JDuBZisFADED on 2010-10-28
Hey all,
Recently Ive bought a new gaming system and was getting back to my good old dual boot ubuntu setup. When I installed ubuntu all went well and it recognized all components from my pc and handled them correctly. But after I installed the latest graphics drivers I was unable to boot into my login screen/gdm ui. I was instead greeted with the recovery terminal requesting me to login. I tried to kill/start gdm and that was a no go/ Also Whenever I get into this terminal I cannot get out. I have tried editing xorg.conf and it is a no go. All I want is a driver to be able to acheive my 1900x1080 resolution. I cant look at a 37inch lcd with 800x600. The space is useless. Please help me out here. I want to get back to my programming work but cannot because i cant look at this crappy resolution. I have tried installing different versions of the driver to no avail. and I had driver support on video like last week or so. Could it be my dual boot. highly doubt it but maybe??? PLEASE HELP!!!

---

### Post by JDuBZisFADED on 2010-10-29
please help me out someone. if you have an android phone you might know me. im hero_over from xda and [www.bakedsnackshack.com](www.bakedsnackshack.com) . I cannot do any android work with this crappy 800x600 resolution! Im sorry to double post but I am willing to pay 20 dollars to whoever solves my problem today. PLEASE PLEASE PLEASE HELP ME.

---

### Post by Dscottmc7 on 2010-10-29
Hey, man...sorry to say I have the same problem.
In the meantime check (sudo nano) your /var/log/Xorg.0.log   for trouble shooting every detail. 
"sudo service gdm halt" before everything, then get rid of everything NVIDIA. 
install the Nvidia kernel moldule  (my problem!!!)
install "nvidia-current" 
sudo service gdm start

BUT I'm screwing something up.  I'll report when I find it.
Ta':confused:

---

### Post by JDuBZisFADED on 2010-10-30
> **Dscottmc7 said:**
> Hey, man...sorry to say I have the same problem.
In the meantime check (sudo nano) your /var/log/Xorg.0.log   for trouble shooting every detail. 
"sudo service gdm halt" before everything, then get rid of everything NVIDIA. 
install the Nvidia kernel moldule  (my problem!!!)
install "nvidia-current" 
sudo service gdm start

BUT I'm screwing something up.  I'll report when I find it.
Ta':confused:
Thanks a lot for the response. I am able to install the latest drivers without any module problems whatsoever. I an install it through command login and throught "additional drivers" but when I reboot I am always taken to a command prompt and am unable to load a gui. I'm guessing its breaking nouveau when I install it. But nouveau only let's me us 800x600. Please help. 20 dollars through paypall will go to whomever can solve my issue

---

### Post by cwwilson721 on 2010-10-30
> **JDuBZisFADED said:**
> ... Please help. 20 dollars through paypall will go to whomever can solve my issue[Give me my 20...]("http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia")
Any questions/issues, message me thru this forum...

If you want a deeper explanation, [go here]("http://www.linuxquestions.org/questions/slackware-14/a-guide-enabling-3d-acceleration-in-x11-402003/"). 

I've been doing this awhile...

---

### Post by JDuBZisFADED on 2010-10-30
> **cwwilson721 said:**
> [Give me my 20...]("http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia")


I would be glad to if i havent tried that 1 million times lol. I definately thank the effort though. So i solved it but im pissed about the way i did it. I removed my tv tuner from my pc. which i use as my dvr because its only one i have. and i noticed ubuntu had crashed. i was thinking that maybe the tvtuner was being recognized as a video output device so i reinstalled without the tuner card and the driver loaded up fine as usual anmd when i rebooted. 1920x1080 and all my graphics effects! yay!

---

