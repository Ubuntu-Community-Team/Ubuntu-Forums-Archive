---
title: "Help with Radeon Catalyst drivers please"
date: 2011-09-12
forum: Multimedia Software
---

### Post by mr_si on 2011-09-12
There's all sorts of guides on the net... yet I'm struggling.

eg from [Ubuntu_Maverick_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide")

I've got as far as 
```
$ sudo aticonfig --initial -f
aticonfig: No supported adapters detected
```

and 
```
si@shed:/etc/X11$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 1.4 (2.1 Mesa 7.9-devel)
```

according to the help this suggest the open source driver is in use. 

```
si@shed:/etc/X11$ sudo rmmod radeon
ERROR: Module radeon is in use
```

```
si@shed:/etc/X11$ sudo apt-get remove --purge xserver-xorg-video-radeon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xserver-xorg-video-radeon is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

So what driver am I currently using, how do I remove it so that I can install the proprietary one? 

(Actually not fussed which driver I use as long as I get some hardware accleration)

AGP Radeon 9200 

```
si@shed:/etc/X11$ lspci -nn | grep VGA
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 PRO] [1002:5960] (rev 01)

```

Thanks (once again :-) )

---

### Post by Toz on 2011-09-12
ATi dropped support for the 9200 some time ago. Looks like you're only recourse is to use the open source radeon drivers. See: [http://wiki.cchtml.com/index.php/Hardware]("http://wiki.cchtml.com/index.php/Hardware")

---

