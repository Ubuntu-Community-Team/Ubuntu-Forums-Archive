---
title: "Can't get NVIDIA 180.22 to install on Hardy 64 bit"
date: 2009-02-06
forum: Multimedia Software
---

### Post by WildeBeest on 2009-02-06
The title says it all.

I've tried the links below and a few others and just can't get 180.22 to install.

I have been able to successfully install 177.82 and always re-install it.

Anyone have a successful install on Hardy 64bit?



[http://ubuntuforums.org/showthread.php?t=1054842]("http://ubuntuforums.org/showthread.php?t=1054842")

[http://www.nvnews.net/vbulletin/showthread.php?t=72490]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

[https://wiki.travisbailey.org/index.php/Computing:Ubuntu:Hardy:NVidia:Drivers]("https://wiki.travisbailey.org/index.php/Computing:Ubuntu:Hardy:NVidia:Drivers")

[http://ubuntuforums.org/showthread.php?t=1034543]("http://ubuntuforums.org/showthread.php?t=1034543")

---

### Post by WildeBeest on 2009-02-09
Anyone?

---

### Post by WildeBeest on 2009-02-10
TTT

Anyone?

---

### Post by WildeBeest on 2009-02-11
Come on people, someone must have been able to get the driver to install.

I've tried every, at least every method I could find on here.
All I've succeeded in doing is the low res mode and the not running an X server from nvidia-settings.

---

### Post by WildeBeest on 2009-02-13
ttt

---

### Post by norwoods on 2009-02-13
i was running NVIDIA 180.22 on Hardy 64 bit but moved to 8.10 because kernel upgrades were a problem.

---

### Post by WildeBeest on 2009-02-14
So, how did you get it to install?

---

### Post by DeMus on 2009-02-14
> **WildeBeest said:**
> The title says it all.

I've tried the links below and a few others and just can't get 180.22 to install.

I have been able to successfully install 177.82 and always re-install it.

Anyone have a successful install on Hardy 64bit?



[http://ubuntuforums.org/showthread.php?t=1054842]("http://ubuntuforums.org/showthread.php?t=1054842")

[http://www.nvnews.net/vbulletin/showthread.php?t=72490]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

[https://wiki.travisbailey.org/index.php/Computing:Ubuntu:Hardy:NVidia:Drivers]("https://wiki.travisbailey.org/index.php/Computing:Ubuntu:Hardy:NVidia:Drivers")

[http://ubuntuforums.org/showthread.php?t=1034543]("http://ubuntuforums.org/showthread.php?t=1034543")


I see you also looked in my thread:
[http://ubuntuforums.org/showthread.php?t=1054842](http://ubuntuforums.org/showthread.php?t=1054842)
already. All I can say is that it worked for me. There are others who experienced the same, and there are others who say it does not work. I have no idea why. I am pretty new to Ubuntu myself and I just wrote down what I did to make it work.

I hope for you somebody else, a real expert, can give you some help.
Good luck.

---

### Post by WildeBeest on 2009-02-14
Demus,

Your method always works for the 177.82 driver, which I always go back to.

I have also tried the new 180.29 driver to no avail. They both always result in low res and nvidia-settings reports no x server is installed.

You wouldn't believe how many different procedures I have tried. Very frustrating.

If it makes any difference, my GPU is a 8400GS.

---

### Post by DeMus on 2009-02-14
> **WildeBeest said:**
> Demus,

Your method always works for the 177.82 driver, which I always go back to.

I have also tried the new 180.29 driver to no avail. They both always result in low res and nvidia-settings reports no x server is installed.

You wouldn't believe how many different procedures I have tried. Very frustrating.

If it makes any difference, my GPU is a 8400GS.

I can imagine this very well, I have had the same problems. I tried it all and then suddenly I got it working. Important is to first uninstall and delete everything related to nVidia.
I wish I could help you any further, but I can't.  Sorry.

---

### Post by WildeBeest on 2009-02-15
I finally found an answer that fixed my 180.29 install. Should work for 180.22 also.

[http://www.nvnews.net/vbulletin/showthread.php?p=1933427#post1933427]("http://www.nvnews.net/vbulletin/showthread.php?p=1933427#post1933427")

Basically the driver installer was not replacing the nvidia.ko in "/lib/modules/(my kernel)/updates/dkms". By manually copying it there did the trick.

---

