---
title: "multiple monitors not working in Jaunty - xorg.conf?"
date: 2009-08-15
forum: Multimedia Software
---

### Post by heykev on 2009-08-15
Just upgraded to Jaunty and can't get it to use my dual monitor setup -- just shows me the same single-monitor desktop on both screens.

System > Preferences > Display ... seems to indicate that only one monitor is detected.

With previous versions of Ubuntu, I've had success editing the xorg.conf file that was automatically generated on installation.  But with Jaunty that file is completely empty.  Tried using the exact same xorg.conf file that I backed up from my previous Ubuntu installation, but it didn't work and I had to start in low resolution mode.

Running lspci in a terminal gives video info as:

[INDENT]01:05.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 82)[/INDENT]

I had read that Jaunty was friendlier to multiple-monitor setups, but so far that hasn't worked out for me.

Thanks for any/all help!

---

### Post by heykev on 2009-08-15
Do I need to download drivers from the manufacturer?  The most recent Linux drivers from Matrox for this card are from 2006.  I don't know if Ubuntu has already integrated that code, or superceded it, or what.

---

### Post by heykev on 2009-08-15
I've pared down the xorg.conf file that worked under my previous version of Ubuntu.  I'm trying to find out which lines are causing the trouble.

The following xorg.conf file works.  At least it allows me to start up, though it still sends the same single-monitor image to each of the two monitors.

BUT if I uncomment that last line in the "Server Layout" section, startup fails and I have to go into low-res mode.

```

Section "Device"
	Identifier	"Device0"
	Boardname	"Matrox Millennium G450 DualHead"
	Busid		"PCI:1:5:0"
	Driver		"mga"
	Screen		0
	Vendorname	"Matrox"
EndSection

Section "Device"
	Identifier	"Device1"
	Boardname	"Matrox Millennium G450 DualHead"
	Busid		"PCI:1:5:0"
	Driver		"mga"
	Screen		1
	Vendorname	"Matrox"
EndSection


Section "Monitor"
	Identifier	"Monitor0"
EndSection

Section "Monitor"
	Identifier	"Monitor1"
EndSection


Section "Screen"
	Identifier	"Screen0"
	Monitor		"Monitor0"
	Device		"Device0"
EndSection

Section "Screen"
	Identifier	"Screen1"
	Monitor		"Monitor1"
	Device		"Device1"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen 0 "Screen0" 0 0
#	Screen 1 "Screen1" rightof "Screen0"
EndSection

```

---

### Post by heykev on 2009-08-15
The following from

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#xorg.conf]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#xorg.conf")

> Recent versions of xorg.conf intended for use with xrandr 1.2 considerably simplify the video section of the configuration. If you upgrading from an earlier version you may find your existing xorg.conf works against the effective deployment of xrandr. So it is best to start with a new Xorg configuration.

An updated Xorg.conf should:

    * omit dual Device/Screen/Monitor sections
    * omit MonitorLayout option and Screen lines from the remaining Device section
    * omit dual Screen lines from the ServerLayout section
    * omit RightOf/LeftOf indication to the remaining Screen line in ServerLayout section
    * add a "Virtual 2048 2048" line in SubSection "Display" to create a large virtual screen 

There is some mysterious (to me) relationship between Xorg, randr, and Gnome -- and perhaps the Jaunty upgrade has altered this relationship in the name of "increased support for multiple monitors".  But in doing so it seems the loophole solution for my old Matrox G450 card has been closed.  Surely not!

Sadly, if I run

```
xrandr -q
```

in a terminal the output acknowledges only one of the two monitors connected.

```

Screen 0: minimum 400 x 300, current 1280 x 1024, maximum 2560 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      60.0*    75.0  
   1024x768       75.0     70.0     60.0  
   800x600        75.0     72.0     60.0     56.0     65.0  
   640x480        75.0     73.0     67.0     60.0  
   1440x900       60.0  
   1280x960       60.0  
   1360x768       60.0  
   1152x864       75.0     70.0     60.0  
   832x624        75.0  
   840x525        75.0     70.0     60.0  
   700x525        75.0     70.0     60.0  
   640x512        75.0     60.0  
   720x450        60.0  
   720x400        70.0  
   680x384        60.0  
   576x432        75.0     70.0     60.0  
   512x384        75.0     70.0     60.0  
   416x312        75.0  
   400x300        75.0     72.0     60.0     56.0  
   2560x1024      60.0  

```

And this, perhaps is why Ubuntu's System > Preferences > Display Properties also sees only one monitor.

Sorry to post all these "replies" to my own thread.  Trying to add only info that will be useful to others if they have this same problem.

Thanks for any help someone might be able to offer!

---

### Post by martinbaselier on 2009-08-15
If xorg fails you can
**cat /var/log/Xorg.0.log**
to see why it failed (from a terminal)
add:
** | grep EE**
to filter out errors (use WW for warnings)
**man xorg.conf** 
can give you more info (use / to search, h for help)

You could also try to disable randr (it should be with the services)

---

### Post by heykev on 2009-08-17
Thank you, martinbaselier, for the reply.  I'm in the process of following all your advice and will let you know how it goes.

Meanwhile, I've found in the X documentation that my video card, the Matrox Millenium G450 DualHead, is explicitly supported.

Link for those with that older hardware (or interested for whatever reason):

[INDENT][http://www.x.org/archive/X11R6.9.0/doc/html/mga.4.html]("http://www.x.org/archive/X11R6.9.0/doc/html/mga.4.html")[/INDENT]

So perhaps the problem is not with X or the xorg.conf file?

---

### Post by rickcama on 2009-09-30
hi heykev,
i am just behind you, with same card and jaunty. Were you able to get the xorg configured for dual display?
Would appreciate any wisdom sharing.

rickcama

---

### Post by heykev on 2009-10-27
> **rickcama said:**
> hi heykev,
i am just behind you, with same card and jaunty. Were you able to get the xorg configured for dual display?
Would appreciate any wisdom sharing.

rickcama

rickcama,

Sorry for the delayed response!  No, I could not solve the problem under Jaunty, though I had been just fine with previous versions.  If you'd like any hints for those versions, I may can help.  Or if you've found a solution since your post, then I'm all ears.  Nobody here appears to know a solution.

I'm also having another display issue ([separate thread]("http://ubuntuforums.org/showthread.php?t=1302202")) with Jaunty.  Maybe there was some fundamental change with that release that left our older hardware in the dust.

---

### Post by kristopher_d on 2009-11-04
The fix in this thread works for Jaunty.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/292214](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-mga/+bug/292214)

Of course, by now you're likely upgraded to Karmic.  Unfortunately I'm back to single monitor (actually, 2 of them showing the same content).

---

### Post by heykev on 2009-11-06
Anyone interested in this thread should definitely check out the link posted above by kristopher_d.

@kristopher_d -- Thanks for the reply.  This was an older thread but you took the time to help me out.  I'm still using Jaunty -- still have the problem -- but I think that rather than attempt the solutions proposed in your link, I'll look seriously at making the effort of a clean install of Karmic.  If that fixes the problem, then I'll confirm it here.

---

### Post by mbmccurdy on 2009-11-09
I had this problem with Jaunty and now I have installed a fresh Karmic, the problem persists. Both monitors show the same content, xrandr -q detects only one.

=(

---

### Post by eldiabolosk on 2010-12-12
Did anyone this working?

I just installed Xubuntu 10.04. Same thing. Using Matrox G450 Two exactly same monitors showing exactly the same thing. Display options show only one monitor. 
Please let me know if you find a solution.

Ed

---

