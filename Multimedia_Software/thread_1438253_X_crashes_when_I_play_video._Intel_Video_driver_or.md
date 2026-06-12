---
title: "X crashes when I play video. Intel Video driver or card issue?"
date: 2010-03-24
forum: Multimedia Software
---

### Post by gaspros on 2010-03-24
Hi there, I am very new to Linux - Experienced on Windows
Two days ago I had a 5 hour marathon session trying to sort this issue out. Nothing seems to have worked.

My specs are as follows:
Intel  Pentium Dual Core E6500 CPU, 2.93 GHz, FSB 1066MHz, Socket   LGA775
ASRock  G41C-VS M/board - Intel G41+ICH7, COMBO DDR2+DDR3, 1333 MHz FSB,  PCIE,  int VGA, SATAII, 5.1Ch
2GB  DDR3 PC-10600 (1333MHz)
500GB Hitachi 7200rpm PATA HD

I have loaded 9.04 Jaunty linux kernal 2.6.28-11 generic Gnome 2.26.1

When I play a video though VLC or movie player after a short time the x server interface crashes. 
Other people in the forums (here: [http://ubuntuforums.org/showthread.php?t=1436004](http://ubuntuforums.org/showthread.php?t=1436004)) have said it could either be this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350306](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350306)
or a bad video card (Although mine is onboard the motherboard) and I have no spare video cards to test it with.

I am happy at this time to stay on 9.04 so can somebody help me with the video card issue.

Thanks

---

### Post by gaspros on 2010-03-25
I have spent further hours searching the forums and trying different things on the computer.
I always seem to get stuck somewhere and just do not have the experience to get through the glitch.
For instance I am trying to upgrade to the latest X.org drivers so I add the PPA but can't for the life of me add the key. I keep getting keyserver time out. Is there some other server oiut there that has the keys I need?
So I am thinking upgrade to 9.10 as its X.org might be newer but last time I tried the system would not boot at all and just threwup a bunch of codes. I tried booting with a livecd of 9.10 and it stops right at the beginning with a bunch of trace codes.
So can somebody please help.
I am almost certain that I have a fairly simple driver problem that many other people with my spec would also have and the solution is out there but I may as well try to touch the moon at this stage.
Help would be greatly appreciated. Thanks.

---

### Post by gaspros on 2010-03-28
X stopped crashing once I was able to load the intel video driver in Karmic. So this problem was solved.

---

