---
title: "Want open source ATI driver, but: client glx vendor string: ATI"
date: 2007-02-14
forum: Multimedia &amp; Video
---

### Post by warjowuch on 2007-02-14
Hi there,
One more Ati-issue :-)
I have a 9200SE card, which is undoubtetly supported by both fglrx (with old libGL.so.1.2) and the open-source ati driver. On my livecd I've seen it work 3d and beryl etc. I copied the livecd's xorg.conf to my working system, uninstalled (completely removed) the fglrx-driver, made sure I had the mesa-things libgl1-mesa-glx and libgl1-mesa-dri reïnstalled, reïnstalled the xorg-xserver-driver-ati (or whatever the thing is called) installed, but still no direct rendering. xorg.conf is also correctly set up (directly taken from livecd's config).

glxinfo keeps saying this string:

client glx vendor string: ATI

I don't know what to do to solve this problem...
I have searched these threads and of course the whole bunch of howto's

[http://www.ubuntuforums.org/showthread.php?p=2149822#post2149822](http://www.ubuntuforums.org/showthread.php?p=2149822#post2149822)
[http://www.ubuntuforums.org/showthread.php?p=2149756#post2149756](http://www.ubuntuforums.org/showthread.php?p=2149756#post2149756)

I hope someone can help!

---

### Post by warjowuch on 2007-02-15
Ok, i have tried a lot of other things, but I can't locate the ati-owned files, the left-overs from the fglrx. Why does the xorg-xserver-driver-ati not overwrite those files...

---

### Post by warjowuch on 2007-02-19
here a *bump*

---

### Post by doobydave on 2007-02-21
I'm not sure, but isnt the "ati" in glxinfo refering to the open source driver?

i'm trying to get the proprietry one working on my 9600 pro and having little joy.
maybe post your xorg.conf and the other stuff from glxinfo.

---

### Post by warjowuch on 2007-02-21
Hi there, thanks for your reply!
Well, in glx-info, ATI stands for the owner, the company ATI, while ati should stand for the driver...  And my xorg.conf should not matter as it is exactly the same as the one that *worked* with the opensource driver on the livecd, I copied it to my installed ubuntu...

glx-info just crashed my X... right on. And it was as what stand here:
[http://www.ubuntuforums.org/showpost.php?p=2178230&postcount=14](http://www.ubuntuforums.org/showpost.php?p=2178230&postcount=14)

fglrx does not work? Maybe get an old libGL.so.1.2 from fglrx 8.24... look around on the forums, you will find one (allthough the issue related to my solution only applied to 9250 and older cards I thought... but it my be worth a try)
Otherwise, I have got it for you and may mail the thing...

---

### Post by warjowuch on 2007-02-27
*bump*?

---

### Post by doobydave on 2007-02-27
Hiya, me again.

Dunno if its worth trying to run- 
sudo dpkg-reconfigure xserver-xorg
to rebuild your xorg.conf. You will be able to choose the ati driver during the reconfiguration.

But, i suspect you have tried this already. And i dont really have any other ideas - for i am noob.

---

### Post by warjowuch on 2007-02-28
yeah, tried that, but it seems to be something in the left-overs from the fglrx-package, even though I selected 'completely remove' in synaptic.
I am sure there is nothing wrong with the xorg.conf.

THanks though for your input, appreciate that.
If I find the solution, I'll post it here

---

### Post by warjowuch on 2007-03-05
Ok then,
update: I tried following 2 guides:
the one from the [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide), from revert to xorg.conf driver, and another one considering the same thing byu doing sodu apt-get remove --purge xorg-driver-fglrx, so the old libGL.so.1.2 will be restored to xorg's version. Alspo reinstalled both libgl-mesa-glx and -dri packages... Still, no thing.

I took a look in my disabled-modules-file and found the radeon-driver being disabled. Oops, so I thougt, this is the solution. So I removed it from the list, restarted, no result! So I still have no idea...

my xorg.conf:
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"dbe"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Driver		"radeon"
	Option		"EnablePageFlip" "true"
	Option		"RenderAccel" "true"
	Option		"ColorTiling" "on"
	Option		"AccelMethod" "XAA"
	Option		"XAANoOffscreenPixmaps" "on"
	#Option		"AGPFastWrite" "on"
	#Option		"AGPMode" "4"
	Option		"AGPSize" "32"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"F730"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Monitor		"F730"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1856x1392" "1792x1344" "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```,

xorg.0.log, which seems to say direct rendering indeed IS enabled, but still direct rendering from glxinfo sais no. While now it just froze my x...??
See the attachment:

Who can help out?? And no, don't come up with the known guides, I have tried all those things, as you can read in my former posts.

---

### Post by doobydave on 2007-03-07
You're not getting a whole lot of help are you. I wonder what the ratio of solved/unsoved threads is in ubuntuforums is?....

 Two more noob ideas.
Try "ati" instead of "radeon" in the device section of xorg.conf (sure is was the default one)
Also try disabling AIGLX in xorg.conf

Reinstall ????

My problem still unsolved. Have filled bug report. [https://launchpad.net/ubuntu/+source/xorg/+bug/89024](https://launchpad.net/ubuntu/+source/xorg/+bug/89024)

I dont think it is similar to your old one unfortunately.
Good luck!

---

### Post by mastu on 2007-03-14
Hi,

I gor the same problem in a past, after searching internet i got an idea that porblem in wrong libGL.so. All my tries to reinstall mesa libs did nothing, so i decided to do some nasty thing, i just removed libs

rm /usr/lib/libGL*

after this

apt-get install --reinstall mesa-libgl1 mesa-libgl1-dri mesa-libGLu glx-utils

and all states to work after this, no any ATI in glxinfo otput

---

### Post by gribelu on 2007-03-27
I had the same problem. I seem to have better 2D performance with the open-source driver.
I found my answer through google, at this link: [https://help.ubuntu.com/community/RadeonDriver#head-c0b2e4234d5129b5b16509e8dcf5685e001dfd1e]("https://help.ubuntu.com/community/RadeonDriver#head-c0b2e4234d5129b5b16509e8dcf5685e001dfd1e")

Wich is.. sudo apt-get remove xorg-driver-fglrx; sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri

Enjoy :)

---

### Post by warjowuch on 2007-03-28
When you would have read my posts, you would have known I allready did those things plenty of times. But :-) thanks anyway for your efforts!
But, an upgrade to feisty beta and replacing some congifiles in the process, I am now rid of this problem. But which configfile it was, or which program files are overwritten by the upgrade... I don' t know... So it is not a real solution, but it is solved...

---

