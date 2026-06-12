---
title: "NVIDIA driver trouble: Intrepid and Jaunty, NVIDIA Geforce4 MX"
date: 2009-05-04
forum: Multimedia Software
---

### Post by mlejayne on 2009-05-04
Hi, I've been looking all over for a fix for this one, so I sadly can't quite remember what I've tried and what I haven't. 

What happens: In Intrepid, when I boot I have a hand on "Checking battery life..." (I have a desktop) and the screen turns on and off a few times. Afterwards, it says that it couldn't detect something right and wants to go into low graphics mode. Desktop effects don't work, and full screen video is very, very choppy.
In Jaunty, a similar startup issue as above, but with more choppiness and slowness with tasks like scrolling and opening windows. 

I've: 
Downloaded and manually installed driver NVIDIA-Linux-x86-96.43.11-pkg1.run (many, many times.)
Tried Nouveau (I had hella issues with strange screen dimension stuff and I had to click on everything a little above and to the right of where my cursor actually appeared)
Messed with my xorg.conf (I had no idea what I was doing. When I broke stuff I just got a new one and re-installed the driver)
Started and stopped my X server and GNOME during various points of installing the NVIDIA driver.

I want to be able to watch video and play some not-very-graphic-intensive games, and desktop effects would be nice. I'm using intrepid because it is currently functioning better.

As you can see, I have very little knowledge of what I'm doing. I have a few logs, but I don't know how to attach them here. 

For starters, this is the error I get in my :O.log:
> (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
5470 5156

And my xorg.conf:

> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


Thank you for helping!

---

### Post by dagoth_pie on 2009-05-04
Hi there, I've spent enough time mucking round to be able to tell you these things, your biggest problem, is that the scripts in the ubuntu repositories don't install old enough drivers to run a GeForce 4 or older GPU with 3d acceleration, so that leaves you with two options, to us the "NV" drivers, which you were probably using by default, or to manually install an Nvidia binary, if you install the binary, then it means you will have to uninstall it whenever you wish to install the kernel updates (or simply don't install the kernel updates. If you're wanting some help specifically with that then I can help, I gave up on a Geforce 4 card, but had to go to a lot of trouble with a Geforce 9 before the 170 drivers were put in the repositories, how far have you gotten with figuring out installing the binaries?

---

### Post by Hyporeal on 2009-05-05
Just today, I downgraded to an old GeForce 3 Ti200 because my current card started failing. In Intrepid, I went through the same stuff at startup, with the display manager insisting that I run in low graphics mode. I spent some time trying to figure out how to get the correct driver installed, and ended up using System|Administration|Hardware Drivers and activating the proprietary driver, which was automatically downloaded and installed. It now works perfectly.

I'm not sure what made it work. I reinstalled the package nvidia-common, which claims to detect your hardware and recommend a driver. I don't know if this is a necessary step or not.

Anyway, I just wanted to share my success story with older Nvidia hardware using the repository. Good luck getting it to work!

---

### Post by ofb on 2009-05-05
Some legacy Nvidia issues are entwined with legacy CPUs.
[http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support](http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support)

It'd be helpful if anyone posting their card success or failure would also post the output for 'cat /proc/cpuinfo'

Just saying 'Duron' isn't enough, because different models of Duron may or may not have SSE.

You can also just do 'cat /proc/cpuinfo | grep sse'  -- Nothing returned means no SSE.

-

FWIW, my Duron sans SSE with GeForce4 MX440SE wouldn't boot a new 8.10 install. Ditto with FX5200. MX440SE is fine on 8.04, but FX5200 cannot do 3D (no GoogleEarth).

I gather our trouble with 8.10 is Nvidia cut off some legacy support in their drivers. I also gather that they've done some work on that since, so I mean to try 9.04 on the weekend.

A big trouble with legacy Nvidia is unless someone has the same card and CPU as you, advice doesn't seem to apply.

---

