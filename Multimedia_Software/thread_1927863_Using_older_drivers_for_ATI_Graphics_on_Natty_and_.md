---
title: "Using older drivers for ATI Graphics on Natty and newer"
date: 2012-02-18
forum: Multimedia Software
---

### Post by njrob on 2012-02-18
Hi,
I'm trying to run a game called Dungeons & Dragons Online using Wine, but the launcher requires OpenGL support.  I just need to know what I can use as a proprietary driver and what I can't, and finally, where to find them free for easy download.  My system and software specs are listed briefly below.

Dell Latitude D810
Windows XP (host OS)
Ubuntu 11.10  (installed using Wubi)
Wine 1.3.37
ATI MOBILITY RADEON X 600 graphics card, (now apparently under the "legacy" support category, according to this thread).

Please let me know if you can point me towards some stable linux compatible drivers that will provide OpenGL support.

Notice:  I have installed the packages for the "Radeon" or "mesa" drivers, but can't make head nor tail of the configuration; I'm not so good with programming or numbers in general, so any hints/tips on how to configure this mesa software into a working state would be much appreciated.

Thank you for your time and patience.

---

### Post by njrob on 2012-02-18
I was able to find this script for finding out what my graphics settings were.


neal@ubuntu:~$ cat /proc/pci | grep VGA || lspci | grep VGA | colrm 1 4 ; cat /proc/cpuinfo | \
> egrep "model name|MHz" ; xdpyinfo | egrep "version:|dimensions|depth of" ; glxinfo | \
> egrep -A2 "direct rendering|OpenGL vendor" ; uname -sr; vblank_mode=0 \
> glxgears & sleep 30 ; killall glxgears
cat: /proc/pci: No such file or directory
0.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
model name	: Intel(R) Pentium(R) M processor 2.26GHz
cpu MHz		: 2267.000
X.Org version: 1.10.4
  dimensions:    1920x1200 pixels (508x317 millimeters)
  depth of root window:    24 planes
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
Linux 3.0.0-16-generic
[1] 6057
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12



If anyone can help me either a) figure out what to make of all this and what I need to do next, or, b) explain why I keep getting syntax errors for putting these graphics related commands through the terminal even though I should have things installed;  help in either of these two categories would be very much appreciated.  Thank you.

---

### Post by njrob on 2012-02-18
I guess I might not have been exactly clear in my questions earlier, so I'll try to restate them more to the point in light of this thread.

I am trying to install drivers for my old ATI graphics card on my Ubuntu 11.10 so that I have full OpenGL/3D graphics support.

One of my main questions is whether ATI graphics cards MUST be equipped with ATI drivers, or if there are drivers that can be used instead even though they are not specifically for ATI graphics hardware.  I'm not all that tech savvy when it comes to drivers and related graphics technology.  All I can be sure of right now is that my OpenGL grasphics aren't working using the current "default" Ubuntu driver, which apparently no longer supports my old ATI Radeon Mobility X600 graphics card.

I tried installing some graphics drivers from here: "ppa:oibaf/graphics-drivers" but I couldn't figure out how to actually use any of the drivers installed since it is all done in the terminal, which is something I have only limited skill using.  Installing "Driconf" from the Software Center didn't seem to help at all, since neither the device nor the drivers appeared in the configuration options.

I have also considered using the Ubuntu opensource "Radeon" drivers, but I'm not all that skilled in translating terminal errors, or knowing what I'm supposed to be doing at the command line level, (like I said before, not my forte).  Does anybody have info on how to install the opensource Radeon drivers?

Sorry, I said this was meant to be more to the point, and here I am making a longer post than before!  I hope this was a bit more focused and relevant to the topic than giving my entire issue.  Graphics with an Old unsupported video card is enough of a hassle by itself!

Valete Socii!
-njrob-

---

### Post by njrob on 2012-02-18
> **njrob said:**
> All I can be sure of right now is that my OpenGL grasphics aren't working using the current "default" Ubuntu driver, which apparently no longer supports my old ATI Radeon Mobility X600 graphics card.

By this I meant that my current driver did not support OpenGL in particular; everything else looks great with the graphics I've got, but I need the OpenGL support from a new driver to let me run my favorite game.  It's not that my current driver doesn't work, it's that it doesn't support all of the features my graphics card possesses.

---

### Post by overdrank on 2012-02-18
Hi and welcome, I have moved your posts to your own thread so not to highjack the other thread.
:)

---

### Post by Jeek Elemental on 2012-02-19
I don't have a solution for you but can try and clear up the problem some.

For your card theres 2 choices of drivers;
Radeon (open source, opengl support but not complete)
old fglrx (proprietary with full opengl support)

From amd webpage:
"
All future ATI Catalyst™ releases made available past the ATI Catalyst™ 9.3 release will not include support for the legacy products listed above or any of the features associated with those legacy products.

AMD may periodically provide Windows XP and Windows Vista driver updates (for the products listed above) for critical fixes only.  No new features will be provided in future driver updates.  The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above.
"

So your options are:
-Use an old ubuntu version with an x.org that supports fglrx 9.3 (you can NOT install 9.3 on current ubuntu), and "freeze" it in time, not updating x.org.

I think ubuntu 9.04 is the latest version you could use then, however it probably means you have to compile wine yourself.

Its a lot of work and no guarantees it will let you run ddo.

-Use the latest beta of Radeon driver ([https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa))
No idea if that will let you run ddo, and it is complicated stuff to manage (read very carefully the page before trying anything).

-Wait until stable Radeon has enough support to run ddo, it may not be far off...Many games already work in wine with it.

Also, post the output from glxinfo, maybe radeon driver is not correctly installed.

---

