---
title: "Just installed xfx 6800 xtreme and now my screen is messed up"
date: 2006-09-13
forum: Multimedia &amp; Video
---

### Post by Rizla on 2006-09-13
Hey Guys,

I just bought and installed my xfx GF 6800 Xtreme AGP 8x video card, but im having problems getting it to work.  First off, i initially had my setup using the onboard vga connector on my mobo and that worked fine.  I wanted to get a dedicated video card so i bought this NVIDIA based card because i heard they take to linux easier than ATI's.  ANyhow, so i installed the card, as i booted up my computer everything looked fine.  Grub came up, i selected my OS and then it went through the normal boot process, but once it loaded the GUI session manager where i login everything went crazy and i just see a bunch of lines... How do i fix this?  I didnt install any drivers yet, but seeing that i cant even see the desktop how do i do so?  Boot from safe mode?

Please help ASAP.  I need to see whats gonig on.  Thanks.

---

### Post by Rizla on 2006-09-13
I tried installing the drivers via sudo apt-get install nvidia-glx (in recovery console).  It downloaded and installed, but then when i rebooted im still getting the same thing. vertical lines.. Please someone help..

---

### Post by tseliot on 2006-09-13
Try Method 1 of this guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by Rizla on 2006-09-13
> **tseliot said:**
> Try Method 1 of this guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

I havent had a chance to try method 1, but i read it over.  It seems that I did part of the process by installing the driver i guess the second half whcih i missed was updating the xorg.

Hopefully when i get home thats all I have to do.  BTW, as i said, i cant even view the normal desktop so i have to do this in recovery mode.

---

### Post by Rizla on 2006-09-14
Alright, so the good news.  I followed the rest of the guid and i got my screen to display properly.  The only issue im having now is that my screen is shaking/vibrating.  My monitors settings are 68.7kHz/85.0Hz.  Unfortunately my monitor wont allow me to change the frequency.  How do i change it in the xorg.conf?  I did a search but there's only one other thread that i found that had similar issue, but it was from last year.  Any help on this issue?

Here's what the relevant section of my xorg.conf says:
```

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

clueless as usual and seeking some guidence.

---

### Post by Rizla on 2006-09-14
Here's an update of what i've done so far.  I did: sudo dpkg-reconfigure xserver-xorg.  Went through the screens step by step and then rebooted, but im having the same problem.  Here's how my xorg.conf looks like now.  It has a few more lines of info.

```

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIAXFX 6800 XT"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"LG StudioWorks 995E"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIAXFX 6800 XT"
	Monitor		"LG StudioWorks 995E"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

Any ideas?

Also, how do i restart X so that i don thave to reboot everytime i change the xorg.conf file?

EDIT:  ONe thing i've noticed.  Im using a KVM switch between my linux box and my windows box.  They're both using the same monitor.  When i swithc to the windows box and check the monitors settings its set to 60 Hz, but when i swithc to the linux box its at 85.  I cant change this anywhere..  let me do the reconfigure again and do it at 60 this time.

---

### Post by Rizla on 2006-09-14
Well i FINALLY got it fixed.  I had to reconfigure xorg and manually set the resoltion.  Turned out to be not so hard, but def frustrating to a novice.  BTW, if someone wnats to know.  If you want to restart xorg, you have to logout then press ctrl+alt+backspace.  That should apply whatever changes you made.

---

