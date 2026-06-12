---
title: "Changing resolution (stuck at 640x480)"
date: 2006-08-30
forum: Multimedia &amp; Video
---

### Post by snaggletooth on 2006-08-30
My resolution is stuck at 640x480 for some reason. The machine that
I am using is set up to be a server so I've disconnected everything 
except for the power cord and ethernet cable. I vnc/ssh to it if
I need to make any changes. I am a former windows user and there
still some things that I need the gui for. My resolution used to be
1152x864 but when I rebooted recently, it changed to 640x480 and I 
haven't been able to change it back ever since. I even changed the
lowest resolution in xorg.conf to 800x600 and it hasn't changed a
thing. It might be because I have no monitor hooked up. Is there a
way to force X to display at 1152x864/1024x768?

Thanks,
- &#1092; §&#325;&#258;&#290;&#286;&#321;&#282;&#358;&#510;&#510;&#358;&#294; &#1092; -

---

### Post by s6dalane on 2006-08-30
Try generating a new modeline for your monitor. [Here]("http://sh.nu/nvidia/gtf.php") you can find a modeline generator and then add the 2 lines to the "Monitor" section in your xorg.conf file.
For example, mine looks like this:

> Section "Monitor"
	Identifier	"CM721F"
	Option		"DPMS"
	Modeline "1024x768_115.00"  131.43  1024 1096 1208 1392  768 769 772 821  -HSync +Vsync
EndSection

---

### Post by snaggletooth on 2006-08-30
Thanks for the help. Unfortunately it didn't help. Not only is my
resolution still 640x480, but I noticed that in "System->Preferences->
Screen Resolution" the only option is indeed 640x480.
Help is greatly appreciated.

Thanks,
- &#1092; §&#325;&#258;&#290;&#286;&#321;&#282;&#358;&#510;&#510;&#358;&#294; &#1092; -

---

### Post by phreel0aderr on 2006-08-30
I was able to get a higher resolution by manually editing the xorg.conf file. I took the resolution i wanted and added it to my xorg. This worked on an Alienware m5500. Might want to give it a try.

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce Go 6600]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		[COLOR="DarkRed"]"1280x800"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		[COLOR="DarkRed"]"1280x800"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		[COLOR="DarkRed"]"1280x800"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		[COLOR="DarkRed"]"1280x800"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		[COLOR="DarkRed"]"1280x800"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		[COLOR="DarkRed"]"1280x800"[/COLOR] "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

---

### Post by snaggletooth on 2006-08-30
Thanks for the suggestion, phreel0aderr, but I've already tried it. Here is 
my xorg.conf section (I also included the Monitor section that s6dalane
suggested I change):

```

Section "Monitor"
        Identifier      "VA720"
        Option          "DPMS"
        # 1024x768 @ 70.00Hz ([http://sh.nu/nvidia/gtf.php](http://sh.nu/nvidia/gtf.php))
        Modeline "1024x768_70.00"  76.16 1024 1080 1192 1360  768 769 772 800  -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
        Monitor         "VA720"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600"
        EndSubSection
EndSection

```

Thanks again,
- &#1092; §&#325;&#258;&#290;&#286;&#321;&#282;&#358;&#510;&#510;&#358;&#294; &#1092; -

---

### Post by the_0ne on 2006-09-01
> **snaggletooth said:**
> My resolution is stuck at 640x480 for some reason. The machine that
I am using is set up to be a server so I've disconnected everything 
except for the power cord and ethernet cable. I vnc/ssh to it if
I need to make any changes. I am a former windows user and there
still some things that I need the gui for. My resolution used to be
1152x864 but when I rebooted recently, it changed to 640x480 and I 
haven't been able to change it back ever since. I even changed the
lowest resolution in xorg.conf to 800x600 and it hasn't changed a
thing. It might be because I have no monitor hooked up. Is there a
way to force X to display at 1152x864/1024x768?

Thanks,
- &#1092; §&#325;&#258;&#290;&#286;&#321;&#282;&#358;&#510;&#510;&#358;&#294; &#1092; -

I have this same problem.  I just plugged an old vaio I have with a very old nvidia card into a 17 inch flat-screen monitor I use in my office.  First time it booted, came up only 640x480 and no other options under the Resolution administration program.  I rebooted and then I had 1024x768, 800x600 and 640x480.  1024x768 worked fine.  I had the machine on all night.  Had to reboot and now I'm back to 640x480.  Rebooted several times and still no other option.

Were any of you able to figure this out??  Thanks for the help...

---

### Post by palmargard on 2006-09-01
I have the same problem. I'm stuck at 640x480 resolution with nothing else available.

xonf.org looks like:

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon X700 Pro (RV410)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

