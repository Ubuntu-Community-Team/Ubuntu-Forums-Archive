---
title: "Where did I go wrong"
date: 2006-11-12
forum: Multimedia &amp; Video
---

### Post by Al3xanR0 on 2006-11-12
So close yet so far away. I recently purchased a Dell Inspiron E1505 for school, I installed Kubuntu Dapper on it (naturally), then configured it to my taste. Next I decided to give it some more visual appeal by installing AiGLX and Beryl. The system specs are as follows: 

PRO: Intel Core 2 Duo T2700 2.16GHz/667MHz
LCD: 15.4 Wide Screen SXGA
GFX: Nvidia GeForce Go 7300 TurboCache
MEM: 512MBx2 Shared Dual Channel DDR2 533MHz
HDD: 120GB 5400RPM SATA
OPT: 8x DVD+/-RW DL DVD+R
AUD: Integrated Sound Blaster Audigy
NET: IPW3945

I followed the instructions [here]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX") verbatim, well maybe not verbatim but close enough to it. If you care to compare here are my exact steps

```
su
``` (I disabled sudo never could get used to it)

```
apt-get update
```

```
apt-get dist-upgrade
```

```
vi /etc/apt/sources.list
```

I added the following repository deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) dapper main aiglx

Next I downloaded the GPG key
```
wget http://ubuntu.beryl-project.org/quinn.key.asc -O - | apt-key add -
```

Next I started downloading AiGLX and dependent files
```
apt-get install linux-dri-modules-common linux-dri-modules-`uname -r`
```

This rendered an error to the effect of its inability locate linux-dri-modules so I entered the following:

```
apt-cache search linux-dri-modules-common linux-dri-modules-`uname -r`
```

then:

```
apt-cache search linux-dri-modules
```

Which indicated that the "linux-dri-modules" did not reside on that mirror. I had to do quite a bit of googling to locate linux-dri-modules for my running kernel, when I did manage to locate it I downloaded it locally then I entered the following:

```
apt-get install xserver-xorg-air-core linux-dri-modules-common
```

Next I installed the elusive linux-dri-modules by entering:
```
dpkg -i /home/al3xanr0/dlds/pkg/deb/ubu/linux-dri-modules-2.6.15-27-686_git20060809-0gandalfn3_i386.deb
```

Next I created sym-links of xorg modules (an apparent work around for the lack of xorg-air modules):  
```
ln -s /usr/lib/xorg/modules/drivers/ /usr/lib/xorg-air/modules/
```

and:
```
ln -s /usr/lib/xorg/modules/input/ /usr/lib/xorg-air/modules/
```

then I backed up my /etc/X11/xorg.conf by entering the following:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.kde.bkp
```

then in my paranoia created a dummy config file to play with so I would still have a working xserver if necessary by entering:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.aiglx
```
Next I made changes to the following sections per the instructions:

> Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA GeForce Go 7300 [TurboCache]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel"		"true"
	Option		"AllowGLXWithComposite" "true"
	Option		"XAANoOffscreenPixmaps" "true"
EndSection

next:

> Section "Screen"
	Identifier	"Default Screen"
	Device	"NVIDIA Corporation NVIDIA GeForce Go 7300 [TurboCache]"
	Monitor	"Generic Monitor"
	DefaultDepth	24
	Option		"AddARGBGLXVisual" "true"
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

then:

> Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option		"AIGLX" "true"
EndSection

finally:

> Section "Extensions"
	Option "Composite" "Enable"
EndSection

I installed Beryl by entering:
```
apt-get install beryl
```

then:
```
apt-get install emerald-themes
```

then I backed up my /etc/kde3/kdm/kdmrc by entering:
```
cp /etc/kde3/kdm/kdmrc /etc/kde3/kdm/kdmrc.bkp
```

Yep while I was at it I created a dummy kdmrc:
```
cp /etc/kde3/kdm/kdmrc /etc/kde3/kdm/kdmrc.aiglx
```

next:
```
vi /etc/kde3/kdm/kdmrc.aiglx
```

edited ServerCmd=/usr/bin/Xorg-air :0 from ServerCmd=/usr/bin/X -br

