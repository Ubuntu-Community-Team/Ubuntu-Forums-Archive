---
title: "My ubuntu got frozen..can't live!!"
date: 2010-05-16
forum: Multimedia Software
---

### Post by taito on 2010-05-16
Hi all... I recently upgraded to 10.04... but since then my system often... unbearably often... got frozen... I mean... the mouse pointer moves but doesn't click anything... keyboard works... not always anyway... the only thing I van do to figure it out is CTRL+ALT+CANC... and it's not fine!!
I think it's a problem with video ... drivers perhaps... I've been getting mad for 2 weeks... but I didn't get through it so far! 

I can't work and do anything with my ubuntu ar the moment... it's very demoralising!!

Would you please help me??? 

Thx a lot
 
Sav

---

### Post by Dimarchi on 2010-05-16
Not enough info to work with. System specifications at the very least. You suspect that it is your video card driver that is giving you that headache. In that case:

```
lspci | grep VGA
```please.

---

### Post by taito on 2010-05-17
Thank you very much my friend... sorry to answer so late..
this is my card:

04:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900]

What can I do to heal my headache???

Thx again

---

### Post by Dimarchi on 2010-05-18
Hopefully you are not using ATI's fglrx driver (either the one in repo or the one from ATI's site). If you are, uninstall it. It does not support your video card.

---

### Post by Dkkline on 2010-05-18
Hmm this is just a wild guess but,

I've had the same issue (under windows 7 tho...) after a lot of "google'ng" i had a tip about cleaning the "fan" thing (don't know the exact english word for it...) and I just vacuum-cleaned it (REMEMBER TO MAKE SURE IT DOESN'T ROTATE WHILE YOU DO THAT OR YOU HAVE A DEAD FAN! HOLD A FINGER WHILE YOU ARE DOING IT!!) ever since I've had no problems at all, and the fan is much more silent than before

(sorry about bad english still working on it :( )

Anyway it's just a wild guess

---

### Post by taito on 2010-05-18
MMmhhh.. this thing of fan-cleaning is very strange Dkkline... but I'll give it a try all the same... I admit I never cared to clean it!! (and your english is far better than mine!!)

Dimarchi... thx you first of all.... how do I check if i have that driver installed and - ifso - how do I get rid of it? Have I to install anything else to replace it?? Will the system work properly without it?? 

Sorry for this streak of silly questions... but I can't work any longer with mu computer... it's very unhearthing... I've come to the point I wonder if I'll be able to finish every post I start to write or it'll freeze over before!!

Please help

Thx... Taito

---

### Post by Dkkline on 2010-05-19
I know the vacuum cleaning thing is a bit strange but, you should really give it a try, I couldn't believe my ears after I booted it, nearly couldn't hear it

before cleaning my fan was always running full power when I played games and stuff.

I've only done it that one time, and it helped a lot

Cheers

---

### Post by Dimarchi on 2010-05-19
System > Administration > Hardware Drivers.

If the first line is "No proprietary drivers are in use on this system." you are in luck, you don't have to do a thing...fglrx is not your cause of problem. Just to make it even more sure, the results of:

```
cat /etc/X11/xorg.conf
```

---

### Post by taito on 2010-05-19
ok... below the result of the commend you posted to me:

ee@see-desktop:~$ cat /etc/X11/xorg.conf.failsafe
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "fbdev"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


In reality I don't have a xorg.conf file... I found only a Xorg.conf.failsafe.. it's the above one. Is it normal?

Does it suggest any solution??

Thank you very much my friend

---

### Post by Dimarchi on 2010-05-20
As far as I know, it is. It appears that the problem can't be blamed on ATI's drivers. What else it could be, I have currently no idea. Has your Ubuntu install frozen when you have used previous versions, or is it just apparent with this latest version?

---

