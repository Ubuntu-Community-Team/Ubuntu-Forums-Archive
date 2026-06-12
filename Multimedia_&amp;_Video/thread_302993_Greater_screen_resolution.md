---
title: "Greater screen resolution?"
date: 2006-11-19
forum: Multimedia &amp; Video
---

### Post by PaulHoffman on 2006-11-19
Greetings. I am using a Priceton monitor that handles up to 1280x1024, but System > Preferences > Screen Resolution only lets me go to 1024 x 768. I even tried editing /etc/X11/xorg.conf to add 1280x1204 to each display and rebooted; no change.

The online documentation gives no hints that I could find. Any pointers are welcome.

---

### Post by Jussi Kukkonen on 2006-11-19
You could try running *sudo dpkg-reconfigure xserver-xorg*, maybe there's some setting you could change...

As an example, many on-board display chips use 'shared memory' and you may have to tell xorg how much shared memory you are using, like 32MB (and make sure that the same amount is specified in your BIOS).

---

### Post by 56phil on 2006-11-19
I had the same problem when I started using Ubuntu. You probably need to install a video driver. What type of video card do you have?

---

### Post by Heilige on 2006-11-19
I'm having the same problem and I even installed one of the latest Nvidia beta drivers and the highest I can go using the Nvidia utility is 1280x800 (which makes everything kinda squished) but I know I can go 1280x1024 but can't, this small screen space is driving me nuts.

---

### Post by Heilige on 2006-11-19
Finally figured it out... Lookup the horizontal and virtical rates for your monitor by googling "yourmonitormodel specs" and then edit the rates in the Monitor section of your xorg.conf file to match them and also add the resolution you want to the mode you use like 24 bit and there ya go. =)

Like so...

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 69.0
    VertRefresh     59.0 - 85.0
    Option         "DPMS"
EndSection

#AND

    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600"
    EndSubSection

---

### Post by 56phil on 2006-11-19
Here's what I did to get an ATI X700 to work on my Gateway M680:
```

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```
Once I installed the driver, I had to edit the /etc/X11/xorg.conf file to add the desired screen resolutions.
```

sudo gedit /etc/X11/xorg.conf

```
This got the full screen resolution but now the system hangs on shutdowm. So, I had to replace 'quiet splash' with 'vga=788' in the /boot/grub/menu.lst file. 
```

sudo gedit /boot/grub/menu.lst

```

I hope this helps. Happy Ubuntu!:)

---

### Post by owyn on 2006-11-19
Just came up with the same fix myself.

However, I cheated and copied the settings from PCLinuxOS xorg.conf hd install on same system. Booting a live cd will also let you get the correct settings for your monitor.

---

### Post by PaulHoffman on 2006-11-20
And I got mine fixed by changing the graphic card driver name in xorg.conf.

Suggestion for the user docs for the screen resolution settings: talk about the fact that the resolutions are based on both the graphic card and the screen settings in xorg.conf.

---

### Post by mutantapple on 2006-11-21
**NOTE:** By what 56Phil meant by changing the screen resolution is:

**EXAMPLE:**

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon X700 Pro (RV410)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    _"1280x1024"_ "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    _"1280x1024"_ "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    _"1280x1024"_ "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    _"1280x1024"_ "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    _"1280x1024"_ "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    _"1280x1024"_ "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

The underlined resolution in your xorg.conf gedit file would be an example of an addition of a screen resolution you can add. ;)

.... Oh I just noticed Heilige already explained that. Ooops.

---

### Post by mutantapple on 2006-11-21
After you do that, hit:

<Ctrl> <Alt> <Backspace>

To restart your computer and it should apply the settings. W00t! :KS

---

