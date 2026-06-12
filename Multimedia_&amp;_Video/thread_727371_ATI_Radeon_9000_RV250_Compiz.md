---
title: "ATI Radeon 9000 RV250 Compiz"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by ejl6266 on 2008-03-17
I have been searching these board for some time now trying to find a way to install compiz and get it to work on my computer which runs Gutsy with a Radeon 9000 RV250 graphics card.  I tried to remove the proprietary driver and install the open source one but I couldn't get it to work.  When I try to enable desktop effects it just says desktop effects cannot be enabled.  I tried to follow another guide but when I did what it said to edit my xorg.conf file my xserver stopped working completely.  I fixed it by running sudo dpkg-reconfigure -phigh xserver-xorg.

When I run the command glxinfo | grep vendor the output is
server glx vendor string:  SGI
client glx vendor string:  SGI
OpenGL vendor string: Tungsten Graphics, Inc.

The command glxinfo | grep "direct rendering" outputs
direct rendering: Yes

So I guess this means that I have 3d support enabled which is good since I want to have 3d Desktop effects.  Right now my xorg.conf file is completely unmodified so I am looking for help on how to alter it.  I have a problem with programs now where there menu bar seems to integrate into the Ubuntu top menu bar and I cant drag or switch between windows using the mouse.  Basically I am looking for some help on how to use compiz or beryl because everything I try to do doesn't work.  Thanks for any help and let me know if you need any more information from me.

---

### Post by larryfroot on 2008-03-20
Hi, 

This is going to be a bit of a journey as there is an excellent thread, one in which the final solution evolves through several peoples input. Firstly please be aware that enabling compiz with the radeon fireGL 9000 will KO video output, but this is easily rectified (in vlc at least) by going into preferences, ticking the advance options box in the lower right hand corner and clicking 'output modules in the video section. This brings up a single drop down box. You may have to maximise the window in order to see it. Selecting X11 from the selection will sort that particular problem out. 

Also I found that the various hacks of xorg.conf that were on display pretty much worked to one degree or other (some much more than others) but please be aware that one of the xorg.conf files on show doesn't. In fact it threw me into vesa mode after logging out and back in again. That is the one on display on page 5 from fedsharp. It may have worked for him, but that is a minor miracle as the ati driver he was using - the officially supported fglrx - is a hinderence than a help when it comes to the radeon 9000. If you have the fglrx driver installed then you are going to have to uninstall it for compiz to be enabled.

The following comes from [http://howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://howtoforge.com/ubuntu_feisty_beryl_ati_radeon")
But please don't bother hacking your xorg.conf according to this tutorial. You are far better served in that department by the thread whose link appears after this section from the howtoforge tutorial. However its deffo the way to go if you do have fglrx installed.
So to get rid of fglrx....

 type

lspci

You should find something like this in the output:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 01)

We want to use AIGLX with open-source ATI driver instead of XGL with the proprietary ATI driver (fglrx). Therefore we have to disable fglrx. First we disable the fglrx kernel module:

sudo modprobe -r fglrx

Then we run

glxinfo | grep vendor

If you see ATI mentioned in the output, then you're still using the wrong driver. If you see SGI instead, everything's fine. On my notebook, the output looked like this:

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

If you have ATI in the output of the previous command, remove the fglrx driver like this (you can do this also if you have SGI in the output - just to go sure):

sudo apt-get remove xorg-driver-fglrx; sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri

Right then...

The driver I have on my laptop running compiz with that radeon 9000 is...

xserver-xorg-video-ati

apt or synaptic, down to you how you get it if its not on your hard drive already. 

So now comes the hacking of  /etc/X11/xorg.conf

As always...take care out there....

The thread I am directing you towards concludes with an xorg.conf file that did the trick for me, and others. Basically it circumvents a number of problems thrown up by various posts in the thread, which are interesting if you have the inclination and or the time. My own working xorg.conf has the addition of "Section DRI" and "Section Extensions" tagged onto the end of the final xorg.conf in the thread...

The relevant parts are...and please remember this is for a laptop!!! So please be carefull when you come to the input devices bit...

> Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"GARTSize" "64"
	Option		"MergedFB" "off"
	Option		"XAANoOffscreenPixmaps" "true"
	
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Virtual 1920 1440
		Modes "1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

Edit your xorg.conf to include the above (and to replace the relevant sections of what was already there) and hopefully it will all work.

