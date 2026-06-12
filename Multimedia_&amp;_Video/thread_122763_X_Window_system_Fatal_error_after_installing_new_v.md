---
title: "X Window system: Fatal error after installing new videocard"
date: 2006-01-28
forum: Multimedia &amp; Video
---

### Post by user_of_gnomes on 2006-01-28
Hello!

I recently removed an ATI/Radeon Asus 9550 AGP videocard and added an Nvidia MX400/440 32MB plus an SB! Live 5.1 soundcard and now I broke something.

It seems that I can no longer enter my graphical environment and I have absolutely no idea what to do. And from the looks of it, neither does my Linux for Dummies book..

When I try to start the X Windows system (Wheter having it start automatically or by typing X) it gives me the following error: 

> 

(EE) No devices detected

..... Fatal server error: no screens found. Please consult the The X.org Foundation Support... Please also check "'/var/log/Xorg.0.log"

When I type "X -config" (As wiki.X.org tells me to) it says:

> Missing output drivers. Configuration failed

I would appreciate any assistance that you could provide. I believe I am using Ubuntu 5.10 with the latest updates.

---

### Post by MartinG on 2006-01-28
At login go to a console login, and then try```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by user_of_gnomes on 2006-01-28
[QUOTE=MartinG]At login go to a console login, and then try```
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]


It didn't work the first time when the kernel frame buffer (?) was enabled, so I ran it again, disabled the kernel frame buffer (?) and restarted the computer. All is well now. 

Much obliged, Martin.

---

