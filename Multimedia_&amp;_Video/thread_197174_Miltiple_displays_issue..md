---
title: "Miltiple displays issue."
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by UrbanSage on 2006-06-15
Hi
Being a newb I have a hard time enabling my other monitors.
I have read through a number of other threads describing how to set up multiple displays. I followed the descriptions in [this]("http://www.paralipsis.org/2006/01/enabling-xinerama-in-ubuntu") link.

output of lspci |grep VGA is:
[i]0000:00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
0000:03:09.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)
0000:03:0a.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)[/i]

telling me that my drivers are installed. Correct?

Then I modified my /etc/X11/xorg.conf to this:
[i]
Section "ServerFlags"
Option "xinerama" "true"
Option "DefaultServerLayout" "Multihead"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82865G Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Device"
        Identifier      "nVidia 1"
        Driver          "nvidia"
        BusID           "PCI:3:9.0"
EndSection

Section "Device"
        Identifier      "nVidia 2"
        Driver          "nvidia"
        BusID           "PCI:3:a.0"
EndSection

Section "Monitor"
	Identifier	"DELL"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Center Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"DELL"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "Left Screen"
        Device          "nVidia 1"
        Monitor         "DELL"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Right Screen"
        Device          "nVidia 2"
        Monitor         "DELL"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section			  "ServerLayout"
	Identifier	   "Multihead"
	Screen 0	 "Center Screen" 0 0
	Screen 1	 "Left Screen" LeftOf "Center Screen"
	Screen 2	 "Right Screen" RightOf "Center Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection[/i]

Sorry if this displays all jumbled around :rolleyes: 

My problem is that the nVidia cards do not turn on at all.

I would like to switch my work environment from Windows to Ubuntu but I need my three monitors if this is to happen.

Thanks!

---

### Post by HankB on 2006-06-15
you need to start by looking at /var/log/Xorg.0.log and search for error messages and warnings.

I also think that 
 BusID "PCI:3:a.0"
should be
 BusID "PCI:3:10.0"

Because that's what I had to do. 

You might try getting the two nVidia cards working first and then add the third.

HTH,
hank

---

### Post by UrbanSage on 2006-06-15
Found this in Xorg.0.log
[i](II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)[/i]

When specifying the driver in xorg.conf is nvidia only a symbolic driver name in the tutorials?

I will try changing the *a* to a *10*
The Intel card is onboard and I guess with my limited knowledge of linux I will have to reinstall Ubuntu with this board disabled in the bios to make the nvidias function. Currently they have not ignited even once. Fresh system instal so no loss.

---

### Post by HankB on 2006-06-15
nvidia is a module that take some extra steps to install. There are directions here:
[http://ubuntuforums.org/showthread.php?t=139264](http://ubuntuforums.org/showthread.php?t=139264)

The name of the module that installs otherwise is 'nv' so if you change the device section (in /etc/X11/xorg.conf) from 'nvidia' to 'nv' it might work. Eventually you might want to use the nvidia driver anyway.

Rather than reinstall, you can rerun the process that configures the X server. I think that's something like "dpkg -configure xserver-common" which should rerun the X configurator, or you can run "X -configure"

Regardless of what you do, you'll want to make a copy of your config file first. I do anyway. ;)

HTH,
hank

---

### Post by bean1975 on 2006-09-17
UrbanSage, do you use three monitors with a 865G and an nVidia MX 4000 AGP 8x card?

---

