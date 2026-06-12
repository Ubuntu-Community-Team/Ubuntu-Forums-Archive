---
title: "Installation of nv driver under Xubuntu 12.04"
date: 2012-06-23
forum: Multimedia Software
---

### Post by Easy Tiger on 2012-06-23
Hello,
I try to install Xubuntu on my old PC. The thing is it has an old graphic card: Nvidia GeForce 2 Ti. Nvidia doesn't provide closed driver for some time, so I had to use open driver.

Sadly, nouveau driver isn't working properly- white dots appear on a screen, so I've installed nv driver according to this post: [http://ubuntuforums.org/showpost.php?p=11493049&postcount=27](http://ubuntuforums.org/showpost.php?p=11493049&postcount=27). Then I entered console by Ctrl + Alt + F1 and I ran commands:

etc/init.d/lightdm stop
cd /etc/X11
Xorg -configure

Later I copied file /root/xorg.conf.new to /etc/X11/xorg.conf and I edited it to use nv driver instead of nouveau.

Sadly I still can't run nv driver even if I blacklist nouveau driver in /etc/modprobe.d/blacklist.conf.

Can anyone tell me what I should do to run nv driver or to make nouveau work properly without white dots appearing on screen?

---

### Post by U202E on 2012-06-23
you could play around with the screen resolution, maybe that will help.

another idea: if you install an old version of windows (95 or so) and kernelEx, then you are able to install virtualbox (OSE) on your pc. (I don't think this is the best idea)

---

### Post by Easy Tiger on 2012-06-23
Well I don't think these white dots are connected with resolution, but I know that nv driver works well.

As to virtualization- it's not a solution because I have low specs on this PC and I don't want any "mess" on it- only Xubuntu without dual boot or running Windows under Linux. Otherwise I would simply install Windows XP but I don't want to.

---

### Post by Yellow Pasque on 2012-06-23
Nvidia killed the nv driver a while ago. I doubt it works with modern kernels/X: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/902636](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nv/+bug/902636)

---

### Post by Easy Tiger on 2012-06-23
Yes, I know that nv driver is not supported anymore, but if you'll look at this thread:
[http://brainstorm.ubuntu.com/idea/29668/](http://brainstorm.ubuntu.com/idea/29668/)
you'll see that it is possible to run it on ubuntu 12.04. User 'pmllr' compilled it manually from source, but I found an easier way, from link to which I refer in my earlier post.

---