then:
```
cp /etc/kde3/kdm/kdmrc.aiglx /etc/kde3/kdm/kdmrc
```


Next I created a beryl startup script

```
vi /home/al3xanr0/.kde/Autostart/beryl.start
```

next edited it by adding the following entries:

> [Desktop Entry]
Encoding=UTF-8
Exec=beryl-manager
GenericName[en_US]=
StartupNotify=false
Terminal=false
TerminalOptions=
Type=Application
X-KDE-autostart-after=kdesktop

then changed the permissions to the beryl startup script by entering the following:

```
chmod +x /home/al3xanr0/.kde/Autostart/beryl.start
```

Finally after double checking for orientation and spelling of entries, I entered the following:

```
cp /etc/X11/xorg.conf.aiglx /etc/X11/xorg.conf
```

keeping the original in tact of course, I've been burned once too many.

Now to see the results, I did a quick ctrl+alt+backspace Kubuntu attempts to reboot then just craps out after services load which leaves me with no choice but to Ctrl+Alt+Del out of a frozen boot splash.

so I restore the xorg.conf from backup I am able to login; however, when I login there are no window borders and I am unable to type into data fields, command line interface. Nevertheless, I did see the Beryl icon in the taskbar so I clicked on it selected kwin and wha la! window borders reappear and suddenly I have regained control over my keyboard.
 
back to the google, after some extensive searching I managed to locate another how to that included one step that was missing from the previous 

so I entered the following:
  
```
apt-get install nvidia-glx
```

once again I entered the following:

```
cp /etc/X11/xorg.conf.aiglx /etc/X11/xorg.conf
```

After another Ctrl+Alt+Backspace to my delight this time I was greeted with a Nvidia splash  screen; however, it seems as if things have progessively worsened. The kdm menu options, kde menu, context menu, etc did not display any text I know this because I was still able to login in spite of the fact that kdm did not render text. Once kde started I opened a command line window and experienced the same results, I was able to type but just unable to see what was being typed (I have included a screen shot for viewing displeasure). Incedentally beryl icon is no longer located in the task bar. I restored the xorg.conf from backup again then edited the dummy xorg.conf (yes I am paranoid) by adding 

> Option		“TripleBuffer” “true”

to the device section. I read somewhere that it would help with performance. once again I entered the following:

```
cp /etc/X11/xorg.conf.aiglx /etc/X11/xorg.conf
```	 

After another Ctrl+Alt+Backspace I was still delighted to be greeted with the Nvidia splash screen. However, this time every login attempt resulted in X crashing, I never got any further than kdm and the text rendering (or the lack there of) issue only made matters worse.

Where did I go wrong?

---

### Post by Al3xanR0 on 2006-11-13
I know that it may be a bit much to read, but I wanted to include as much information in the way of details as possible. Some help would be appriciated.

---

### Post by Al3xanR0 on 2006-11-14
Perhaps it was too much detail, 80 + views and not any advise?

---

### Post by goldenfly on 2006-11-19
I also ran into a similar bug. Basically, some text on my screen won't display at all, and some will appear to not display, but re-appears when scrolled-over... Others will appear as weird characters (usually consists of whitespaces and underscores).

My KONSOLE doesn't display anything now, and the menus all have those weird characters!

- I have a Toshiba M30 (nVidia 5xxx level card)
- Ubuntu Dapper 6 (the first release version, forgot num)
- GNOME & GNOME-XGL installed

Here's what I did:
- apt-get upgrade-system
- apt-get install xserver-xorg-air-core
- apt-get linux-dri-modules-common
- apt-get linux-dri-modules-`uname -r`
- modified xorg.conf (recovered old version though)
- modified gdm.conf-custom (also recovered)

I'm suspecting that air is the issue... unless the upgrade-system was a bad move :S...


I would appreciate any help / hints... I'm not in much of a hurry because I only use Eclipse on my ubuntu... and that still works... When i get time (like after Xmas), I'll just install Edgy :D

---

### Post by goldenfly on 2006-11-19
Well that was fast... I uninstalled air-core using synaptic, and everything worked again! Even XGL!

I learned to be satisfied with what i got... well at least until i can install a new version of Ubuntu :D

---

