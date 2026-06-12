---
title: "1280x1024 and now can't use monitor.."
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by Defection on 2007-06-13
I'm new to Ubuntu and its' forums. Sorry if this has already been answered or if I am in the wrong location...
I also don't know the technical terms so i may have to describe things strangely?

I recently installed Ubuntu and although I've had a number of smaller problems I am having fun with it.  My biggest problem (up till now) has been that the resolution was always at 1024x768 or something like that, which is waaaay too large for me.  After browsing the forums for a while I came across a couple things that helped. One which was supposed to but did not was adding "1280x1024"  to the...um...Gedit? thingy? under the monitor stuff?  So i tried that and still it did not appear as an option. Next I followed someone else's advice and ran some other thingy on Terminal and got a Blue box config kinda thing. After following the steps in that I changed the default setting to 1280x1024 and restarted via ctr+alt+backspace.  Now I have lots of horizontal bars across my screen which renders the computer completely useless...I can't even see the mouse...does this mean I have to reinstall Ubuntu AGAIN!?  Sorry for the lengthy message but I thought a history would be helpful.  thanks again to whoever may reply!!!

*Just so you know. The welcome screen is perfectly fine and i think in 1280x1024, but after i put in username/pw it just goes crazy with lots of slanted horizontal bars....

---

### Post by reclusivemonkey on 2007-06-14
> **Defection said:**
> 
I recently installed Ubuntu and although I've had a number of smaller problems I am having fun with it.  My biggest problem (up till now) has been that the resolution was always at 1024x768 or something like that, which is waaaay too large for me.

Do you mean you want a resolution of 800x600 or lower?

I am not sure how you are reading this if your display is corrupted, but it should be a relatively easy fix. Please post

[LIST=1]
[*]What video card you have
[*]What monitor you have
[/LIST]

and attach, NOT post, your /etc/X11/xorg.conf file.

---

### Post by scott_g on 2007-06-14
You are getting a bunch of horizontal bars because your screen refresh rate is set too high.  

There are two ways to fix this.  The easy way uses a liveCD (like the Ubuntu install CD,or KNOPPIX).  If you have this, skip to the second part.  If not, keep reading.

_Step 1:_ (Allows the computer to boot into a graphical mode)
I would boot into the recovery mode (an option in grub), and type the following:

```

nano /etc/X11/xorg.conf

```

Scroll down (using the arrow keys) until you get to a line that says:

> 
        Horizsync       ##-##
        Vertrefresh     ##-##

Change the upper value to a lower number (around 60, until you get it up and running).

Reboot and it will hopefully boot into a graphical screen.

_Step 2:_ (Edit configuration files to have a correct refresh rate)
If using a liveCD, mount your / drive using a fdisk -l to find your drive, then a mount -t ext3 /dev/<hd>.

Next, open a terminal.  Type in the following:

gtf <height> <width> <refresh>

Eg: 
```

gtf 1280 1024 60

```

Copy and paste the resulting line (ctr-shift-c) into your /etc/X11/xorg.conf file of your / hard drive (depends on where you mounted it if using a LiveCD), in the "Monitor" section (under your hsync / vertrefresh values).  You should see a horizsync value in the commented line for example:

> 
# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz


In this case, you would need to edit your hsync value in your xorg.conf file to match the above line (63.6 in this case).

Here is an example of my "Monitor" Section:

> 
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-65
	Vertrefresh	43-60
	# 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  	modeline  "1280x1024_60.00" 108.88 1280 1360 1496 1712 1024 1025 1028 1060 -HSync +Vsync
  
 
	# 1280x1024 @ 50.00 Hz (GTF) hsync: 52.70 kHz; pclk: 89.38 MHz
	modeline  "1280x1024_50.00" 89.38 1280 1352 1488 1696 1024 1025 1028 1054 -HSync +Vsync
	# 1024x768 @ 50.00 Hz (GTF) hsync: 39.55 kHz; pclk: 51.89 MHz
	modeline  "1024x768_50.00" 51.89 1024 1064 1168 1312 768 769 772 791 -HSync +Vsync
	
	
EndSection


Next, add your desired screen resolution to the Screen Section, in the Mode line.  An example is below.

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia 7600GS"
	Monitor		"Generic Monitor"
	
	#Option "UseEdidFreqs" "false"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"	"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"	"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"	"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"	"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"	"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"
	EndSubSection
EndSection

```

Good Luck; if you need something clarified, just ask.

Scott

---