The above is the summation of all the wisdom that I have shamelessly lifted from the very intelligent individuals who got it right in the end. If it doesn't work you might have to go into the thread and slowly work your way through each xorg.conf hack to see what works and what doesn't. But please remember a) not to use fedsharps xorg.conf hack - I am sure it must have been an honest mistake and b) if you do work your way through the thread - remember at the end of the day you can start compiz without entering SKIP_CHECKS=yes compiz into a terminal  or a file. You will also not be restricted to 16 million colours instead of the 24 million that is your god-given right to have. And you will be able to use video playback as well. 

It has amazed me how much life linux can squeeze out of an ageing 32 meg graphics card...it beats vista hands down. Simply amazing. Anyways the thread in question is....

[//http://untuforums.org/showthread.php?t=550082]("http://ubuntuforums.org/showthread.php?t=550082")

I hope it goes well for you.

---

### Post by martinlall on 2008-04-10
Unfortunately this doesn't work in new Ubuntu 8.04. Anybody knows how to get it work? Have tried all, including this tutorial but no success.

My video card is also ATI Radeon 9000 RV250 or Mobility Radeon 9000 32mb (depends, from what source i'm using to see it's info). Anyway, this doesn't matter. 

Thank you,
Martin

---

### Post by warp99 on 2008-04-10
> **martinlall said:**
> Unfortunately this doesn't work in new Ubuntu 8.04. Anybody knows how to get it work? Have tried all, including this tutorial but no success.

My video card is also ATI Radeon 9000 RV250 or Mobility Radeon 9000 32mb (depends, from what source i'm using to see it's info). Anyway, this doesn't matter. 

Thank you,
Martin

First we need to install the hardware rendering mesa drivers and remove the software ones that are installed on you computer so open a terminal and enter the following:

```
sudo apt-get remove --purge libgl1-mesa-swx11 libgl1-mesa-swrast libgl1-mesa-glx+ libglu1-mesa+
```

once that is done you should set your card to use the open drivers since your card should work with Compiz:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

choose 'ati' as your driver. If that does not work then we need to install the restricted drivers packages:

```
sudo apt-get install --reinstall xorg-driver-fglrx fglrx-control linux-restricted-modules && sudo depmod -a

```

then:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and choose 'fglrx' as your driver.

Edit:
Remember to reload xserver, crtl+alt+backspace, when changing drivers.

---

### Post by martinlall on 2008-04-11
> **warp99 said:**
> First we need to install the hardware rendering mesa drivers and remove the software ones that are installed on you computer so open a terminal and enter the following:

```
sudo apt-get remove --purge libgl1-mesa-swx11 libgl1-mesa-swrast libgl1-mesa-glx+ libglu1-mesa+
```

once that is done you should set your card to use the open drivers since your card should work with Compiz:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

choose 'ati' as your driver. If that does not work then we need to install the restricted drivers packages:

```
sudo apt-get install --reinstall xorg-driver-fglrx fglrx-control linux-restricted-modules && sudo depmod -a

```

then:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and choose 'fglrx' as your driver.

Edit:
Remember to reload xserver, crtl+alt+backspace, when changing drivers.


Actually, I cannot choose fglrx driver. What I m doing wrong?

---

### Post by larryfroot on 2008-04-23
hi....in my experience, for the radeon 9000 the fglrx driver sucks.Whenever I have installed it and removed xserver-xorg-video-ati my installation falls back onto the vesa driver. You can make the change between the two in synaptic...fglrx and xserver will do as search terms. 

And I am currently in the dark re compiz and the radeon 9000 say in this old dell laptop. I think I may have a lead. If it gets fruitful I will pass it on. Some guy on launchpad said he got his to work, but didn't say how...I'm going to try and trace him though the forums, or at least look at other threads on the subject.

---

### Post by larryfroot on 2008-04-23
hi again...this is a copy of a post I made elsewhere re old radeon cards and compiz. Hope it helps you.

 hello chaps. I have a radeon 9000 running with the xserver-xorg-video-ati driver with an xorg,conf generated from a

sudo dpkg-reconfigure -phigh xserver-xorg

command while running under the ati driver.Be sure to do the reconfigure only whilst using the ati driver. The fglrx driver has proved to be useless for me.

Then I simply typed

SKIP_CHECKS=yes compiz

into a terminal window and watched my desktop do the now I'm here, now I'm not thing for a minute or so. Then it reappeared with compiz enabled. I'm just about to add the skip-checks thingy to the system > preferences > session manager so compiz can skip the checks on every startup. And yes I am on hardy. Hope this helps someone before they start having dreams about xorg,b****y.conf and being naked in the library. I think there's a bug in /usr/bin/compiz that fails to register xgl on its checks for 3d capability with older ati cards.
__________________
Many a mickle muches a markle

---

### Post by larryfroot on 2008-04-24
Would you beieve it, I logged out and shutdown, and when I logged back in this morning, no SKIP_CHECKS=yes compiz had been run from the services manager. Moreover, when I typed it into a terminal, compiz knocked out quarter of my display. So I changed my xorg.conf (only the relevant sections of my xorg.conf are shown here) to:

> 
Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option "XAANoOffscreenPixmaps"
	Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
	Option		"GARTSize" "64"
	Option		"MergedFB" "off"
	
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Virtual 1920 1440         
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Option "AIGLX" "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection


After that I typed the SKIP_CHECKS=yes compiz into a terminal window, and everythings back to normal again. That is, compiz is working nicely.

The one thing in all of that which seems the most relevant is the virtual display value of 1920 1440 which re-aligns the offset that compiz spits out. there are other bits n' bobs in the whole deal that you might like to try if you haven't a radeon 9000...enabling compositing and
Option "XAANoOffscreenPixmaps"
Option "DisableGLXRootClipping" "true" 
are pretty central. 

Hope this works for you all.

---

### Post by unskold on 2008-05-03
hello, I am also having the same problem can not run compiz without making the command **SKIP_CHECKS = yes**
[B]When type glxinfo | grep vendor I see output:
glx server vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.[/B]
I have xorg like this:
> # Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "pt"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection

Section "Device"
Identifier "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
Driver "ati"
BusID "PCI:1:0:0"
Option "XAANoOffscreenPixmaps"
Option "DisableGLXRootClipping" "true"
Option "AddARGBGLXVisuals" "true"
Option "AllowGLXWithComposite" "true"
Option "EnablePageFlip" "true"
Option "GARTSize" "64"
Option "MergedFB" "off"

EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Virtual 1920 1440
Modes "1400x1050"
EndSubSection
EndSection

Section "ServerLayout"
Option "AIGLX" "true"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

my graphics is: 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01) and im using ubuntu 8.04


	
when tried to do this, my keyboard was in another language. can help me back in by the Portuguese?
Thanks in advance

