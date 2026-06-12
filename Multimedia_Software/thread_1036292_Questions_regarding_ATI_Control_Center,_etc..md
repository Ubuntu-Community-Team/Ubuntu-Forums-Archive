---
title: "Questions regarding ATI Control Center, etc."
date: 2009-01-10
forum: Multimedia Software
---

### Post by xeddog on 2009-01-10
Hi everyone.

I have been having a devil of a time with my Ubuntu Intrepid system for the last couple of days.  In particular, getting the dual displays to function the way I want them to.  I started out by removing the disk drive from a computer that had an nVidia graphics card with a single monitor and put it into a similar machine that had an ATI Radeon 9600 AGP card in it and two monitors.  

Installing the drivers was easy enough.  When I booted the system it just went into low graphics mode and then came up.  I had the driver notification in the top panel and just installed the ATI driver from there.  Badabing Badaboom.

Then I got adventureous and started playing with dual monitors.  The Radeon 9600 can drive two monitors so I think that is called a dual head graphics card in Linux terms.

I did a lot of reading and based on that I went to the AMD website and downloaded/installed their latest drivers.  With either set of drivers (from the distros and from AMD) there isn't a whole lot of difference as far as I can tell.

What my goal is, is to have a separate desktop on each monitor.  That means each will load a wallpaper in it's own space, and each will have it's own desktop (I think that is the correct term).

It sounds like I want to utilize Xinerama, and that is where my troubles have led me.  I have made mincemeat outta my xorg.conf so I don't think it would be very productive to include a copy of it in this post.  Besides, it doesn't seem to make any difference what I put in there.  The Catalyst Control Center (CCC) just seems to do whatever the hell it wants to do anyway.

Right now I am using dual monitors, but there are several problems.  One, the wallpaper is spread across both monitors with about 1/2 on each.  Kinda makes some of my aircraft photos look more like crashes.  

Two, it seems as though there is about 200 pixels that are not displayed to the right side of monitor 1 (monitor 2 is "left of 1").  That area is not scrollable and I think the only thing that might actually be using are the top and bottom panels.  They have stuff on them that I cannot see because it is off the edge of the screen.

Three, even though I configured each monitor as 1280x1024 before making the "Big Desktop", one monitor is 1280x1024 and the other is 1600x1200.  The CCC will not let me correct this and I have tried many things in the xorg.conf with no affect at all. 

But when I run the CCC now, there is a tab called "Display Options".  The only option is to enable Xinerama but it is greyed out.  It still looks like it is enabled, but still greyed out.  The last line says "You currently have only one desktop enabled.  Configuring more than one desktop in the Display Manager will allow you to configure Xinerama."  

that gets me to the question.  How in the *&&^%^#*@ do I do that?  I have searched the forum, the Ubuntu Help, and Google and just can't find that.  Probably just need the right search arguments.  anyway, as I understand it, when Ubuntu is installed it creates 2 desktops.  Is this correct, or does it create ONE desktop with TWO Workspaces?  

Any help for me???


TIA

xeddog

---

### Post by cditty on 2009-01-11
I am in the same boat as you.  I've even tried hand writting the conf file and that didn't work.  Hopefully someone will ocme along and tell us what we need to do.

---

### Post by xeddog on 2009-01-12
Sheez.  Looks like we are SOL.  We must be the only two trying to set up dual monitors with Radeon cards.  :-)

xeddog

---

### Post by vprasaj on 2009-03-02
Well, now we are 3. The same problem. I'm SOL too.

---

### Post by vprasaj on 2009-03-02
Hey... SOLUTION!!!

I just played a little with options and success.

First you have to set at least two desktops. Skip this if you already have it. (You can do that after you added desktop switcher to your panels. Then you right click on it and then you can set number of desktops.)

Run Catalyst Control Center as super-user.

```
sudo amdcccle
```

Then you need to set both screens as one.
In display manager click that arrow in one of the screens and select "Single(Independent Display)" Look at the picture below. (My screen in this picture is already set and uses xinerama.)

