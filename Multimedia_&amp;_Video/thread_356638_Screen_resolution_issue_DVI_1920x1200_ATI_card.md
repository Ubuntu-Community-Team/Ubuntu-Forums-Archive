---
title: "Screen resolution issue DVI 1920x1200 ATI card"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by Arthur75 on 2007-02-08
Hello there, I'm a complete newbie here and to linux also ! (but not to unix in general although far from being an expert)

So I just installed Ubuntu, first I could not install it with the live cd as I have a dell 24" so 1920x1200, but it would always stick to 640x480 or something so I could not reach the button of the install application ....

So I put the screen in VGA, there I could go up to 1024x768 but that's all !

Now I'm back on DVI on the full hard disk installation and still 1024x768 maximum, my video card is a small thing ATI 9200 or something.

How can I set up the screen resolution to 1920x1200 ??:confused:

---

### Post by forrestgump on 2007-02-08
[http://ubuntuforums.org/showthread.php?p=2113867](http://ubuntuforums.org/showthread.php?p=2113867)

worked a charm for me

---

### Post by Arthur75 on 2007-02-08
Ok I will try that thanks

---

### Post by Arthur75 on 2007-02-08
I tried the guide for ATI drivers :

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a)


and now I'm completely stucked : blank screen , only console in recovery mode .....

---

### Post by Arthur75 on 2007-02-09
I guess I just have to reinstall everything and try the second method ....

---

### Post by Arthur75 on 2007-02-09
Ok I'm a bit desperate here .... (just installed ubuntu 4 times or something ...)

I tried the second method of this guide :

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

It didn't work, at the create deb package step, ie following this command :

sh ati-driver-installer-8.33.6-x86.x86_64.run --buildpkg Ubuntu/edgy

I got the error :

line 176 : dpkg-architecture : not found

so to make sure everything was clean I reinstalled ubuntu again to try first method

there it worked (in VGA because in DVI I cannot install the system cannot reach the buttons)

but max resolution is 1600x1200 for my dell 24 at 1920x1200 and it looks ugly.

Plus in DVI it does not work !!!  :confused: 

Wanted to install linux for developing something in scheme, I might just drop the idea I guess, or buy another video card ? Use another installation ?

Does these ATI drivers issue on current linux exist with all distribution ?

here is the current output of fglrxinfo :

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

my card is a 9200 se I think

as I don't play games I don't care that much about the card power, but I care about a fanless one and a nice looking screen ie 1:1 pixel mapping in DVI, what would be a card that would for sure work on Edgy ?

---

### Post by Antec2 on 2007-12-31
you need to download fglrx, the ati driver for ubuntu. Go to ubuntu wiki and they have a nice tutorial on installing the driver for your card and the ATI Catalyst center. When you do go to the wiki page, make sure you follow method 2, worked for me.... after 5 hours of trial and error. That's the best way to learn ubuntu... this is my 3rd day with it and so far so good.

---