any help resolving this issue would be highly appreciated.

---

### Post by the_0ne on 2006-09-01
Well, I think I solved this problem, at least for my case.  The problem was these lines were missing from the Monitor section of my /etc/X11/xorg.conf file...

HorizSync   30-70
VertRefresh 43-72

Put those in and restarted X and the machine boots up in 1024x768 again.

---

### Post by snaggletooth on 2006-09-05
Thanks guys, that worked.

&#1092; §&#325;&#258;&#290;&#286;&#321;&#282;&#358;&#510;&#510;&#358;&#294; &#1092; -

---

### Post by almalaci on 2006-09-05
That worked for me too, thanks, I had the same problem. 
Could anyone explain a bit how to determine these values (HorizSync 30-70
VertRefresh 43-72) to best fit my monitor?
And why do I have to manually edit xorg.conf on one monitor (desktop with LCD screen) while I don't have to do it on another one (laptop) ?
Thanks,
almalaci

---

### Post by phreel0aderr on 2006-09-06
@ almalaci
Take your monitors native refresh rate and make sure it is between the values listed. From what it looks like, the range shown should suffice for most LCDs. As for the laptop, it could be possible what when you installed the OS it auto detected all your components. It did this for me (well for the most part). Hope this helps.

---

### Post by Ziox on 2006-09-06
use 

sudo ddcprobe

to find a list of resolution and frequencies that Ubuntu automatically detect.  I believe that sometimes Ubuntu is unable to detect the DDC setting from externel monitors.  (I believe you can enter an option in xorg.conf to force xorg to use DDC options).  As for the laptop, apparently Ubuntu is able to detect DDC from the laptop's monitor better...

---

### Post by J_A on 2007-05-09
hi all of ya, 

so, I've installed ubuntu & kubuntu on my dell inspiron 6400 and so far things seem to be working well and I will freely admit I'm already falling in love with linux. however, there's this screen res problem that is related to this topic, so I'm resurrecting it. 

my screen should have a res of 1280x800 & I have the ATI mobility graphics card. ubuntu only sees 1024x800 and that's the highest res I'm able to get. I tried editing the xorg.conf file and there, it shows the newly added options (like someone already posted in this thread), yet I can't set it to actually use this changed file

having read this thread, I just looked at the ddcprobe file, here are its contents:

"vbe: VESA 3.0 detected.
oem: ATI ATOMBIOS
vendor: (C) 1988-2005, ATI Technologies Inc.
product: M54P 01.00
memory: 16384kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x256
mode: 1024x768x256
mode: 1280x1024x256
mode: 132x25 (text)
mode: 132x43 (text)
mode: 640x480x32k
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x32k
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x32k
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 320x200x32k
mode: 320x200x64k
mode: 320x200x16m
mode: 1600x1200x256
mode: 1600x1200x32k
mode: 1600x1200x64k
edid:
edid: 1 3
id: a900
eisa: LPLa900
serial: 00000000
manufacture: 0 2006
input: analog signal.
screensize: 33 21
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
dtiming: 1280x800@60
dtiming: 1280x800@60"
and then the monitorid follows

I saw that someone suggested adding a couple of lines in the xorg. would this work for my problem? and do I just add them to the end of the file? 

can anyone offer more advice on this? 

thanks :)

---

### Post by chiefrocca on 2007-06-17
> **the_0ne said:**
> Well, I think I solved this problem, at least for my case.  The problem was these lines were missing from the Monitor section of my /etc/X11/xorg.conf file...

HorizSync   30-70
VertRefresh 43-72

Put those in and restarted X and the machine boots up in 1024x768 again.

Thanks for the help...
this is what helped me exactly....still dont know how or why it changed!

---

### Post by dcstar on 2007-07-27
> **Ziox said:**
> use 

sudo ddcprobe

to find a list of resolution and frequencies that Ubuntu automatically detect.  I believe that sometimes Ubuntu is unable to detect the DDC setting from externel monitors.  (I believe you can enter an option in xorg.conf to force xorg to use DDC options).  As for the laptop, apparently Ubuntu is able to detect DDC from the laptop's monitor better...

When I use ddcprobe on my old Nvidia card, it only lists resolutions up to 1280x1024x16m, where I am now running a 1440x900 widescreen! (by having manual modeline entries in my xorg.conf).

At least it explains why Ubuntu (and Windows) didn't offer 1440x900 as available resolutions, the video card didn't have these new widescreen resolution programmed into it when it was manufactured!

I am currently upgrading some to some widescreen monitors at work and I have to manually install a utility to install a 1440x900 resolution entry into the XP Registry on the machines with older video cards - most likely because their DDC output doesn't list that res!

---

