---
title: "IBM-9495 17&quot; LCD Monitor HOWTO"
date: 2006-06-19
forum: Multimedia &amp; Video
---

### Post by Indras on 2006-06-19
I've installed quite a few versions of Linux, but I am my no means an expert.  I usually only install it, use it for a few hours, and then switch back to Windows for a few months and repeat the process.  In every version of every distribution I've tried, my monitor always has problems at first.  In some versions of Redhat, I had to install in text mode.

However, once the X Server gets started, it usually sets up my monitor and eveything works okay.  My main complaint is the maximum resolution is always 1024x768.  Windows 98SE, 2000, and XP will all allow a maximum resolution of 1280x1024, which works beautifully.

Now that I've made the switch permanently to Ubuntu, it was rather important that I get my monitor working right.  Here's how I got it working:

**First, back up your existing xorg.conf:**
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
**Now, open your xorg.conf file for editing:**
```
sudo gedit /etc/X11/xorg.conf
```
**Scroll down to the "Monitor" section, set the values for your HorizSync and VertRefresh to the proper settings for this monitor.  I found these in a .pdf file on IBM's website.  If you have a different monitor, you can probably find the information on yours from whomever makes it.  Change the values so that your monitor section looks like this:**
```

Section "Monitor"
	Identifier	"Default Monitor"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	56-75
EndSection

```
Note: this will also fix a lot of flickering problems with this monitor, and your screen sometimes appearing way off center (leaving a big black gap on the left or right).

**Now, add the maximum resolution to your "Screen" section so that you can access 1280x1024.  Each line has to be individually set, or you can just copy and paste the values in.  When you're done it should look like this:**
```
ection "Screen"
	Identifier	"Default Screen"
	Device		"*the name of your video card*"
	Monitor		"Default Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```
**Now save the file and restart your X server with CTRL+ALT+Backspace.  If it does not immediately load into 1280x1024, use the Screen Resolution changer in Ubuntu which can be found at System->Preferences->Screen Resolution.**

I'm using the IBM-9495 17" LCD Monitor and a NVidia Geforce FX 5600 Ultra video card with 128Mb of video ram.  I have installed GLX and Compiz and they run flawlessly at 1280x1024 with this setup.  The only noticeable slowdown is if I enable the water plugin for compiz and turn on the raindrops.  They look fine, but trying to move windows with the wobble animation at the same time is very laggy.

Hope this guide helps somebody.

---

