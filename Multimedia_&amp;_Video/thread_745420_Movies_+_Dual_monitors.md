---
title: "Movies + Dual monitors"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by markcgriffiths on 2008-04-04
Hi,

I have a laptop, which I have connected to an external monitor.  I am able to use the second monitor to do everything expect play movies.  I have tried with Totem, xine and mplayer.  All of them show only a black screen on the second monitor.  How do I get to play movies on my external monitor?

I can do everything else, even play movies in Google video.  What's gone wrong?

Thanks in advance.

---

### Post by overdrank on 2008-04-04
> **markcgriffiths said:**
> Hi,

I have a laptop, which I have connected to an external monitor.  I am able to use the second monitor to do everything expect play movies.  I have tried with Totem, xine and mplayer.  All of them show only a black screen on the second monitor.  How do I get to play movies on my external monitor?

I can do everything else, even play movies in Google video.  What's gone wrong?

Thanks in advance.

Hi and welcome, what is the model of the graphics card and have you installed all therestricted formats to play videos?

---

### Post by sloggerkhan on 2008-04-04
Google video uses your CPU, whereas those other apps are using a video overlay. My guess is that you have an ati card with older drivers which force you to select one monitor for the video overlay. You should be able to use aticonfig to move the overlay to the other screen.

---

### Post by markcgriffiths on 2008-04-05
Hi,

Yes I've got an ati card.  How do I use that aticonfig to display movies on the external monitor?  I have downloaded all of those codecs.  Playing movies isn't a problem but getting them to be played on the external monitor is.

Thanks again.

---

### Post by markcgriffiths on 2008-04-05
Hi

I've just done this and now my settings are worse, for example I don't have wobbly windows and advanced desktop settings.

Method 1: Install the Driver the Ubuntu Way

This will install the driver that is currently in the repositories. It may be older than the current version from AMD.

sudo apt-get update	
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

sudo aticonfig --initial

and

aticonfig --initial --force brute

deletes my xorg.conf file.

How do I go back to my previous settings, using my old xorg file does not work.  Still I can't use my external monitor.

---

### Post by sloggerkhan on 2008-04-06
wrong way to go there...
Personally, I'd get the latest drivers from amd's website, and then use the --buildpkg ubuntu/gutsy to make deb files.

Then aticonfig intitual --horizontal overlayon=1 or something.
Above command is wrong, but aticonfig --help should show you the right direction.

Also, there are probably tons of tutorials for ati fglrx drivers around.

---

### Post by IsawSp4rks on 2008-04-06
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Complete **Method 2: Install the Catalyst 8.3 Driver Manually**

---

### Post by markcgriffiths on 2008-04-06
Things are getting worse ;)

I just installed this:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

now my screen is very slow.  How do I default back to my original settings?

I have this error too:

mark@mark-laptop:~$ aticonfig  --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-3
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

---

### Post by markcgriffiths on 2008-04-06
another error:

mark@mark-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.0.1

Segmentation fault (core dumped)

---

### Post by markcgriffiths on 2008-04-06
I have a radeon x300, can anyone help.  I can't figure it out, envy doesn't help.

---

