---
title: "weird behaviour of external samsung tv"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by esagherardo on 2008-01-06
I have a HP Pavillion dv4000 laptop, and a Samsung LCD tv LE26R5.
The tv has a vga port.

I tried to connect the laptop to the tv via the external laptop vga port, and:

1. it works perfetcly well, I can see my desktop duplicated in the TV, which acts as a perfect monitor, but...

2. when I start mplayer, the mplayer window pops up: on the laptop screen, it shows the movie.. on the tv screen, it is blue! The desktop below the mplayer window still is visible, but the content of the window is plain homogeneous blue.

Any clue? 

Thanks in advance.

-------------------------------

Some infos:

laptop bought in Switzerland, TV in Italy.

lspci gives:

```
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
```

Xorg -version ouputs:

```
$ Xorg -version

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux dirac 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 29 September 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present

```

My xorg.conf reads... uh, there's no xorg.conf anywhere...

```

$slocate xorg.conf
/var/lib/x11/xorg.conf.md5sum
/var/lib/x11/xorg.conf.roster
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/xresprobe/xorg.conf
/usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablectrlaltbackspacegnome
/usr/share/ubuntu-docs/ubuntu/sample/xorg.conf_disablenvidialogo
/usr/share/displayconfig-gtk/xorg.conf.fallback
gherardo@dirac:~$ 

```

---

