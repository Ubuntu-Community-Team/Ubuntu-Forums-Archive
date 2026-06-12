---
title: "XMMS + OpenGL Visualization + fglrx = Bye bye, Ubuntu!"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by andrebrait on 2007-11-02
I was listening some music, so I decided to try a plugin for XMMS that's an OpenGL visualization.
Oce I enabled it, the system froze, so I reseted and... bye, ubuntu! GRUB was taking more than 1 minute to Start, and Ubuntu wouldn't load even in Safe mode.

Back to M$ Windows :(

---

### Post by BLTicklemonster on 2007-11-02
Well, if or when Windows crashes, are you going to come back?


don't run off, see if you can correct the problem!  My grub will take a while to figure itself out sometimes, you just have to wait. Walk away for a while then come back. And theres a fix somewhere to make grub stop trying to update itself like that.

---

### Post by andrebrait on 2007-11-02
Well... my Windows (XP) never get sooooo bad to the point I can't even start it.
Win98 becomes useless after 3 months and WinME sometimes would give me the BSOD at the first boot try.

Linux always come to a point when I have to format. I never had  Linux distr for more than a week.

I had Linux in two PCs:
AMD Duron 750Mhz
ECS K7SEM (SiS730S)
256MB RAM PC133
20Gb HD

AMD Athlon 64 3200+
ASUS K8V-X SE
1280MB RAM DDR-400
40Gb + 80Gb HD (Linux and Windows) PATA
First I had a GeForce FX 5200 128MB and now an ATi Radeon 9600XT 256MB.

back to the Duron days, Once I installed a Linux distro, LILO would crash itself after 3 or 4 days, giving me the error "99999999999999999999999999999999999999999..."
Tried: Kurumin, Slackware, Mandrake and SuSe. I tried every FileSystem possible... Ok, since that machine was really weird.

In the Athlon 64, first I was facing a problem with the nVidia drivers. No matter what version of nvidia driver I was using, after a few days it would simply crash X, showing me a Black/Grey/White squares on the screen.
Now I have an ATI graphics card. Ok, after passing all the day trying to make fglrx driver work, not giving me the BSOD (in this case, the Blank Screen Of Death), I simply started a damn visualization and it frozen my system. Ok, I though... So... All my work is lost! I could access the ReiserFS partition from windows and grab the files I needed, but I gave up...

Tried: Slackware (wouldn't even boot) Mandriva 2007 (unstable) Ubuntu 7.04 and 7.10...

There's a lot of work ahead. Linux is heading the right way, but there's still a lot f work.
Mainly in the "User Friendly" section.

A great addition on Ubuntu 7.10 is the possibility to generate de Monitor data to x.org from a Windows  monitor driver. This is a big advance. But I couldn't get video to work until I removed it and other stuff from xorg.conf, but it seems to be ATI's problem.

I think I'll try 7.04 again.

---

### Post by andrebrait on 2007-11-02
But this will be the last Try before Ubuntu 8.04.

---

### Post by eye208 on 2007-11-02
> **andrebrait said:**
> I could access the ReiserFS partition from windows and grab the files I needed, but I gave up...
Next time you install Linux, don't use ReiserFS.

ReiserFS has a long track record of becoming corrupt in various ways when the system is not shut down properly. See [http://en.wikipedia.org/wiki/Reiserfs#Criticism](http://en.wikipedia.org/wiki/Reiserfs#Criticism) for more info.

ext3 will not prevent fglrx from crashing or locking up, but it will at least make sure the system will be up and running after resetting the computer. This is why ext3 has become the default file system of all major distributions. (Even SuSE dropped ReiserFS as its default option some time ago.)

---

