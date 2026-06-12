---
title: "can't see incoming webcam in skype"
date: 2008-05-11
forum: Multimedia Software
---

### Post by savethewabbit on 2008-05-11
hi, 
i'm using skype for web chat, and i can see myself (and people see me), however i cannot see other people's incoming videos (i see all black), even though they can see themselves. 
is it a known bug or i'm doing something wrong? there don't appear to be settings for incoming videos in skype, so i have no idea... 
any help would be appreciated. thanks!

---

### Post by viperskunk on 2008-09-28
> **savethewabbit said:**
> hi, 
i'm using skype for web chat, and i can see myself (and people see me), however i cannot see other people's incoming videos (i see all black), even though they can see themselves. 
is it a known bug or i'm doing something wrong? there don't appear to be settings for incoming videos in skype, so i have no idea... 
any help would be appreciated. thanks!
same problem here.

---

### Post by masq on 2009-03-02
Did you guys find it out?

cuz I have the same problem and can't find out how to fix it...

---

### Post by krlhc8 on 2009-03-05
I start skype in a terminal with this command to get video working for me: 

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

### Post by lynchmob4444 on 2009-05-10
Hi all out there...
 
I just ran into the same Skype problem 
 
I have win XP and have Skype 4.0 and logitect web cam
 
I can see me on my screen I cannot see the caller on my screen.. Big ? on the shoulders of an animiated  person
 
Caller can see me AND see themselves on their screen.
 
We want to see our grandkids BUT we are frustrated.
I would call myself a "low intermediate" re skill with a PC
 
Please help
 
Thanks

---

### Post by aquamammal on 2009-12-13
Same Problem. Anyone? Thanks.

---

### Post by gradinaruvasile on 2009-12-13
Is this problem occuring Ubuntu-Ubuntu and/or Windows-Ubuntu? If it only occurs Ubuntu-Windows, it might be a Windows client update - just a speculation though.

What version of Skype do you guys use? And from where was it installed (repositories/skype site)?
Also what Ubuntu version/video card do you use? 
If you use compiz, does it work if its off?

I (and the family) use Skype 2.1 beta1 from the Skype site on Ubuntu 9.10/Ubuntu 9.04/Ubuntu 8.10 but never saw this problem. Also it worked with Windows clients too.

---

### Post by aquamammal on 2010-01-19
Anyone? So frustrating.

---

### Post by fruitz on 2010-04-25
Same problem for me.....

---

### Post by azizzle on 2010-05-16
same problem here

---

### Post by saias on 2010-05-17
exact same problem..

X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 
X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes)

several times..

is that an x server error?

---

### Post by manutdnsubi on 2010-05-17
I also have this problem. Same errors as above. I really need it to work because my girlfriend is in Spain for the summer :( Anyone fixed this yet?

---

### Post by saias on 2010-05-18
good news! problem solved!

solution can be found [here]("http://ubuntuforums.org/showthread.php?t=1318506")

post 13 worked for me. it seems to be an issue with the Cairo-dock application.

have fun on skype!!!

---

### Post by dda on 2011-10-18
In my case, the problem root was different. I solved by installing "current" Nvidia driver. The older (.173) driver was installed earlier, and it caused the incoming video malfuncton. With the new ("current") driver it works fine.
 
Here is the diff of xvinfo output. Seems like the old drived had wrong saturation, hue and contrast margins?
 
[FONT="Courier New"]$ diff igor.xvinfo.old igor.xvinfo.new
5c5
<     port base: 286
---
>     port base: 310
73c73
<       "XV_BRIGHTNESS" (range -512 to 511)
---
>       "XV_BRIGHTNESS" (range -1000 to 1000)
76c76
<       "XV_CONTRAST" (range 0 to 8191)
---
>       "XV_CONTRAST" (range -1000 to 1000)
79c79
<       "XV_SATURATION" (range 0 to 8191)
---
>       "XV_SATURATION" (range -1000 to 1000)
82c82
<       "XV_HUE" (range 0 to 360)
---
>       "XV_HUE" (range -1000 to 1000)
[/FONT]
(also posted at [http://community.skype.com/t5/Linux/No-incoming-Video/m-p/218812](http://community.skype.com/t5/Linux/No-incoming-Video/m-p/218812))

---

### Post by MidnightOwl on 2012-02-24
Same issue ...

No incoming video displayed.

I can see my self and audio is fine.

I am using 
 
ubuntu-ubuntu (version 10.04 and Skype 2.2 Beta). Will the above resolutions work for me?

On Acer One AOA150

---

