---
title: "Yet another xserver/gdm crash"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by Gusse on 2007-04-29
Hi,
I've tried to install the NVIDIA drivers, using the guide from [www.ubuntuguide.org]("www.ubuntuguide.org"), which included editing xorg.conf and gdm.conf-custom and apt-getting nvidia-glx. As for so many others the xserver crashed on boot, saying something about gdm, a command that couldn't be executed (i can get the exact error if its important). Using the terminal i reverted the changes, ran dpkg-reconfigure xserver-xorg. I also installed the x-window-system-core. I get the same error when i boot, but if I log in and startx it starts perfectly, even has a higher resolution (I added one when I reconfigured) than before. It says now that the nvidia driver is not enabled. If i log off i get back to the terminal and if I reboot I have to manually startx.

Bottom line:
What is going on (I'd like to understand this), and how can I get back all old setting without formatting?

Thanks in advance.

I'm running 7.04 x386 on an AMDx2, NVIDIA 7800GT.

---

### Post by Gusse on 2007-04-29
Help. Anyone? I kind of feel this is an easy one for someone with just a little experience.

---

### Post by Lumus on 2007-09-01
Was this issue fixed? I'm having exactly the same problem. Gdm is trying to find Xgl but it doesn't exist. However when I boot using _startx_ it works perfectly fine (except that the shutdown button doesnt have all the option) I know it's a configuration issue with /etc/gdm/gdm.conf but I have no idea how to fix it.

---

### Post by Gusse on 2007-09-01
Sounds precisely like it was for me, and as my desktop (the one with Ubuntu) is rarely used (esp. in the summertime), I haven't bothered to try anything more. I'd be ecstatic if somebody would cough up something here...

---

### Post by wislon on 2007-09-02
I have not had this problem myself, but have a look on the forum for "Envy", it's a script that helps automate the whole process of driver download and setup for you, it's got some good reviews.

Good luck with it! :)

---

### Post by Gusse on 2007-09-02
Thanks, I'll take a look at it!

---

