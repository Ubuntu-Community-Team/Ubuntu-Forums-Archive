---
title: "Desperate for normal DVD performance"
date: 2008-06-29
forum: Multimedia Software
---

### Post by James_the_dude on 2008-06-29
So here's my problem:

I cannot have acceptable quality DVD playback and use the fglrx ATI driver in order to enjoy desktop effects at the same time.

I know there are a number of threads about the problem, as I have been trying to understand it for a couple of weeks now; ubuntu (and other linux distros) users experience choppy, pixelated, jumpy DVD playback when they have the proprietary driver installed so as to enjoy certain desktop effects.

A number of people have suggested solutions to this issue. I have tried every solution I come across:
*Disabling desktop effects* - improves nothing so long as the system is still using fglrx
*Trying different media players* - no difference in quality
*Selecting "X window system (no Xv)" in the multimedia systems selector* - no improvement
... and some others I don't remember off the top of my head
Basically  I've messed around a lot, butchered my xorg.conf file (among other things) numerous times; reinstalled ubuntu numerous times and tried a couple other systems (OpenSolaris, Fedora, Kubuntu, FreeBSD).

It would seem that this problem really cannot be fixed on the consumer end. The way I see it, something is inherently wrong with fglrx and there is nothing I can do about it except hope that ATI will fix it.

Flashy 3d effects are not really that important to me, but there are certain effects which I have actually found quite useful, such as having actual transparency on my command prompt window: something which does not work without fglrx.

So here are the options I am considering:

1. Have a very small partition on my disk (maybe containing Xubuntu or DSL) in which the installed linux variant uses only free graphics drivers... no effects, but media will look fine.

2. Wait and hope that fglrx is fixed. (anyone know anything about current development?)

3. Experiment with some more free operating systems... maybe I'll get lucky.

4. Try an older version of ubuntu?

I have an ATI Radeon Xpress 1150 (also known as 200M) card, if that helps.

Does anyone have any thoughts or advice on this matter? Anyone know of a linux variant which is not effected by this poor DVD playback problem?

---

### Post by James_the_dude on 2008-07-12
I don't know if this is considered "necroposting" at this point, but I have found a solution to my problem, so I figured I'd update this thread just in case it helps anyone.

Up until now I have been using 64-bit ubuntu 8.04 on my laptop. Just today I thought "maybe using 32-bit ubuntu will make a difference in video quality." So I installed 32-bit ubuntu 8.04 and I used the system>administration>Hardware Drivers to enable ATI's proprietary driver.

There was definitely  a difference in DVD quality. Mainly, the video did not jump, or become vertically desynchronized: it was no longer "choppy". This was a huge improvement, however DVDs were still uncomfortably pixelated.

At this point I thought "okay, for some reason things work differently in 32-bit linux, so maybe I'll give the *newest* driver a shot again via Envy, and maybe that will fix the pixelation issue with DVDs." According to my research ubuntu's repositories do not include the newest fglrx driver. I also learned that a program called Envy is designed to install the most recent ATI or nVidia drivers on Debian based linux.

Now, when I tried Envy in 64-bit ubuntu it did not work at all, it only broke things. This is to say that my screen would be white upon restart after envy installed fglrx: only the mouse was visible (for me this is the effect any newer-than-ubuntu-repository-listed fglrx driver had no matter how I installed it).

With the above 64-bit disaster mentioned, I did not have much hope when trying Envy in 32-bit ubuntu, but I figured "hey it's worth a try."

It worked great! No more vertical desynchronization, choppiness, no more pixelation or white screens of death or "ubuntu has been started in safe graphics mode". DVDs looked like... well, DVDs!

So, if your having trouble with your video driver in 64-bit ubuntu, just try it out in 32-bit ubuntu, things may improve.

---

### Post by sdowney717 on 2008-07-12
so what version did Envy install?
I think the latest is 8.6?
I think I have 8.4

---

### Post by James_the_dude on 2008-07-13
I think envy installed 8.4.

Everything worked great. fglrxinfo returned the correct info about my card, and said nothing about "mesa" - which I perceive is good.

I'm sad to say that envy only succeeded in instilling false hope. As soon as I updated the system it was back to white screens on login. While trying to figure things out in "failsafe gnome" fglrxinfo returned that "mesa" was doing stuff - which I think is a part (or symptom) of this problem. When the system updates after a clean install there are ~230 updates, I have no way of knowing which one ruined this. Does anyone know how or why an update/s did this? Maybe there could still be hope if I just knew which update ruined everything, so that I could avoid it.

---

### Post by sdowney717 on 2008-07-13
after you get this white screen from doing all the updates.
Have you tried redoing the Envy fglrx driver?
You can get to a command prompt from boot
Once there you can run ENVY in terminal mode
It will redo the driver, xorg, etc... all from the command prompt screen.
I think it is envy -t for text mode.

[http://www.linuxjournal.com/article/9792](http://www.linuxjournal.com/article/9792)

scroll down to read about this

Xorg.conf has gotten very simple wiith these ati drivers
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

---

### Post by James_the_dude on 2008-07-19
Yes, I did try re-envying after updating; it fixed nothing.

(sorry my responses are a week late at times, I don't have my own internet connection)

I am now using xubuntu x86_64, and EnvyNG installed fglrx v8-6. So far things are _not_ *not* _working_ right (my newfound superstition tells me that if I post that "everything now w__ks gr__t, there are n_ pr_bl_ms!" a problem will soon haunt me; hence the awkward wording). ;)

If anything worth mentioning comes up I will give an update on the status report here.

**STATUS REPORT UPDATE:**

So after updating in xubuntu fglrxinfo indicated indirect rendering by mesa. So I used envy to uninstall and then reinstall fglrx. Now fglrxinfo does not mention mesa, which is good. However, fglrxinfo does mention a "segmentation fault." Should I be concerned?

> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7659 Release

Segmentation fault


**UPDATE: UPDATE**

Another little annoyance: fglrx-control-envy, the graphical control panel for ati cards, also known as "ATI Catalyst Control Center" is nowhere to be found in my applications menu, even though synaptics lists it as being installed, and I have hit "reinstall" a couple times now.

How can I open it?/ how can I make it visible in my applications menu?

---

