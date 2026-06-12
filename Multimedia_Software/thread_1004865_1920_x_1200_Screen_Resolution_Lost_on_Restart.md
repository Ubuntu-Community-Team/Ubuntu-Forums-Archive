---
title: "1920 x 1200 Screen Resolution Lost on Restart"
date: 2008-12-07
forum: Multimedia Software
---

### Post by Bill Wood on 2008-12-07
First, I am a newbie to Ubuntu Linux. I just started teaching myself Linux in the hope of being able to get rid of my Windows based server.

I am running Ubuntu 8.04 on a Dell Optiplex GX270 with an Intel 82865G graphics cards and a Viewsonic VX2835wm monitor (with 1920 x 1200 resolution). The Optiplex uses the Windows dual boot which was configured by Ubuntu as part of the Ubuntu installation; the computer also runs Windows XP. Ubuntu is now the default OS on boot up.

When I first downloaded and installed Ubuntu Linux a month or so ago, it immediately and correctly configured my monitor resolution to use the full 1920 x 1200 screen resolution of my monitor. Yesterday, in the midst of an office move, I restarted my Optiplex with the HDMI cable removed. No big deal until I restarted the computer with the cable attached and found myself staring at a 640 x 480 resolution screen.

When this happened I knew nothing about either the "Screens and Graphics" menu or the xorg.conf files. In the 24 hours since then, I have learned more than I wanted to know about this menu and these files. I have been able to restore partial functionality to my monitor by getting the resolution up to 1024 x 768 by selecting the Intel 865 (i810 Integrated Graphics) driver and the generic 1920 x 1200 display monitor. (Also, I am quite sure that there is no hardware problem since the monitor still functions fine when I boot into Windows XP instead of Ubuntu.)

I don't have a back up of whatever the xorg.conf file looked like before this all started happening and I would like to avoid having to learn how to program the xorg.conf file (I have made some attempts that failed miserably). I am hoping / assuming that since the screen resolution was configured effortlessly (and correctly) on the initial install, there may be a simple way to restore my prior settings. Alternatively, is there a way to add additional monitors to the menu on the "Screens and Graphics" menu? If so, is there a way to find out what Ubuntu driver support there is for my Viewsonic monitor? (I couldn't find anything at the Viewsonic web site and none of the Viewsonic drivers listed which I tried seemed to work.)

---

### Post by Bill Wood on 2008-12-20
Two weeks and over 50 hours later I have fixed the video resolution problem, although the solution is not especially satisfying.

Suffice it to say that after a week of trying to get the monitor to work in 1920 x 1200 mode (indeed, anything better than 1024 x 768), I formatted my harddrive, reinstalled Windows from scratch and then reinstalled Ubuntu 8.04. When that didn't work, I downloaded new copies of 8.04 and 8.10 and tried installing them. When that didn't work, I reformatted the harddrive and started from scratch again. That didn't work either.

What did work was buying and installing an nVidia EVGA e-GeForce 6200 PCI graphics card to replace the utterly lame Intel 82865g that had come with my Optiplex GX270. The Comprehensive Ubuntu Hardware Database was very useful in guiding me to my decision to buy the GeForce 6200 video card; see:

[http://ubuntuhcl.org/browse/search/](http://ubuntuhcl.org/browse/search/)

Also the NewEgg site had some very helpful guidance for how to install this card on an older Windows machine like my GX270; see:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130289](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130289)

So I am ready to start again, pretty much from scratch. I lost most of my earlier Ubuntu installation when I reformatted my harddrive the first time. In addition, I remain completely clueless as to how it was that Ubuntu 8.04 recognized that Intel 82865g video card on my original installation and configured my Optiplex for 1920 x 1200 resolution. It was some strange and weird fluke since it never happened again on any of the half dozen or more subsequent installs which I tried. In any event, the real answer is don't use the 82865g with Ubuntu 8.04 or higher; it simply isn't reliable.

---