---

### Post by Mguel on 2008-05-10
Has anyone managed to enable tv-out with the radeon 9000 rv250 on hardy?

Sorry for posting sort of off-topic, but I haven't found a solution for this issue and there aren't much threads nor other info I can find with google neither.

I've tried with xorg driver, with fglrx through repos, and Envy... and lots of settings. I would be glad to sacrifice compiz to have the tv-out working.

I'm close to go back to kubuntu gutsy (there I could have tv-out with a geforce2 mx400, which by the way couldn't make it to display a tv-out image on hardy neither).

Cheers,
Mguel

---

### Post by JFire on 2008-06-13
Heya, I haven't bothered reading through the whole thread so forgive me if someone's already mentioned this.

The following solution worked for me. (just copy and paste the following into your terminal)

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

You can find the original post here: [https://bugs.launchpad.net/ubuntu/+bug/193702](https://bugs.launchpad.net/ubuntu/+bug/193702)

HTH

---

### Post by indiecast on 2008-06-25
OMG this is the best thread!


i just simply put that line in a terminal and it worked.

i remember seeing something about a month ago that compiz blacklisted ati radeon cards for some reason, and that the black list file had to be edited.

i have a feeling ship checks forces compiz to ignore the blaklist and successfully.

IM SO HAPPY THIS WORKS. i had it working in 6.10 but when i upgraded it wouldnt.  its so great that this semi-powerful card can now be put to good use!

off to download awn so i can mac-itize my compy


thanks ubunut community

---

### Post by Caseyjp on 2008-06-26
This thread for compaq x1000 users SHOULD BE F'in stickied!  Finally, my old compaq has life again beyond the 2d stuff.  The following two bits need to be done from a default install (8.04) to get things working:

In xorg.conf:
SubSection "Display"
Depth 24
Virtual 1920 1440
Modes "1400x1050"
EndSubSection

And then from a terminal, run this command.

 -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

Restart, select extra effects from system > appearance > visual effects tab.

Download via syaptic or apt-get install compizconfig-settings-manager  and away ya go.

Thanks you guys.

Oh and one fyi........the new opensuse 11.0 picks up the rv250 card and settings automatically.  I still prefer ubuntu, but from a compiz perspective, suse is waaaay ahead as far as autodetection of lcd screen and settings.

---

