---
title: "Trouble with Ubuntu + Nvidia graphics card.. help!"
date: 2010-12-05
forum: Multimedia Software
---

### Post by Antnee on 2010-12-05
Long story short, the driver that is provided in system/additional drivers makes ubuntu not bootable upon restart.  I have a nVidia Corporation NV41GL [Quadro FX 1400] (rev a2) card... what am I doing wrong?

Also, here is a screenshot of what happens when i try to boot after using these drivers:
[http://i.imgur.com/g53oN.jpg](http://i.imgur.com/g53oN.jpg)

---

### Post by buntunub on 2010-12-05
First, reboot and select Safe Mode boot option. When the menu screen comes up, select the option for the command prompt with or without networking. Then type:

```
#mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then

```
#reboot
```

After the reboot, select the regular kernel that you normally boot on and it should boot up into the open source driver you were using before installing the Nvidia driver. After you log in, you should sift through your /var/log/dmesg, and /var/log/messages and look for the errors. That should give you some hints as to what went wrong, and google searches based on your findings.

BTW, there are known issues with certain laptop onboard Nvidia cards, and no real solutions for those problems have yet been found, although the Nouveau drivers work on them flawlessly (with no 3D). Nvidia needs to release a Linux driver for this, and so far even the latest beta driver does not work.

---

### Post by Antnee on 2010-12-05
I did that, but I am clueless as to what to do with this information.  All I see is a bunch of code that I really don't know what to do with!

Also, the Noveau drivers work fine, but not in 3d apps like Second Life.  So, am I basically out of luck?

---

