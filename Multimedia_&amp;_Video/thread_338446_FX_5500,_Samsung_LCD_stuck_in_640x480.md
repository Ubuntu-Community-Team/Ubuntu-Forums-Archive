---
title: "FX 5500, Samsung LCD stuck in 640x480"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by rmills on 2007-01-14
so as it says, I'm running Edgy on an old Dell with GeForceFX 5500 (capable of 1600x1200 DVI out) and it's connected to Samsung's 1080p LCD (capable of 1920xsomething) with a DVI to HDMI cable.  After installing the card, the monitor was connected via VGA, I ran:

sudo dpkg-reconfigure xserver-xorg

and went through and reset everything.  In doing this, the box was able to detect the monitor and it said "Samsung" and most of the stuff was already configured for me.  The resolution was set at 1024x768 by default from that point.  I rebooted the computer, installed the nvidia-glx drivers following the suggestions here: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia).  Restarted and the same resolution came up.  I swapped the connection for DVI-HDMI and rebooted again.  This time the resolution came up at 640x480.  I thought maybe I had to rerun the reconfigure so I did.  It didn't detect the monitor this time, instead saying "Generic Monitor".  The resolutions selected in the reconfigure however were everything up to 1024x768 AND 1600x1200 (which is the only one I really want and is now the only one I have marked).  In /etc/X11/xorg.conf:

Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5500]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-80
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5500]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200"
        EndSubSection
EndSection


The display still comes up in 640x480, despite it not being an option in the xorg.conf.  In System > Preferences > Screen Resolution, it is the only option.  Anybody have any suggestions?  Thanks.

---

### Post by Android8675 on 2007-01-16
I tried that on my LN-S4095D Samsung, After picking up and reading *the manual* I found out that PCs are NOT supported via the HDMI port. I dropped the DVI -> HDMI cable and connected my PC to the normal PC Input on the TV and it booted up at 1280x1024.

Only problem I'm having now is getting ubuntu into 1980x1080 mode. Supposed to be supported, but not having much luck with that yet.

Maybe HDCP won't let my PC run at 1080p? I dunno. Hope this helps ya.

---

### Post by tseliot on 2007-01-16
install the Nvidia driver and then type:
```
sudo nvidia-settings
```

and set the resolution you need

---

### Post by rmills on 2007-01-25
Android: That'd be great if the VGA would support something higher than 1200x1024.  My DVI out is what supports the max resolution and I'd prefer to get the best out of my hardware.  I wish there was just someway to force the output to be higher than what it's detecting the monitor can handle.  Perhaps I should have started reading my TVs manual before I started plugging things into it.  I was just too excited.

tseliot: tried that.  also tried using automatix which i heard installs a different nvidia-glx version.  neither worked.  to be clear, after running nvidia-settings i still had to change the xorg.conf file to change "nv" to "nvidia" to get the right drivers running, but still no luck.  I think Android is right though.


Unless I can find a way to force higher resolutions out of the video card without it detecting the monitor, I might have to, unfortunately, give MCE2005 a shot and see if it can handle the resolutions.

---

### Post by jual_mahal1 on 2007-01-25
**rmills**, I think I want to try this at home after work. This is because my **19" ViewSonic va912b** keeps popping up its on-screen display configurator at certain conditions (like running appications with demanding graphics) under Linux. When this happens, the whole screen will blink a few times at me ;P. It never happens under Windows XP.

The LCD monitor can support the maximum resolution 1280 x 1024 @ 60/70/72 Hz but I could only manage to set it at the lowest refresh 60 Hz by using DVI output from my **Nvidia FX 5500 256MB** (through **nvidia-settings** utility though). I am also setting my display in **TwinView** mode by connecting my 15" Acer CRT monitor on the analog output.

I will try this at home...

_In xorg.conf under [Screen] section for my LCD setup:_

[B]option "UseEdidFreqs" "False"
option "ModeValidation" "NoEdidMaxPClkCheck"[/B]

---

### Post by robquin on 2007-01-26
I have had a similar type of problem on 2 of my computers since I changed to Ubuntu 6.06 (Ubuntu 5.10 worked straight out of the box). I presume that the difference is to do with different versions of xorg being included in the different Ubuntu distributions but I don't have the time to check this out.

It seems that when xorg starts up, it looks at the Modes part of the Screen section of your xorg.conf file. It then gets the monitor capabilities via an EDID query to the monitor. It puts both pieces of information together to generate the necessary timings. If the query to the monitor doesn't succeed then it defaults to something safe (640x480). ](*,)    The solution is to put a modeline or a mode statement in the Monitor section of your xorg.conf.     Some of this HowTo is relevant [http://www.tldp.org/HOWTO/XFree86-Video-Timings-HOWTO/index.html](http://www.tldp.org/HOWTO/XFree86-Video-Timings-HOWTO/index.html)

One of my computers is a dual head setup with the second monitor running through a KVM. When the monitor is connected directly to the display adapter it works fine but running through the KVM it runs at 640x480. I had the specs for this monitor so I installed the videogen deb package and ran the "some_modes" tool to generate some modelines. I then put one of these modelines in the Monitor section of my xorg.conf and restarted the xserver. Everything worked fine at 1280x1024. here is part of my xorg.conf file for this computer.

Section "Device"
        Identifier      "MGA G400_1"
        Driver          "mga"
        BusID           "PCI:1:0:0"
        Screen          0
EndSection


Section "Device"
        Identifier      "MGA G400_2"
        Driver          "mga"
        BusID           "PCI:1:0:0"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "E-171_1"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "E-171_2"
        Option          "DPMS"
        Modeline "1280x1024" 104.96 1280 1320 1384 1640 1024 1026 1030 1078  # 105 MHz, 64.0 kHZ, 59.4 Hz
EndSection

Section "Screen"
        Identifier      "Screen_1"
        Device          "MGA G400_1"
        Monitor         "E-171_1"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
       SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen_2"
        Device          "MGA G400_2"
        Monitor         "E-171_2"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Screen_1" LeftOf "Screen_2
        Screen          "Screen_2
        Option          "Xinerama"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection



Note only the second monitor needed the Modeline statement as the first monitor connects directly to the display adaptor.





I tried to do the same thing on the second computer but it didn't work because I couldn't find the right values to enter into the some_modes utility. I then installed the read-edid deb package and did    sudo get-edid | parse-edid
This produced a new monitor section which I pasted into the xorg.conf file. I commented out the original monitor section, restarted X and everything worked fine. This is part of the xorg.conf that I ended up with.

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Driver		"nv"
	BusID		"PCI:2:0:0"
EndSection

#Section "Monitor"
#	Identifier	"LL-T15A4-B"
#	Option		"DPMS"
#	Modeline "1024x768" 65.00 1024 1048 1188 1344 768 771 777 806
#EndSection

Section "Monitor"
        # Block type: 2:0 3:fc
        Identifier "LL-T15A4-B"
        VendorName "SHP"
        ModelName "LL-T15A4-B"
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:fd
        HorizSync 22-62
        VertRefresh 50-75
        # Max dot clock (video bandwidth) 80 MHz
        # Block type: 2:0 3:ff
        # DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

        Mode    "1024x768"      # vfreq 60.004Hz, hfreq 48.363kHz
                DotClock        65.000000
                HTimings        1024 1048 1184 1344
                VTimings        768 771 777 806
                Flags   "-HSync" "-VSync"
        EndMode
        # Block type: 2:0 3:fc
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:ff
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
	Monitor		"LL-T15A4-B"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


I hope one of these methods works for you, Rob

---