[[img]http://www.shrani.si/t/1L/XB/1eEwunFg/slika.jpg[/img]](http://www.shrani.si/?1L/XB/1eEwunFg/slika.png)

Then you can go to Display Options and set Xinerama.

[[img]http://www.shrani.si/t/1L/13x/VFl6hyX/slika-catalyst-control-c.jpg[/img]](http://www.shrani.si/?1L/13x/VFl6hyX/slika-catalyst-control-c.png)

At some point it will ask you to restart your computer.

After restart you will have fully functional expand or horizontal span as nvidia calls it. Movies render over both screens with no problem at all. I haven't try any 3D at this point.

Info:
My card is HD3850 AGP version.
Driver is [ati-driver-installer-9.2-x86.x86_64.run]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9.2-x86.x86_64.run")

[[img]http://www.shrani.si/t/r/Gj/1J7LNZHz/slika-catalyst-control-c.jpg[/img]](http://www.shrani.si/?r/Gj/1J7LNZHz/slika-catalyst-control-c.png)

My sistem is 32bit linux mint felicia (well, it's ubuntu).

I hope this will help someone.

Good luck. (SOL is away :lolflag:)

---

### Post by cditty on 2009-03-03
YMMV - I tried this and spent the next hour trying to get my original driver working again.

---

### Post by vprasaj on 2009-03-04
> **cditty said:**
> YMMV - I tried this and spent the next hour trying to get my original driver working again.

It happend to me too.
I just used recovery mode and uninstalled driver with envyng -t.
Then I installed driver back with envyng -t.

Then I rebooted normaly and installed official driver over.

It is good to reboot after every change you make with amdcccle.

You can look at my xorg.conf:
```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
#	Disable	"dri2"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "on"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "amdcccle-Monitor[1]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	Monitor    "amdcccle-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	Monitor    "amdcccle-Monitor[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by xeddog on 2009-03-09
I tried that (with the 9.2 driver installed) and the only way I could get my system back up again was to boot into recovery mode, go to the root prompt, copy my backed up xorg.conf file back, and then resume.  I tried it several times doing things a little differently each time, but nothing worked.  

xeddog

---

### Post by teq. on 2009-03-30
Sorry for the thread revive but I'm having a very similar problem

4650 in a Core2 box w/ latest ubuntu etc (fresh install this morning)
I have the ati drivers & CCC installed

when following the guide that vprasaj has posted (the first image of AMDCCCLE)
I do not get the option of splitting my two monitors into multiple desktops?

when I click on the button it just says "Unknown"


I'm using 2 x 22 monitors, both exactly the same

[IMG]http://unix.org.au/~brett/images/amdcccle.jpg[/IMG]

---

### Post by teq. on 2009-03-31
I have been mucking around with this for hours, It's finally working and I'm not sure exactly what I did that fixed it

Here's my xorg.conf for anyone else in this situation

2x22" monitors w/ ATI 4650 

> Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" LeftOf "aticonfig-Screen[0]-0"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "vesa"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


---

### Post by vprasaj on 2009-04-23
I'm glad that you fix it. :)

I had the same problem. After that I crashed xorg and I have to do repair in recovery mode.

Then I reinstalled driver and make one change at time, reboot and then change one option and reboot ... and so on. Log off didn't work.:confused:

Like that I had no problem.

This was the way in my case. But you can have more luck. :)

Again. My card is AGP HD 3850. Maybe because of the card I had to do it this way.

---

### Post by syxxness on 2009-04-24
> **teq. said:**
> I have been mucking around with this for hours, It's finally working and I'm not sure exactly what I did that fixed it

Here's my xorg.conf for anyone else in this situation

2x22" monitors w/ ATI 4650

This DID IT! Mostly anyway.  4870, 2x 22" Lcds. Works mostly, except that the Xinerama still isn't turned on.  But I do have two working displays now.  So its a step in the right direction.

That said, I'm still hoping for true dual monitor support from this driver in the future.  Think Windows with Ultra-Mon.

---

### Post by u235sentinel on 2009-06-16
> **teq. said:**
> Sorry for the thread revive but I'm having a very similar problem

4650 in a Core2 box w/ latest ubuntu etc (fresh install this morning)
I have the ati drivers & CCC installed

when following the guide that vprasaj has posted (the first image of AMDCCCLE)
I do not get the option of splitting my two monitors into multiple desktops?

when I click on the button it just says "Unknown"


I'm using 2 x 22 monitors, both exactly the same

[IMG]http://unix.org.au/~brett/images/amdcccle.jpg[/IMG]


do you run amdcccle to get the control panel for your ati card?  When I run amdcccle I get nothing on the screen.  It just flashes a few times then it sits there doing nothing :/

I've noticed with my Radeon Mobility X1600 on my laptop that with my big desktop setup, the monitor identified as number 1 works great but monitor number 2 has a problem with refresh.  Moving anything on that screen is VERY slow with refresh.  I was hoping there might be an option in the ati control tool that I may have perhaps missed.

I'm running ubuntu 8.04 btw.
Thanks

---

