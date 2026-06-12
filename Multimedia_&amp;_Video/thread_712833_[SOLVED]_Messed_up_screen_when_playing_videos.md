---
title: "[SOLVED] Messed up screen when playing videos"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by 000dom000 on 2008-03-02
Hi, just reinstalled ubuntu and for some reason randomly, videos play back as messed up green and pink lines. Sometimes there is sound but sometimes not. Rebooting often does the trick, and sometimes enabling/disabling compiz works. However I havn't found any fixed solution to my problem. This applies to all video players and all video formats.

My player often looks similar to this: 

[http://ubuntuforums.org/attachment.php?attachmentid=56288&d=1200245427]("http://ubuntuforums.org/attachment.php?attachmentid=56288&d=1200245427")

Thanks for any help!

---

### Post by timjayko on 2008-03-02
did you try a:

sudo dpkg-reconfigure xserver-xorg

---

### Post by 000dom000 on 2008-03-02
Did that and rebooted, are there any specific settings I should use? I played a few videos and they worked fine. Left it for 20mins and tried again bbut it's all gone wrong again. In mythtv I get a similar screen just different colours.:confused:

---

### Post by 000dom000 on 2008-03-02
bump. anyone know? or should i report it?

---

### Post by cisforcojo on 2008-03-02
I think it's a Compiz problem. When I had Beryl running a while back, I had the exact same problem. I also ran into some Java interfaces not displaying at all (for example, the application Frostwire).

---

### Post by 000dom000 on 2008-03-02
> **cisforcojo said:**
> I think it's a Compiz problem. When I had Beryl running a while back, I had the exact same problem. I also ran into some Java interfaces not displaying at all (for example, the application Frostwire).

the thing is it sometimes doesn't work when compiz is off and sometimes I solve it by turning it on, but sometimes the other way around...

---

### Post by 000dom000 on 2008-03-03
it seems to be getting worse and worse now, not working unless i reboot and to keep it working i have to keep playing videos. If i leave it for a while and try again it will go all messed up again. I have noticed that the colours are different when running/not running compiz...

---

### Post by ubuntu-freak on 2008-03-03
What graphics device do you have? Also, that dpkg command should be;
 
**sudo dpkg-reconfigure -phigh xserver-xorg**
 
If you have an Intel based card, make sure the driver is "intel" and not "i810".
 
Did the problem start after you first used Totem? It sometimes gives people strange video issues, even when they use other players afterwards (I don't know why this happens to some users). Perhaps you could do a fresh install and not launch Totem at all, just as an experiment. 
 
Nathan

---

### Post by 000dom000 on 2008-03-03
> **reassuringlyoffensive said:**
> What graphics device do you have? Also, that dpkg command should be;
 
**sudo dpkg-reconfigure -phigh xserver-xorg**
 
If you have an Intel based card, make sure the driver is "intel" and not "i810".
 
Did the problem start after you first used Totem? It sometimes gives people strange video issues, even when they use other players afterwards (I don't know why this happens to some users). Perhaps you could do a fresh install and not launch Totem at all, just as an experiment. 
 
Nathan

I have an nvidia 7600gt with the restricted drivers installed. Well I probably did use totem first though I can't remember. I never had any problems before with it though. The first time I noticed it was when I tried out a couple of the example videos on the livecd and it happened. I didn't think much of it though.

---

### Post by Estesark on 2008-03-11
This seems to be the same problem as discussed in [_this thread_]("http://ubuntuforums.org/showthread.php?t=712509"). I'm experiencing it too.

---

### Post by eye208 on 2008-03-11
This is a bug in the NVidia driver. Switching to text console and back fixes it.

---

### Post by 000dom000 on 2008-03-11
Well I did


sudo dpkg-reconfigure xserver-xorg

again and now I get a big nvidia logo at startup and I hav'nt had a problem since. Looks like that must have solved it.

---

### Post by Estesark on 2008-03-17
^ I have no idea what options to select when I try that, so I'm not confident enough to run it.

Restarting X usually solves this problem temporarily, but it returns after a while.

---

### Post by 000dom000 on 2008-03-18
Niether do I to be honest so I selsected all the auto ones, strange though the other day it happened again, but it's been OK  since.

---

