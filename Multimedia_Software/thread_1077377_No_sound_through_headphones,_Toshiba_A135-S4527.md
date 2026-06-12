---
title: "No sound through headphones, Toshiba A135-S4527"
date: 2009-02-22
forum: Multimedia Software
---

### Post by charlieddayton on 2009-02-22
Hi.

I have the following problem on 8.10:

On a toshiba Satellite A135,  the sound plays properly from the speakers but when I connect headphones they don't work.  Sound keeps playing trhough the laptop's speakers.

I already checked the Volume control and headphones are at max sound.


Please help.

---

### Post by PRDS on 2009-06-25
To get headphones working on your Toshiba A135-S4527 notebook:

First, type the following command into the terminal:

gksudo gedit /etc/modprobe.d/alsa-base.conf

At the bottom, add the following command: 

options snd-hda-intel position_fix=1 model=lenovo



Reboot! Done!

Note: This method seems to play sound through both the speakers and the headphone jacks. You will have to mess with volume control to enable headphones only. If there is a way to make the speakers turn off and the headphones turn on automatically, I would be interested in hearing about it.

---

### Post by PRDS on 2009-06-25
Also, this method [see my previous post] works on Ubuntu 9.04 as well.

---

### Post by TheIrisBaNe on 2009-08-12
I have the same problem. I tried following your steps but will admit when it comes to linux I am noobzorz and have no clue what i'm doing. I tried typing that in terminal but it said
bash: options: command not found.  
 
 can you help me please? I have been through hades with this lappy. I bought it used from a guy who whiped vista home from it and added xp home. when I got it it couldn't find any sound devices. So I tried ubuntu. Now the speakers work great just no headphones...I plug the in and nothing while the speakers still play. Also I'm not sure If I have all the drives or packs I need for the video and such. Please help this noob! I just want toget everything working before my cross country plane trip to cali!
Thanks

---

### Post by rinyotsu on 2010-03-10
I did the above solution by PRDS on my Toshiba Satellite A135-S4527 running pure Ubuntu goodness (Ubuntu 9.04) and it enabled headphones to work and also turned the speakers off automatically. Thanks for the help!

---

### Post by hegomir on 2010-07-19
Thank you, the above solution worked on my Toshiba Satelite L670. Again, thank you! :D

---

