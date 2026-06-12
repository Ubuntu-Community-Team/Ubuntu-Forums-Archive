---
title: "nVidia TwinView"
date: 2006-11-17
forum: Multimedia &amp; Video
---

### Post by Ziox on 2006-11-17
[SIZE=4]**Dual Monitor With nVidia TwinView HowTo**[/SIZE]     [LEFT][FONT=Verdana]The following HowTo attempts to enable Dual Monitor support by using the TwinView function of the nVidia binary graphics driver.

 [/FONT][/LEFT]
        [LEFT][B][FONT=Verdana][SIZE=3]System Requirements:

[/SIZE][/FONT][/B][/LEFT]
    [LEFT][FONT=Verdana]A nVidia card with Dual output, whether it is VGA-DVI, VGA-VGA, or DVI-DVI.[/FONT][/LEFT]
    [LEFT][FONT=Verdana]Two Monitors (best if they are the same resolution, but different resolutions will work)[/FONT][/LEFT]
    [LEFT][FONT=Verdana]Installed and Working nVidia Binary graphics driver:[/FONT][/LEFT]
[INDENT][LEFT][FONT=Verdana]    Use the following link to install and enable the binary driver:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

[/FONT][/LEFT]
[/INDENT][SIZE=4][COLOR=Red][FONT=Arial Black]MAJOR (and Delayed) UPDATE:
NEW GRAPHICAL METHOD:
[/FONT][/COLOR][/SIZE]With the recent and awesome release of Ubuntu 7.04 Feisty Fawn, (almost) every nVidia card user's dream of dual monitors is just a few clicks away. LITERALLY! 
Here's the basic breakdown:

[INDENT][B][U][COLOR=Red]For users of nVidia cards with driver 9.xxx, there is a GUI application installed to configure X. 

To access the application, enter:
```
gksudo nvidia-settings
```

And configure to your heart's desire! :guitar:

After all the configuration is done, make sure to save the configuration file.

And that's it! Enjoy![/COLOR][/U][/B]
[/INDENT][LEFT][FONT=Verdana][COLOR=Red][SIZE=4][FONT=Arial Black][/FONT][/SIZE][/COLOR][/FONT][/LEFT]
[COLOR=Red][SIZE=4][/SIZE][/COLOR][INDENT][LEFT][FONT=Verdana] [/FONT][/LEFT]
[/INDENT][LEFT][COLOR=Red][SIZE=4][FONT=Arial Black]OLD METHOD (AND ALMOST OBSOLETE)[FONT=Verdana]**:**[/FONT][/FONT][/SIZE][/COLOR][B][FONT=Verdana]

[/FONT][/B][/LEFT]
        [LEFT][COLOR=Red]***[FONT=Verdana]1. Open Xorg.conf file by activating ONE of the following command (based on your distribution):[/FONT]***[/COLOR][/LEFT]
        [LEFT][FONT=Verdana]Gnome (Ubuntu):[/FONT][/LEFT]
    [LEFT]```
gksudo gedit /etc/X11/xorg.conf
```[/LEFT]
    [LEFT][FONT=Verdana]KDE (Kubuntu):[/FONT][/LEFT]
    [LEFT]```
kdesu kate /etc/X11/xorg.conf
```[/LEFT]
    [LEFT][FONT=Verdana]Xfce4 (Xubuntu):[/FONT][/LEFT]
    [LEFT]```
gksudo mousepad /etc/X11/xorg.conf
```[/LEFT]
    [LEFT][FONT=Verdana]Command-Line Based:[/FONT][/LEFT]
    [LEFT]```
sudo nano /etc/X11/xorg.conf
```[/LEFT]
        [LEFT][COLOR=Red]***[FONT=Verdana]2. Next navigate to your "Device" Section, which should appear similar to the example shown below, the identifier and BusID WILL be different:[/FONT]***[/COLOR][/LEFT]
    [LEFT]```
Section "Device"
    Identifier    "nVidia 7900"
    Driver        "nvidia"
    BusID        "PCI:1:5:0" 
EndSection
```***[FONT=Verdana][COLOR=Red]3. Add the following lines to that section:[/COLOR][/FONT]***[/LEFT]
    [LEFT]```
Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"   
Option "UseEdidFreqs" "True"
Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
Option "UseDisplayDevice" "string" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
```[/LEFT]

        [LEFT]**[FONT=Verdana]These codes are the bare minimum for enabling TwinView.  This should work most people, however, every system is configured differently, so use the following guide to add more options:[/FONT]**[/LEFT]
    [LEFT][FONT=Verdana][http://download.nvidia.com/solaris/1.0-8762/README/appendix-d.html](http://download.nvidia.com/solaris/1.0-8762/README/appendix-d.html)

[/FONT][/LEFT]
        [LEFT][I][B][FONT=Verdana][COLOR=Red]4. Save the file, and restarted X (ctrl+alt+backspace), or reboot.

[/COLOR][/FONT][/B][/I][/LEFT]
        [LEFT][B][FONT=Verdana]You should now have TwinView :). If not, then just post the problem's symptoms, along with your xorg.conf file.

[/FONT][/B][/LEFT]
        [LEFT][COLOR=Red]**[FONT=Verdana]Good Luck! :)[/FONT]**[/COLOR][/LEFT]

---

### Post by bobo1on1 on 2006-11-18
Ok I'll go first, I have a geforce fx5500 with a widescreen tft connected to dvi and a television connected to the vga port with a homemade vga to scart converter (check  here: [http://www.nexusuk.org/projects/vga2scart/](http://www.nexusuk.org/projects/vga2scart/), lots of modelines at the bottom I need to use).
Both the tft and the television work in X.

Here's my device section:

```

Section "Device"
        Identifier      "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"
Option "UseEdidFreqs" "False"
Option "MetaModes" "1440x900,720x480"
Option "UseDisplayDevice" "DFP" #replace 'string' with either 'DFP' (Digital fla$
EndSection

```

This doesn't work, I tried various configurations.
With the default xorg.conf only with added television resolutions I get a picture on the tft when the television is not connected, when I connect the tv and restart X I get a picture on the tv and no picture on the tft.

This is from my Xorg.log:

```

(**) NVIDIA(0): Option "UseEdidFreqs" "False"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "MetaModes" "1440x900,720x480"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
**(WW) NVIDIA(0): Unable to read EDID for display device CRT-1**
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.69.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:0:0:
(--) NVIDIA(0):     CRT-1
(--) NVIDIA(0):     Nexgen MIRAI DML-519 (DFP-0)
(--) NVIDIA(0): CRT-1: 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Nexgen MIRAI DML-519 (DFP-0): 135.0 MHz maximum pixel clock
(--) NVIDIA(0): Nexgen MIRAI DML-519 (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Option "UseDisplayDevice" "DFP" converted to "DFP-0".
**(WW) NVIDIA(0): TwinView requested, but only 1 display devices found.**
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): Invalid display device in Mode Description "720x480"
(WW) NVIDIA(0): Not using mode description "720x480"; unable to map to display
(WW) NVIDIA(0):     device
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1440x900,720x480"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp


```

---

### Post by Ziox on 2006-11-19
> **bobo1on1 said:**
> Ok I'll go first, I have a geforce fx5500 with a widescreen tft connected to dvi and a television connected to the vga port with a homemade vga to scart converter (check  here: [http://www.nexusuk.org/projects/vga2scart/](http://www.nexusuk.org/projects/vga2scart/), lots of modelines at the bottom I need to use).
Both the tft and the television work in X.

Here's my device section:

```

Section "Device"
        Identifier      "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"
Option "UseEdidFreqs" "False"
Option "MetaModes" "1440x900,720x480"
Option "UseDisplayDevice" "DFP" #replace 'string' with either 'DFP' (Digital fla$
EndSection

```

This doesn't work, I tried various configurations.
With the default xorg.conf only with added television resolutions I get a picture on the tft when the television is not connected, when I connect the tv and restart X I get a picture on the tv and no picture on the tft.

This is from my Xorg.log:

```

(**) NVIDIA(0): Option "UseEdidFreqs" "False"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "MetaModes" "1440x900,720x480"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
**(WW) NVIDIA(0): Unable to read EDID for display device CRT-1**
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.69.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:0:0:
(--) NVIDIA(0):     CRT-1
(--) NVIDIA(0):     Nexgen MIRAI DML-519 (DFP-0)
(--) NVIDIA(0): CRT-1: 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Nexgen MIRAI DML-519 (DFP-0): 135.0 MHz maximum pixel clock
(--) NVIDIA(0): Nexgen MIRAI DML-519 (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Option "UseDisplayDevice" "DFP" converted to "DFP-0".
**(WW) NVIDIA(0): TwinView requested, but only 1 display devices found.**
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): Invalid display device in Mode Description "720x480"
(WW) NVIDIA(0): Not using mode description "720x480"; unable to map to display
(WW) NVIDIA(0):     device
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1440x900,720x480"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp


```

Try adding this line to your device section:
```
Option "ConnectedMonitor" "DFP, CRT"
```

---

### Post by bobo1on1 on 2006-11-19
Ok got it working now, here is the config in my xorg.conf:

```
Section "Device"
        Identifier      "NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
Option "TwinView" "True"
Option "TwinViewOrientation" "LeftOf"
Option "UseEdidFreqs" "False"
Option "MetaModes" "720x480,1440x900"
Option "UseDisplayDevice" "CRT,DFP"
EndSection

```

I had to switch the resolutions because twinview sees the vga as the primary monitor, I also had to change RightOf to LeftOf, otherwise the login screen showed up on the television.
Just one little bug, the Bookmarks menu from firefox doesn't show it's full height anymore, it seems it's size is adjusted to the 720x480 resolution.

---

### Post by Webziz on 2006-11-20
Looking for pointers here.

I'm trying to get my Samsung R32R72 32" HDTV to work alongside my Samsung LCD monitor. With my Radeon I managed to get some kind of signal to HDTV (@1024x768) at the same time as 1280x768 on my LCD.

Now, when the machine boots up, everything seems just nice on both the screens, but as soon as X starts up, tv goes blank, and lcd starts up just nicely. 

I'm completely at loss. Tried some different MetaModes, but Ubuntu doesn't seem to care.

Random facts: Using edgy, AGP Nvidia Geforce 7600GS, HDTV is connected on VGA and LCD on DVI.

Thank you, beforehand.


Important parts of xorg.conf:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option "TwinView" "True"	
	Option "TwinViewOrientation" "RightOf"   
	Option "UseEdidFreqs" "True"
	Option "MetaModes" "1360x768, 1280x1024; 1280x1024, 1360x768;1280x1024, 1024x768; 1024x768, 1280x1024; 1280x1024,1280x1024; 1024x768,1024x768"
	Option "UseDisplayDevice" "DFP" 
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
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

---

### Post by mojoman on 2006-11-21
Hi,

I followed the howto but don't seem to get it right. I'm running dapper on my desktop which have BFG GeForce 7600GS 256MB. I'm using a lame-*** old NEC LCD  monitor which is configured as your ordinary run-of-the-mill generic monitor (which has always worked fine) but I'm trying to configure my lovely, brand new, oh so shiny, Hitachi PJ-TX200 HD projector. :D 

Oddly enough, even before I tried with twinview I could see the boot sequence but as the login screen appears the signal to the projector disappears. (I've connected it via the DVI-out to the HDMI-in.)

I thing these are the relevant parts of the xorg.conf:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "RightOf"
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option "UseDisplayDevice" "CRT"
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

Now, I'll attach my xorg.0.log as a rarfile (it was slightly to large) as well (and my complete xorg.conf just in case it's needed). Reading the logfile I gathered that for some reason only one monitor is detected. However, in the logfile the projector is correctly identified as a Hitachi, and I've never entered this information anywhere so it is detected somehow.

If anyone can help me out with this I'd sure appreciate it.

Best regards
/Mojoman

---

### Post by Figgy on 2006-11-21
Okay, my system has 2 nvidia geforce 6600gt's. I am running my main monitor on one, while I am trying to get the second card to run my second monitor. But as of now my 2nd monitor does nothing.
Here is my xorg.conf file ( excerpt )
```
Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
    Option "TwinView" "True"
	Option "TwinViewOrientation" "RightOf"   
	Option "UseEdidFreqs" "True"
	Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
	Option "UseDisplayDevice" "CRT" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
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
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by Ziox on 2006-11-21
To: mojoman, Webziz
Try adding the following line to your "Device" Section:
```
Option "ConnectedMonitor" "DFP, CRT"
```You can try switching the DFP and CRT.

To Figgy:
nVidia Twinview only works on a SINGLE graphics card that supports dual-output. If you wish to utilize both graphics card, visit my Xinerama guide in a week or so. I'm adding support for two graphics card to that guide soon.

EDIT: No need to wait that long! Xinerama Guide has been updated!

---

### Post by mojoman on 2006-11-22
Thanks for the help Ziox.

I tried your advice and even though it didn't do the trick it did make me somewhat wiser.

Adding the line

```
Option "ConnectedMonitor" "CRT, DFP"
```

was bad. When I restarted X (CTRL+ALT+BACKSPACE) it didn't restart. It was just black and I ended up logging in via my laptop in order to restore xorg.conf.

However, the tip about changing CRT to DFP made me look at this line

```
Option "UseDisplayDevice" "CRT"
```

and when I changed it to DFP the computor used the projector instead of the monitor. So, the monitor is CRT and the projector is DFP. Now that's one step in the right direction and I know for sure that the projector can be used in Ubuntu. All that remains is to make the computer use both at the same time. If you, or any one else reading, have any more ideas I'm all ears. :-D 

All the best
/Mojoman

Edit: I tried auto-generating a new xorg.conf with the projector connected. I got a working projector (though the fonts were screwed up on the login screen and the edges of the screen wasn't visible) but my regular monitor didn't work (but I think it was detected because it looked very weird). I'm attaching my autogenerated xorg.

---

### Post by detarmstrong on 2006-11-22
I found this How To to be better: 
[http://ubuntuforums.org/showthread.php?t=85769]("http://ubuntuforums.org/showthread.php?t=85769")

It helped me get TwinView working on my Dell Inspiron 9300 w/ Nvidia 6800 GO and DEll 2407 FWP monitor. DAPPER.

It also explains what some of those lines in the conf file mean. Very nice.

---

### Post by Ziox on 2006-11-22
> **detarmstrong said:**
> I found this How To to be better: 
[http://ubuntuforums.org/showthread.php?t=85769](http://ubuntuforums.org/showthread.php?t=85769)

It helped me get TwinView working on my Dell Inspiron 9300 w/ Nvidia 6800 GO and DEll 2407 FWP monitor. DAPPER.

It also explains what some of those lines in the conf file mean. Very nice.


I agree that guide provide better explaination of TwinView.  But what I provided is the bare minimum needed to enable TwinView.  If you wish view more and better explainations of the different options, then use the link I gave at the end of my guide.  It was very useful.

---

### Post by Shin_RockmanX on 2006-11-23
Hi,
thanks for the how-to.
I'm also having some trouble: 2 screens, 1 on VGA, 1 on DVI (in fact I use an adapter to convert it back to VGA).
The VGA screen is Ok, but on the other screen, it's written "out of frequency range 149.8kHz/335Hz.

Here is my .conf:

```

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600]"
	Driver		"nv"
	BusID		"PCI:4:0:0"
	Option "TwinView" "False"
	Option "TwinViewOrientation" "RightOf"   
	Option "UseEdidFreqs" "False"
    	Option "SecondMonitorHorizSync"   "UseEdidFreqs"
	Option "SecondMonitorVertRefresh" "UseEdidFreqs"
	Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
	Option "UseDisplayDevice" "CRT"
	Option "ConnectedMonitor" "CRT, CRT"
EndSection

```

Thanks

---

### Post by Ziox on 2006-11-23
> **Shin_RockmanX said:**
> Hi,
[COLOR=black][IMG]chrome://easygestures/skin/small_more.png[/IMG][IMG]chrome://easygestures/skin/small_bookmarkPage.png[/IMG][IMG]chrome://easygestures/skin/small_forward_gray.png[/IMG][IMG]chrome://easygestures/skin/small_nextTab_gray.png[/IMG][IMG]chrome://easygestures/skin/small_prevTab_gray.png[/IMG][IMG]chrome://easygestures/skin/small_closeTab.png[/IMG][IMG]chrome://easygestures/skin/small_back.png[/IMG][IMG]chrome://easygestures/skin/small_bookmarks.png[/IMG][IMG]chrome://easygestures/skin/small_menu.png[/IMG][/COLOR]
[COLOR=black][IMG]chrome://easygestures/skin/small_link.png[/IMG][IMG]chrome://easygestures/skin/matchCase_Off.png[/IMG][IMG]chrome://easygestures/skin/altMenuSign.png[/IMG][COLOR=black][IMG]chrome://easygestures/skin/contextMenuSign.png[/IMG][IMG]chrome://easygestures/skin/contextMenuSign.png[/IMG][/COLOR]
[/COLOR]
 thanks for the how-to.
I'm also having some trouble: 2 screens, 1 on VGA, 1 on DVI (in fact I use an adapter to convert it back to VGA).
The VGA screen is Ok, but on the other screen, it's written "out of frequency range 149.8kHz/335Hz.

Here is my .conf:

```

Section "Device"
    Identifier    "NVIDIA Corporation NV43 [GeForce 6600]"
    Driver        "nv"
    BusID        "PCI:4:0:0"
    Option "TwinView" "False"
    Option "TwinViewOrientation" "RightOf"   
    Option "UseEdidFreqs" "False"
        Option "SecondMonitorHorizSync"   "UseEdidFreqs"
    Option "SecondMonitorVertRefresh" "UseEdidFreqs"
    Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option "UseDisplayDevice" "CRT"
    Option "ConnectedMonitor" "CRT, CRT"
EndSection

```Thanks

You have some contradicting options enabled.  First of all, if you want to enable TwinView, then change the option "TwinView" to "true".
Then Change the options "UseEdidFreqs" to true as well.  As for your "SecondMonitor..." I suggest specifying a range. Such as the following values:

HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0

---

### Post by Shin_RockmanX on 2006-11-24
Allright,
Here is the new code
```
Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600]"
	Driver		"nv"
	BusID		"PCI:4:0:0"
	Option "TwinView" "True"
	Option "TwinViewOrientation" "RightOf"   
	Option "UseEdidFreqs" "True"
	Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
	Option "SecondMonitorHorizSync" "28.0-51.0"
	Option "SecondMonitorVertRefresh" "43.0-60.0"
	Option "UseDisplayDevice" "CRT"
	Option "ConnectedMonitor" "CRT, CRT"
EndSection
```

But it still doesn't work, and there's still a message on the second screen "Out of frequency range".

By the way, my second monitor wasn't detected automatically by Linux, do I have to add it in a Section "Monitor"??

---

### Post by Ziox on 2006-11-24
> **Shin_RockmanX said:**
> Allright,
Here is the new code
```
Section "Device"
    Identifier    "NVIDIA Corporation NV43 [GeForce 6600]"
    Driver        "nv"
    BusID        "PCI:4:0:0"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "RightOf"   
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option "SecondMonitorHorizSync" "28.0-51.0"
    Option "SecondMonitorVertRefresh" "43.0-60.0"
    Option "UseDisplayDevice" "CRT"
    Option "ConnectedMonitor" "CRT, CRT"
EndSection
```But it still doesn't work, and there's still a message on the second screen "Out of frequency range".

By the way, my second monitor wasn't detected automatically by Linux, do I have to add it in a Section "Monitor"??

what's the output for this command?

```
sudo ddcprobe
```

---

### Post by pentrant on 2006-11-26
FYI, I was able to get mine working with the following adjustment:

> Option "UseDisplayDevice" "CRT,DFP"

I also commented out the following line regarding the ConnectedMonitors, as it was redundant at that point.

Thanks for your guide!

---

### Post by Zorro on 2006-11-27
This is the only thing I should edit to get twinview happening right? I mean I dont have to set up the other monitor etc? As i recalled when I had this working before I did :? 

But with this only and the rest just standard.. I get only one screen love... 


Anyone know of why?

Ta..




Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    BusID           "PCI:2:0:0"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "RightOf"   
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option "SecondMonitorHorizSync" "28.0-51.0"
    Option "SecondMonitorVertRefresh" "43.0-60.0"
    Option "UseDisplayDevice" "CRT, CRT"
    #Option "ConnectedMonitor" "CRT, CRT"
EndSection

---

### Post by Ziox on 2006-11-27
> **Zorro said:**
> This is the only thing I should edit to get twinview happening right? I mean I dont have to set up the other monitor etc? As i recalled when I had this working before I did :? 

But with this only and the rest just standard.. I get only one screen love... 


Anyone know of why?

Ta..




Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    BusID           "PCI:2:0:0"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "RightOf"   
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option "SecondMonitorHorizSync" "28.0-51.0"
    Option "SecondMonitorVertRefresh" "43.0-60.0"
    Option "UseDisplayDevice" "CRT, CRT"
    #Option "ConnectedMonitor" "CRT, CRT"
EndSection

A bit more descriptive would be nice...but perhaps changing the resolutions via metmodes and the horizesync and vertrefresh rates might be the key

---

### Post by belshire on 2006-11-28
Hi thanks for the how-to it worked great.  I've run into one issue, while both of my monitors are working the one I would like to be my primary monitor is not.  I have a nVidia GeForce 6600GT card with two DVI ports, a ViewSonic 19" LCD, and an old 17" CRT going through a DVI to VGA dongle.  I've tried many things but can't get my LCD to be the primary monitor.  I should also note that the LCD had been my primary monitor before I went through the process of installing XGL and Beryl.

Here's some of my xorg.conf

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Monitor"
    Identifier     "VX924" #LCD Monitor Model Number, possibly the CRT is getting wrongly identified somehow?
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "LeftOf"
    Option         "UseEdidFreqs" "True"
    Option         "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option         "UseDisplayDevice" "LCD" 
    Option         "ConnectedMonitor" "LCD, LCD"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Monitor        "VX924"
    DefaultDepth    24

    # Enable 32-bit ARGB GLX Visuals
    Option "AddARGBGLXVisuals" "True"

    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x640" "640x480"
    EndSubSection
EndSection


```

---

### Post by marcinciel on 2006-11-29
Hi :)

IBM R50e + (VGA) LCD Belinea 101570

xorg.conf
> Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
        Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"   
Option "UseEdidFreqs" "True"
Option "MetaModes" "1024x768,1024x768"
Option "UseDisplayDevice" "CRT" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
Option "ConnectedMonitor" "CRT, CRT-1" #replace 'string' and 'strin-1' with either 'DFP' (Digital Flat Panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
    
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection



xorg.log
> (WW) I810(0): Bad V_BIOS checksum
(--) I810(0): A non-CRT device is attached to pipe B.
	No refresh rate overrides will be attempted.
(--) I810(0): Maximum space available for video modes: 12288 kByte
(II) I810(0): Using detected DDC timings
(II) I810(0): 	HorizSync 30-62
(II) I810(0): 	VertRefresh 50-75
(WW) I810(0): config file hsync range 28-51kHz not within DDC hsync range 30-62kHz
(WW) I810(0): config file vrefresh range 43-60Hz not within DDC vrefresh range 50-75Hz
*(WW) (1024x768,Generic Monitor) mode clock 94.5MHz exceeds DDC maximum 80MHz
(WW) I810(0): Option "TwinView" is not used
(WW) I810(0): Option "TwinViewOrientation" is not used
(WW) I810(0): Option "UseEdidFreqs" is not used
(WW) I810(0): Option "MetaModes" is not used
(WW) I810(0): Option "UseDisplayDevice" is not used
(WW) I810(0): Option "ConnectedMonitor" is not used


Help me please :oops:

---

### Post by belshire on 2006-11-29
> **marcinciel said:**
> Hi :)

IBM R50e + (VGA) LCD Belinea 101570

xorg.conf


xorg.log


Help me please :oops:


I'm no expert but try changing:
 Option "ConnectedMonitor" "CRT, CRT-1"
To:
 Option "ConnectedMonitor" "CRT, CRT"

You might want to try LCD for the second one also since your other monitor is an LCD.

---

### Post by marcinciel on 2006-11-29
:)

This same - don't work ](*,)

---

### Post by tronica on 2006-11-29
for anyone who this helps, all i have to do is just put 

Option  "twinview" to in the device section, and all is good.

---

### Post by Ziox on 2006-11-29
> **tronica said:**
> for anyone who this helps, all i have to do is just put 
 
Option "twinview" to in the device section, and all is good.
 
Wow, you must be one of the luckiest guy in the world...:evil: :-k

---

### Post by Quattr0 on 2006-11-30
Been struggling for hours to get Twinview working on my desktop system, running kubuntu dapper. Still no progress. I want to use two LCD-monitors, one through DVI and for the other one I have to use a VGA-to-DVI-adapter.
I have dual screen output when the computer is booting but when X starts it switches back to one monitor. So there's probably something wrong with my xorg.conf-settings but I can't figure out what exactly.

Anyone an idea what to do?
Here's my xorg.conf

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
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
	Option		"XkbLayout"	"be"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
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
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	Option          "NoLogo"
	Option          "Coolbits" "1"
	Option		"UseFBDev" "true"
	Option "TwinView" "1"
	Option "TwinViewOrientation" "RightOf"
	Option "UseEdidFreqs" "True"
	Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
	Option "UseDisplayDevice" "DFP"
	Option "ConnectedMonitor" "DFP, DFP"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"BenQ FP93GX"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"BenQ FP93GX"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
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
	Option          "Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by mojoman on 2006-12-01
I've been trying to get my projector working with TwinView without success and though I might have made some progress I would really appreciate if someone could help me out.

I've managed to - sort of - get the projector working and I have no problem with my regular monitor (a NEC LCD monitor). I've worked out that my monitor is CRT and the projector is DFP. However, if I enable the line ```
Option "ConnectedMonitor" "CRT, DFP"
``` I get 50% white screen, 50% black screen on both the monitor and the projector, and I have to login via my laptop to restore xorg.conf and restart the computor. (I've posted twice in this thread before, that's how I got this far...) 

My working xorg.conf (relevant parts) look like this:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "se"
EndSection

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

I autogenerated a xorg.conf with my projector running and I did get a working projector, though the edges of the screen wasn't visible and the fonts on the login screen looked weird (but not after login). The relevant parts look like this:
```

Section "Module"
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

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:7:0:0"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "RightOf"
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "1280x760,1024x768; 1024x768,1024x768"
    Option "ConnectedMonitor" "CRT, DFP"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
	Identifier	"Projector"
	Option		"DPMS"
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

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Projector"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x720" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x720" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x720" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x720" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x720" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x720" "640x480"
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
```

My feeble attempt to combine these to get a working xorg.conf look like this:
```

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	# Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:7:0:0"
	Option "NvAGP" "2"
	Option "NoLogo" "1"
	Option "RenderAccel" "0"
	Option "CursorShadow" "1"
	Option "Coolbits" "1"
	Option "UseDisplayDevice" "CRT,DFP"
	# Option "ConnectedMonitor" "CRT, DFP"
	Option "NoPowerConnectorCheck"
	Option "TwinView" "1"
	Option "TwinViewOrientation" "RightOf"
	Option "UseEdidFreqs" "True"
	Option "Metamodes" "1280x720,1024x768; 1024x768,1024x768; 800x600,800x600; 640x480,640x480; 1280x1024,NULL"
	Option "SecondMonitorHorizSync" "31.5-64.0"
	Option "SecondMonitorVertRefresh" "60.0-85.1"
	# Option "NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
	Identifier	"Projector"
	Option		"DPMS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
	Viewport 0 0
	Depth       1
	Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
	Viewport 0 0
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
	Viewport 0 0
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
	Viewport 0 0
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
	Viewport 0 0
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
	Viewport 0 0
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection

Section "ServerLayout"
	Identifier "TwinView Configuration"
	Screen 0 "Default Screen" 0 0
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	Option "Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

What am I doing wrong here? Is there anyone who could help me out? Any help towards getting me a working monitor and projector would be much appreciated :) 

Thanks
/Mojoman

---

### Post by bluevoodoo1 on 2006-12-02
I'm having an issue getting a picture on my second monitor. First monitor works fine. I can see that windows are opening, and the panel is stretching out to the blank monitor. It's getting a signal, though nothing I have tried has made it work... Both monitors work while in BIOS, so I'm certain it's a configuration problem. The screenshots explains it all. First one is with XGL, 2nd is without. The area to the left is not viewable through the monitor. It is as if there's a layer of black covering the screen... Under the screen resolution preferences it is giving me a resolution of 2240x900. I have a 7900 GS OC with 2 dvi inputs. 

xorg.conf

```
Section "Device"
	Identifier	"Nvidia 7990 GS OC"
	Driver		"nvidia"
	BusID		"PCI:8:0:0"
	Screen		0
	Option 		"TwinView" 
	Option 		"TwinViewOrientation" "LeftOf"   
	Option 		"UseEdidFreqs" "True"
	Option 		"UseDisplayDevice" "DFP, DFP" 
	Option 		"ConnectedMonitor" "DFP, DFP" 
	Option 		"SecondMonitorHorizSync" "30-82"
	Option 		"SecondMonitorVertRefresh" "56-70"
	Option 		"MetaModes" "1440x990,1440x990; 1440x990,1440x990"

	#Option 	"MetaModes" "1440x990,1440x990; 1440x990,1440x990"
	#Option		"RenderAccel"		"true"
	#Option		"AllowGLXWithComposite" "true"
	#Option 	"TwinView" "True"
	#Option 	"TwinViewOrientation" "LeftOf" 
	#Option 	"ConnectedMonitor" "dfp, dfp"
	#Option 	"MetaModes" "1440x990,1440x990"
 	#Option         "NoPowerConnectorCheck"
	#Option 	"UseDisplayDevice" "DFP"
	#Option		"NvAGP" "0"
	#Option 	"Coolbits" "1"
	#Option 	"UseEdidFreqs" "True"
	#Option 	"UseEDIDFreqs" "false"
	#Option 	"UseEDIDDpi" "true"
	#Option 	"UseEDID" "False"
	#Option		"ModeValidation" "NoEdidModes"
	#Option 	"ExtactModeTimingsDVI" "true"
	#Option 	"ModeValidation" "NoEdidDFPMaxSizeCheck, NoVesaModes"

EndSection


Section "Monitor"
	Identifier	"Acer AL1916W One"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen One"
	Device		"Nvidia 7990 GS OC"
	Monitor		"Acer AL1916W One"
	DefaultDepth	24
SubSection "Display"
		Depth		24
		Modes		"1440x990"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen One"
	#Screen		"Default Screen One" LeftOf "Default Screen Two"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "ServerFlags"
	Option "Xinerama" "False"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
          Option  "Composite" "Enable"
EndSection

```

similar xorg.conf with similar results (excuse all the comments...)
```

Section "Device"
	Identifier	"Nvidia 7900 GS OC"
	Driver		"nvidia"
	BusID		"PCI:8:0:0"
	Option 		"TwinView" "True"
	Option 		"TwinViewOrientation" "LeftOf"   
	Option 		"UseEdidFreqs" "True"
	Option 		"UseDisplayDevice" "DFP, DFP" 
	Option 		"ConnectedMonitor" "DFP, DFP" 
	Option 		"SecondMonitorHorizSync" "30-82"
	Option 		"SecondMonitorVertRefresh" "56-70"
	Option 		"MetaModes" "1440x990, 1440x990; 1440x990, 1440x990"

	#Option 	"MetaModes" "1440x990,1440x990; 1440x990,1440x990"
	#Option		"RenderAccel"		"true"
	#Option		"AllowGLXWithComposite" "true"
	#Option 	"TwinView" "True"
	#Option 	"TwinViewOrientation" "LeftOf" 
	#Option 	"ConnectedMonitor" "dfp, dfp"
	#Option 	"MetaModes" "1440x900,1440x900"
 	#Option         "NoPowerConnectorCheck"
	#Option 	"UseDisplayDevice" "DFP"
	#Option		"NvAGP" "0"
	#Option 	"Coolbits" "1"
	#Option 	"UseEdidFreqs" "True"
	#Option 	"UseEDIDFreqs" "false"
	#Option 	"UseEDIDDpi" "true"
	#Option 	"UseEDID" "False"
	#Option		"ModeValidation" "NoEdidModes"
	#Option 	"ExtactModeTimingsDVI" "true"
	#Option 	"ModeValidation" "NoEdidDFPMaxSizeCheck, NoVesaModes"

EndSection


Section "Monitor"
	Identifier	"Acer AL1916W One"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	56-76
EndSection

Section "Monitor"
	Identifier	"Acer AL1916W Two"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen One"
	Device		"Nvidia 7900 GS OC"
	Monitor		"Acer AL1916W One"
	DefaultDepth	24
SubSection "Display"
		Depth		1
		Modes		"1440x990" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x990" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x990" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x990" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x990" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x990" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Default Screen Two"
	Device		"Nvidia 7900 GS OC"
	Monitor		"Acer AL1916W Two"
	DefaultDepth	24
SubSection "Display"
		Depth		1
		Modes		"1440x990" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x990" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x990" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x990" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x990" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x990" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen One"
	Screen		"Default Screen One" LeftOf "Default Screen Two"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "ServerFlags"
	Option "Xinerama" "False"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
          Option  "Composite" "Enable"
EndSection


```

/var/log/Xorg.0.log referring to nvidia...
```
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen One" (0)
(**) |   |-->Monitor "Acer AL1916W One"
(**) |   |-->Device "Nvidia 7900 GS OC"
(**) |-->Screen "Default Screen One" (1)
(**) |   |-->Monitor "Acer AL1916W One"
(**) |   |-->Device "Nvidia 7900 GS OC"
(EE) Screen Default Screen Two doesn't exist: deleting placement
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP, DFP"
(**) NVIDIA(0): Option "UseEdidFreqs" "True"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "LeftOf"
(**) NVIDIA(0): Option "SecondMonitorHorizSync" "30-82"
(**) NVIDIA(0): Option "SecondMonitorVertRefresh" "56-70"
(**) NVIDIA(0): Option "MetaModes" "1440x990, 1440x990; 1440x990, 1440x990"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP, DFP"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     enabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): ConnectedMonitor string: "DFP, DFP"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(0): Unable to read EDID for display device DFP-1
(II) NVIDIA(0): NVIDIA GPU GeForce 7900 GS at PCI:8:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.71.22.42.01
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7900 GS at PCI:8:0:0:
(--) NVIDIA(0):     Acer AL1916W (DFP-0)
(--) NVIDIA(0):     DFP-1
(--) NVIDIA(0): Acer AL1916W (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Acer AL1916W (DFP-0): Internal Dual Link TMDS
(--) NVIDIA(0): DFP-1: 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-1: Internal Single Link TMDS
(II) NVIDIA(0): Option "UseDisplayDevice" "DFP" converted to "DFP-0, DFP-1".
(WW) NVIDIA(0): Unable to use mode "640x480" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "320x240" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "800x600" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "400x300" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "800x600" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "400x300" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1024x768" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "512x384" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1024x768" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "512x384" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1280x960" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "640x480" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1280x1024" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "640x512" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1600x1200" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "800x600" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1600x1200" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "800x600" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1280x768" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "640x384" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1280x800" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "640x400" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1400x1050" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "700x525" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1400x1050" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "700x525" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1440x900" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "720x450" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1600x1024" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "800x512" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1680x1050" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "840x525" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1920x1200" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "960x600" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "640x480" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "800x600" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "800x600" for DFP-1; cannot compute backend
(WW) NVIDIA(0):     DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1024x768" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1024x768" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1280x960" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1280x1024" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1600x1200" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(WW) NVIDIA(0): Unable to use mode "1600x1200" for DFP-1; cannot compute
(WW) NVIDIA(0):     backend DFP timings (no EDID).
(II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
(WW) NVIDIA(0): No valid modes for "1440x990,1440x990"; removing.
(WW) NVIDIA(0): No valid modes for "1440x990,1440x990"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 2240 x 900
(--) NVIDIA(0): DPI set to (89, 87); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.

```

---

### Post by Tim Prosser on 2006-12-04
I have a Twinview set up with "Clone" to try and duplicate the desktop onto a projector.

The projector has a resolution of 1280x720 and the desktop is a 1280x800 laptop screen.

I have the modelines set up fine, and I'm getting the right resolution on each device.


I would like the projector to show the top 720 pixels of the laptop screen.  This would show the Gnome panel only on the laptop.

Unfortunately, Gnome insists on moving the panel so that it shows on both displays.  It moves it up the laptop display to match the bottom of the projector.  I've tried "1280x720+0+80", "1280x800+0+0" for the display modes (and let Clone do its own thing) but it doesn't work.

Is there any way to avoid this behaviour?


PS What I would really like is to configure the laptop to switch displays like Windows on FnF5, but I've not heard of that being possible.

---

### Post by Webziz on 2006-12-05
> **Ziox said:**
> To: mojoman, Webziz
Try adding the following line to your "Device" Section:
```
Option "ConnectedMonitor" "DFP, CRT"
```You can try switching the DFP and CRT.

To Figgy:
nVidia Twinview only works on a SINGLE graphics card that supports dual-output. If you wish to utilize both graphics card, visit my Xinerama guide in a week or so. I'm adding support for two graphics card to that guide soon.

EDIT: No need to wait that long! Xinerama Guide has been updated!

That line did nothing. Picture still shows on both screens until x starts. Then it's only the main monitor. By using CRT on both options I got some kind of view on my 32" LCD, with a mouse pointer but no apparent indication of the system working correctly. By switching the order of DFP and CRT I got a black screen and no option of ctr+alt+backspace.

Any other ideas?

---

### Post by bobo1on1 on 2006-12-06
Does anyone know how to change the monitors around? I installed xubuntu and the login screen shows up on my tv which is connected to the vga port.
The "TwinViewOrientation" options has absolutely no effect, the placement changes but the login screen is still on the tv.

---

### Post by madcow on 2006-12-07
Hi guys,
I've just tried to enable TwinView editing the xorg file...but
how do I see if Dual Monitor is working?
I have a RIVA TNT 2 with a CRT and the VGA OUT is connected to  a TV!
thanks

---

### Post by legolas on 2006-12-07
[http://download.nvidia.com/solaris/1.0-8762/README/appendix-d.html](http://download.nvidia.com/solaris/1.0-8762/README/appendix-d.html)
is a difficult read.  If I got it straight, when you want to have a dual image , one on your monitor, and one on your tv, you should add 
Section "Device"
    Identifier     "NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
    Driver         "nvidia"
Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"   
Option "UseEdidFreqs" "True"
Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
Option "UseDisplayDevice" "TV"
Option "ConnectedMonitor" "CRT, TV"
EndSection

to your xorg.  Am I wrong?  I have a normal CRT flatscreen(i think) and want to pipe it to my tv also.  Is that set-up right?  I don"t understand what to put for "UseDisplayDevice" and "ConnectedMonitor"
I tried 
Option "UseDisplayDevice" "TV"
Option "ConnectedMonitor" "TV, TV"
and it went to the TV but unfortunately, my monitor went black.
Thanks for all your help!

---

### Post by chrisedu on 2006-12-07
hello folks

thx for these amazing tips... I am havin the following issue after installing and configuring nvidia drivers for a QuadroFX540 with dual monitor output ( CRT ).

even after editing the xorg.conf files ( followint these posts ), I just have one resolution available at "screen resolution" ( under system>preferences ): 2048x768.

Can't change the resolution... maybe some command at xorg.conf?



Section "ServerLayout"
*** Identifier**** "Default Layout"
*** Screen******** "Default Screen" 0 0 
*** InputDevice*** "Generic Keyboard"
*** InputDevice*** "Configured Mouse"
*** InputDevice*** "stylus" "SendCoreEvents"
*** InputDevice*** "cursor" "SendCoreEvents" 
*** InputDevice*** "eraser" "SendCoreEvents"
EndSection


Section "Monitor"
*** Identifier**** "Generic Monitor"
*** HorizSync****** 28.0 - 51.0
*** VertRefresh**** 43.0 - 60.0
*** Option******** "DPMS"
EndSection 

Section "Device"
*** Identifier**** "NVIDIA Corporation NV43GL [Quadro FX 540]"
*** Driver******** "nvidia"
Option "TwinView" "True"
Option "RenderAccel" "True" 
Option "TwinViewOrientation" "RightOf"* *
Option "UseEdidFreqs" "True"
Option "MetaModes" "1600x1200, 1600x1200"
Option "UseDisplayDevice" "CRT, CRT" 
Option "ConnectedMonitor" "CRT, CRT"
EndSection

Section "Screen"
*** Identifier**** "Default Screen"
*** Device******** "NVIDIA Corporation NV43GL [Quadro FX 540]" 
*** Monitor******* "Generic Monitor"
*** DefaultDepth*** 24
*** SubSection**** "Display"
******* Depth****** 1
******* Modes***** "1600x1200" "1024x768" "800x600" "640x480" 
*** EndSubSection
*** SubSection**** "Display"
******* Depth****** 4
******* Modes***** "1600x1200" "1024x768" "800x600" "640x480"
*** EndSubSection
*** SubSection**** "Display" 
******* Depth****** 8
******* Modes***** "1600x1200" "1024x768" "800x600" "640x480"
*** EndSubSection
*** SubSection**** "Display"
******* Depth****** 15
******* Modes***** "1600x1200" "1024x768" "800x600" "640x480"
*** EndSubSection
*** SubSection**** "Display"
******* Depth****** 16
******* Modes***** "1600x1200" "1024x768" "800x600" "640x480" 
*** EndSubSection
*** SubSection**** "Display"
******* Depth****** 24
******* Modes***** "1600x1200" "1024x768" "800x600" "640x480"
*** EndSubSection
EndSection 

thx for any help

---

### Post by majoridiot on 2006-12-07
it would help to post your xorg.0.log, chrisedu... but you might try replacing:

Option "UseEdidFreqs" "True"  

with

Option "UseEdidFreqs" "False"

if that doesn't fix it, post a copy of your xorg.0.log and what ver. of the nvidia driver you are using.

---

### Post by Robbyx on 2006-12-09
I chose Xinerama, had it working but then found the Terminal window would not open from within the GDM. Nvidia's conference suggested I try twinview, but I can not get it to work. The second screen does not show anything. It is black. Ub thinks its there and is putting items to the right of the working screen and I can not see them without dragging them to the main screen.

I am using the latest binary of the Nvidia driver on a GF 7600.

Robin

Xorg.conf:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)

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
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
	Option		"XkbVariant"	"dvorak"
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
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option "TwinView" "True"
        Option "TwinViewOrientation" "RightOf"   
        Option "UseEdidFreqs" "True"
        Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
        Option "UseDisplayDevice" "DFP,DFP" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
        Option "ConnectedMonitor" "DFP,DFP" #replace 'string' and 'strin-1' with either 'DFP' (Digital Flat Panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
	Option "SecondMonitorHorizSync" "30.0 - 83.0"
        Option "SecondMonitorVertRefresh" "55.0 - 75.0"
         # Option "NoTwinViewXineramaInfo"
         Option "UseEdidFreqs" "False"
EndSection

Section "Monitor"
	Identifier	"V7 P19S"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"V7 P19S"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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
```

This is the full xorg.0.log because I do not know what to edit out and I hoping you will also spot other problems:

```
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux robin-desktop 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Dec  9 16:48:47 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "V7 P19S"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) `fonts.dir' not found (or not valid) in "/usr/share/X11/fonts/misc".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/X11/fonts/misc").
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0308 card 1106,0308 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1308 card 1106,1308 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2308 card 1106,2308 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3208 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4308 card 1106,4308 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:5: chip 1106,5308 card 1106,5308 rev 00 class 08,00,20 hdr 80
(II) PCI: 00:00:7: chip 1106,7308 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1106,a208 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0f:0: chip 1106,0591 card 1106,0591 rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1106,0571 rev 07 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1106,3038 rev a0 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1106,3104 rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3337 card 1106,3337 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:7: chip 1106,287e card 1106,337e rev 00 class 06,00,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1043,80ed rev 7c class 02,00,00 hdr 00
(II) PCI: 00:13:0: chip 1106,337b card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 00:13:1: chip 1106,337a card 0000,0000 rev 00 class 06,04,01 hdr 01
(II) PCI: 02:00:0: chip 10de,0392 card 107d,2a52 rev a1 class 03,00,00 hdr 00
(II) PCI: 03:01:0: chip 1106,3288 card 1043,81b5 rev 10 class 04,03,00 hdr 00
(II) PCI: 04:04:0: chip 8086,1040 card 8086,1000 rev 00 class 07,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0007 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:2:0), (0,2,2), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf9000000 - 0xfbafffff (0x2b00000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:19:0), (0,3,3), BCTRL: 0x0007 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfbb00000 - 0xfbbfffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:19:1), (0,4,4), BCTRL: 0x0007 (VGA_EN is cleared)
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B]
(--) PCI:*(2:0:0) nVidia Corporation unknown chipset (0x0392) rev 161, Mem @ 0xfa000000/24, 0xd0000000/28, 0xf9000000/24, I/O @ 0xec00/7, BIOS @ 0xfbae0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B]
	[1] -1	0	0xfbbfc000 - 0xfbbfffff (0x4000) MX[B]
	[2] -1	0	0xf8ffb800 - 0xf8ffb8ff (0x100) MX[B]
	[3] -1	0	0xf8ffbc00 - 0xf8ffbcff (0x100) MX[B]
	[4] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[5] -1	0	0xfbae0000 - 0xfbafffff (0x20000) MX[B](B)
	[6] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[10] -1	0	0x0000c480 - 0x0000c49f (0x20) IX[B]
	[11] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[12] -1	0	0x0000c880 - 0x0000c89f (0x20) IX[B]
	[13] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[14] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[17] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[19] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B]
	[1] -1	0	0xfbbfc000 - 0xfbbfffff (0x4000) MX[B]
	[2] -1	0	0xf8ffb800 - 0xf8ffb8ff (0x100) MX[B]
	[3] -1	0	0xf8ffbc00 - 0xf8ffbcff (0x100) MX[B]
	[4] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[5] -1	0	0xfbae0000 - 0xfbafffff (0x20000) MX[B](B)
	[6] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[8] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[10] -1	0	0x0000c480 - 0x0000c49f (0x20) IX[B]
	[11] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[12] -1	0	0x0000c880 - 0x0000c89f (0x20) IX[B]
	[13] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[14] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[17] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[19] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B]
	[5] -1	0	0xfbbfc000 - 0xfbbfffff (0x4000) MX[B]
	[6] -1	0	0xf8ffb800 - 0xf8ffb8ff (0x100) MX[B]
	[7] -1	0	0xf8ffbc00 - 0xf8ffbcff (0x100) MX[B]
	[8] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[9] -1	0	0xfbae0000 - 0xfbafffff (0x20000) MX[B](B)
	[10] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[16] -1	0	0x0000c480 - 0x0000c49f (0x20) IX[B]
	[17] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[18] -1	0	0x0000c880 - 0x0000c89f (0x20) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[23] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[25] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[27] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B]
	[5] -1	0	0xfbbfc000 - 0xfbbfffff (0x4000) MX[B]
	[6] -1	0	0xf8ffb800 - 0xf8ffb8ff (0x100) MX[B]
	[7] -1	0	0xf8ffbc00 - 0xf8ffbcff (0x100) MX[B]
	[8] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[9] -1	0	0xfbae0000 - 0xfbafffff (0x20000) MX[B](B)
	[10] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[16] -1	0	0x0000c480 - 0x0000c49f (0x20) IX[B]
	[17] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[18] -1	0	0x0000c880 - 0x0000c89f (0x20) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[20] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[23] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[25] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[27] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B]
	[5] -1	0	0xfbbfc000 - 0xfbbfffff (0x4000) MX[B]
	[6] -1	0	0xf8ffb800 - 0xf8ffb8ff (0x100) MX[B]
	[7] -1	0	0xf8ffbc00 - 0xf8ffbcff (0x100) MX[B]
	[8] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[9] -1	0	0xfbae0000 - 0xfbafffff (0x20000) MX[B](B)
	[10] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[19] -1	0	0x0000c480 - 0x0000c49f (0x20) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[21] -1	0	0x0000c880 - 0x0000c89f (0x20) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[23] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[26] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[28] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[29] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[30] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP,DFP"
(**) NVIDIA(0): Option "UseEdidFreqs" "True"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "SecondMonitorHorizSync" "30.0 - 83.0"
(**) NVIDIA(0): Option "SecondMonitorVertRefresh" "55.0 - 75.0"
(**) NVIDIA(0): Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP,DFP"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     enabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): ConnectedMonitor string: "DFP,DFP"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS at PCI:2:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.16.68
(II) NVIDIA(0): Detected PCI Express Link width: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:2:0:0:
(--) NVIDIA(0):     VSN V7 P19S (DFP-0)
(--) NVIDIA(0):     Acer AL1715 (DFP-1)
(--) NVIDIA(0): VSN V7 P19S (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): VSN V7 P19S (DFP-0): Internal Dual Link TMDS
(--) NVIDIA(0): Acer AL1715 (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Acer AL1715 (DFP-1): Internal Single Link TMDS
(II) NVIDIA(0): Option "UseDisplayDevice" "DFP" converted to "DFP-0, DFP-1".
(II) NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024,1280x1024"
(II) NVIDIA(0):     "1024x768,1024x768"
(II) NVIDIA(0): Virtual screen size determined to be 2560 x 1024
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B]
	[8] -1	0	0xfbbfc000 - 0xfbbfffff (0x4000) MX[B]
	[9] -1	0	0xf8ffb800 - 0xf8ffb8ff (0x100) MX[B]
	[10] -1	0	0xf8ffbc00 - 0xf8ffbcff (0x100) MX[B]
	[11] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[12] -1	0	0xfbae0000 - 0xfbafffff (0x20000) MX[B](B)
	[13] -1	0	0xf9000000 - 0xf9ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] 0	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[23] -1	0	0x0000c480 - 0x0000c49f (0x20) IX[B]
	[24] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[25] -1	0	0x0000c880 - 0x0000c89f (0x20) IX[B]
	[26] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[27] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[29] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[30] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[31] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[32] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[33] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[34] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024,1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "XkbVariant" "dvorak"
(**) Generic Keyboard: XkbVariant: "dvorak"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+gb(dvorak)+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
```

---

### Post by Dayhawk1 on 2006-12-09
After many hours of frustration I found this to be the solution to my problem:


Section "Device"
	Identifier	"Nvidia Geforce 6800 GT"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option          "TwinView" "True"
	Option          "MetaModes" "1280x1024, 1280x1024"
EndSection

Section "Monitor"
	Identifier	"Viewsonic XV924"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	50-75
EndSection


I was using 2 identical monitors, one connected to my Geforce 6800 GT's DVI and the other to VGA.  I tried many many different configurations, all which failed and ended with me needing to use sudo dpkg-reconfigure xserver-xorg every time in restore mode.

I found that every time i used the above command that the default monitor that it displayed to was the monitor connected to my vga.  So then I decided to humor myself and not specify my monitors (contrary to every example I've found out on the web) and sure enough it worked.

Gotta love how the simplest things always work:D

---

### Post by Robbyx on 2006-12-10
If you are  passing by, could you please comment on my posting at #35. I can not spot what I have done wrong but twinview will not work at the moment.

Robin

---

### Post by Ziox on 2006-12-10
> **Robbyx said:**
> If you are  passing by, could you please comment on my posting at #35. I can not spot what I have done wrong but twinview will not work at the moment.

Robin

Do both of your monitors support 1280X1024 resolution?

---

### Post by Robbyx on 2006-12-10
Yes, they both support that resolution.

---

### Post by allyourzigg on 2006-12-10
Hello, I'm trying to set up twinview on both of my monitors, one CRT and one DFP and it will dsetect both but then say the other can't be found. Why is this? The video card I'm using is the nvidia 7950 GT and here are my xorg.conf and xorg.log files
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel" "true"
	Option		"TripleBuffer" "true"
	Option		"UseDisplayDevice" "DFP-1"
	Option		"TwinView" "true"
	Option		"TwinviewOrientation" "DFP-1 LeftOf CRT-0"
	Option		"MetaModes"	"1680x1050,1680x1050; 1440x900,1140x900; 1280x800,1280x800; 1024x640,1024x640; 1680x1050,NULL; 1440x900,NULL; 1280x800,NULL; 1024x640,NULL"	
	Option		"UseDisplayDevice" "DFP,CRT"
	Option		"NoPowerConnectorCheck"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	Option "AddARGBGLXVisuals" "true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by majoridiot on 2006-12-10
you need a monitor section and a screen section defining all of your 
monitors.  currently, you are defining only the dfp.  try adding monitor
and screen sections for your crt too.

---

### Post by majoridiot on 2006-12-10
> **Robbyx said:**
> I am using the latest binary of the Nvidia driver on a GF 7600....

your xorg log looks fine, so i bet this is a bug in the driver you are using.
there are many similar reports i've seen on the nvidia forums.  i suggest
reverting to 1.0-8776, as i know this works fine with twinview and a triple-
head setup.  if you want the latest (and possibly buggier) driver confirmed
to work with twinveiw, try 1.0-9629

downloads from nvidia are here: [http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html)

---

### Post by Robbyx on 2006-12-10
MI:

Thanks for that really useful reply re buggy drivers.

Robin

---

### Post by Robbyx on 2006-12-11
The cause of my problem turned out to be that my second monitor is  not digital although it is a flat screen. It has an analogue connector with a converter supplied by the card manufacturer. I changed the second monitor in the xorg.conf to crt and it worked.

```
Option "UseDisplayDevice" "DFP,CRT" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
```

Robin

I also changed the driver as suggested but that made no difference until I made the code alteration above.

---

### Post by mojoman on 2006-12-12
Hi,

I've been trying to configure TwinView for my nVidia 7600 GS for far to long now and I could really use some help. I'm using a monitor and a projector. The monitor and the projector works fine alone and I've autogenerated xorg.conf's to get the different values. I also merged these two xorg.conf, carefully noted what comes from which xorg.conf. 
This xorg.conf gives me a dual output on the login screen and I can move the mouse across both screens but as I login the signal to the projector dies.

The monitor is connected through the VGA and the projector is connected via HDMI from the DVI.
If I use Option ConnectedMonitors X crashes.
I've tried switsching UseEdidFreqs to False but there is no (visible) difference.

I'm attaching my xorg.conf. If anyone could give me some help I sure would appreciate it.

Best regards
/Mojoman

---

### Post by Webziz on 2006-12-12
Gotta up this problem, for It's pretty annoying to have high performance LCD with no ability to use it. 

I'm losing precious tv-time, and I wouldn't like to switch back to windows just to get my screen working properly.


> **Webziz said:**
> Looking for pointers here.

I'm trying to get my Samsung R32R72 32" HDTV to work alongside my Samsung LCD monitor. With my Radeon I managed to get some kind of signal to HDTV (@1024x768) at the same time as 1280x768 on my LCD.

Now, when the machine boots up, everything seems just nice on both the screens, but as soon as X starts up, tv goes blank, and lcd starts up just nicely. 

I'm completely at loss. Tried some different MetaModes, but Ubuntu doesn't seem to care.

Random facts: Using edgy, AGP Nvidia Geforce 7600GS, HDTV is connected on VGA and LCD on DVI.

Thank you, beforehand.


Important parts of xorg.conf:
....

---

### Post by Webziz on 2006-12-12
> **Webziz said:**
> Gotta up this problem, for It's pretty annoying to have high performance LCD with no ability to use it. 

I'm losing precious tv-time, and I wouldn't like to switch back to windows just to get my screen working properly.

I tinkered with the xorg.org a little... when I do this:

Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option "TwinView" "True"
        Option "TwinViewOrientation" "Clone"
#       Option "UseEdidFreqs" "True"

        Option "SecondMonitorHorizSync" "47.7"
        Option "SecondMonitorVertRefresh" "60"
        Option "MetaModes" "1360x768; 1280x1024, 1360x768; 1280x1024, 1024x768; 1024x768, 1024x768"


        #"1280x1024, 1360x768; 1280x1024, 1024x768; 1280x1024,1280x1024; 1024x768,1024x768"

#        Option "UseDisplayDevice" "DFP"
        #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is$        #Option "ConnectedMonitor" "DFP, CRT"

        #replace 'string' and 'strin-1' with either 'DFP' (Digital Flat Panel connected via DVI port), 'CRT' (any m$EndSection

both screens show the picture in 800x600 (wich is the first time I see something on my LCD). There are some disturbances on the main screen though.

And if I uncomment Option "UseEdidFreqs" "True" 32" lcd goes blank, and picture shows perfectly on my main screen. 

Any ideas?

---

### Post by yuv656 on 2006-12-12
Hello, I am running dapper and I couldn't get TwinView to work. I have a Geforce fx5200 with one dvi port and one analog port. I have 2 LCDs, both analog. The one is plugged into the DVI port with a DVI-Analog adapter.

Here's my xorg file:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option "NvAGP" "2"
	Option "RenderAccel" "0"
	Option "CursorShadow" "1"
	Option "Coolbits" "1"
	Option "ConnectedMonitor" "crt, dfp"
	Option "NoPowerConnectorCheck"
	Option "TwinView" "1"
	Option "Metamodes" "1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 800x600,800x600; 1024x768,1024x768; 1280x1024,NULL;1024x768,NULL"
	Option "SecondMonitorHorizSync" "31-82"
	Option "SecondMonitorVertRefresh" "56-76"
	# Option "NoTwinViewXineramaInfo"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Viewport 0 0
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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
	Option "Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by majoridiot on 2006-12-12
> **yuv656 said:**
> Hello, I am running dapper and I couldn't get TwinView to work. I have a Geforce fx5200 with one dvi port and one analog port. I have 2 LCDs, both analog. The one is plugged into the DVI port with a DVI-Analog adapter.


try identifying both monitors as crt. (crt,crt)... as any monitor with a vga
connection is regarded as a crt, regardless of where it is plugged.

optionally, you might try just commenting out that line entirely, as it
often not necessary to identify the monitors, but let them be autodetected.

---

### Post by yuv656 on 2006-12-12
I forgot to mention that I already tried that, to no avail

---

### Post by Cypfer on 2006-12-12
Greetings I followed the example and i can't get the second monitor to work.   My primary Monitor is unaffected but my second screen is nothing but bars and lines of different colours.  the card is a Pny verto Geforce 5200 dual VGA agp 8x it also has a TV port if that makes a different

also my ubuntu edition is 6.10

Thanks in advance for any help

**************here is the config file**************************************

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Option		"TwinView" "True"
	Option		"TwinViewOrientation" "RightOf"
	Option		"UseEdidFregs" "True"
	Option		"MetaModes" "1024x768,1024x768; 800x600,800x600"
	Option		"UseDisplayDevice" "CRT"
	Option		"ConnectedMonitor" "CRT, CRT"
EndSection

Section "Monitor"
	Identifier	"1777"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"1777"
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

---

### Post by majoridiot on 2006-12-12
> **yuv656 said:**
> I forgot to mention that I already tried that, to no avail

shooting in the dark, but i maybe it's a typo in your metamodes:

```
Option "Metamodes" "1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 800x600,800x600; 1024x768,1024x768; 1280x1024,NULL;1024x768,NULL" 
```

try:

```
Option "Metamodes" "1280x1024, 1280x1024; 1280x960, 1280x960; 1152x864, 1152x864; 800x600, 800x600; 1024x768, 1024x768; 1280x1024, NULL; 1024x768, NULL"
```

if that makes no difference, you need to post your Xorg.0.log so we can see
what's going on.

---

### Post by majoridiot on 2006-12-12
> **Cypfer said:**
> Greetings...

please post your Xorg.0.log, cypher.  it's almost impossible to help you
debug without seeing what's really happening.

:)

---

### Post by acegolfer on 2006-12-13
> **Dayhawk1 said:**
> After many hours of frustration I found this to be the solution to my problem:


Section "Device"
	Identifier	"Nvidia Geforce 6800 GT"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option          "TwinView" "True"
	Option          "MetaModes" "1280x1024, 1280x1024"
EndSection

Section "Monitor"
	Identifier	"Viewsonic XV924"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	50-75
EndSection


I was using 2 identical monitors, one connected to my Geforce 6800 GT's DVI and the other to VGA.  I tried many many different configurations, all which failed and ended with me needing to use sudo dpkg-reconfigure xserver-xorg every time in restore mode.

I found that every time i used the above command that the default monitor that it displayed to was the monitor connected to my vga.  So then I decided to humor myself and not specify my monitors (contrary to every example I've found out on the web) and sure enough it worked.

Gotta love how the simplest things always work:D

It worked for me too. I'm using Nvidia 6200 AGP card with 1 DVI and 1 VGA out. They are connected to 2 identical monitors (1280x1024). The simplest thing worked, where I tried to outsmart it. The key is to comment CRT, DFP line. I guess it confused the Nvidia card.

I'm also using Beryl and the cube rotates independently. I have 1 rotating cube for each monitor. It will be nicer to have 1 gigantic cube across 2 monitors rotating. 

Actually, I have done this before (by tweaking Nvidia control panel) but there is one big cost. Beryl now thinks the desktop space is 1 giant area. For example, if I maximize the window, it spans over 2 monitors, which is kinda pain. So I'm back to 2 somewhat independent spaces. Easier to move the windows around for me.

---

### Post by Cypfer on 2006-12-13
Here is the log file

is kind of long I'm not sure what part of it you want to look at so here is all of it 
Ps is in two parts cause of character limits
```


X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 x86_64 
Current Operating System: Linux Cypferlinux 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 13 20:18:24 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "1777"
(**) |   |-->Device "NVIDIA Corporation NV34 [GeForce FX 5200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,00e1 card 0000,0000 rev a1 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00e0 card 1458,0c11 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00e4 card 1458,0c11 rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00e7 card 1458,5004 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00e7 card 1458,5004 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00e8 card 1458,5004 rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:06:0: chip 10de,00ea card 1458,a002 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,00e5 card 1458,5002 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0a:0: chip 10de,00e3 card 1458,b002 rev a2 class 01,01,85 hdr 00
(II) PCI: 00:0b:0: chip 10de,00e2 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,00ed card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0322 card 196e,01ad rev a1 class 03,00,00 hdr 00
(II) PCI: 02:07:0: chip 12eb,0002 card 0101,0701 rev fa class 04,01,00 hdr 00
(II) PCI: 02:0b:0: chip 11ab,4320 card 1458,e000 rev 13 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf2000000 - 0xf3ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:14:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xf5ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x880fffff (0x100000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xf2000000/24, 0xe0000000/28
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf1ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf5040000 - 0xf5043fff (0x4000) MX[B]
	[1] -1	0	0xf5000000 - 0xf503ffff (0x40000) MX[B]
	[2] -1	0	0xf6001000 - 0xf6001fff (0x1000) MX[B]
	[3] -1	0	0xf6005000 - 0xf60050ff (0x100) MX[B]
	[4] -1	0	0xf6004000 - 0xf6004fff (0x1000) MX[B]
	[5] -1	0	0xf6003000 - 0xf6003fff (0x1000) MX[B]
	[6] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[10] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[11] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[14] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[15] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[16] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[17] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[20] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[21] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf5040000 - 0xf5043fff (0x4000) MX[B]
	[1] -1	0	0xf5000000 - 0xf503ffff (0x40000) MX[B]
	[2] -1	0	0xf6001000 - 0xf6001fff (0x1000) MX[B]
	[3] -1	0	0xf6005000 - 0xf60050ff (0x100) MX[B]
	[4] -1	0	0xf6004000 - 0xf6004fff (0x1000) MX[B]
	[5] -1	0	0xf6003000 - 0xf6003fff (0x1000) MX[B]
	[6] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[10] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[11] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[14] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[15] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[16] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[17] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[20] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[21] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf5040000 - 0xf5043fff (0x4000) MX[B]
	[5] -1	0	0xf5000000 - 0xf503ffff (0x40000) MX[B]
	[6] -1	0	0xf6001000 - 0xf6001fff (0x1000) MX[B]
	[7] -1	0	0xf6005000 - 0xf60050ff (0x100) MX[B]
	[8] -1	0	0xf6004000 - 0xf6004fff (0x1000) MX[B]
	[9] -1	0	0xf6003000 - 0xf6003fff (0x1000) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[16] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[17] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[20] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[21] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[22] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[23] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[26] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[27] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[28] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100
(II) Primary Device is: PCI 01:00:0
(--) Chipset GeForce FX 5200 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf5040000 - 0xf5043fff (0x4000) MX[B]
	[5] -1	0	0xf5000000 - 0xf503ffff (0x40000) MX[B]
	[6] -1	0	0xf6001000 - 0xf6001fff (0x1000) MX[B]
	[7] -1	0	0xf6005000 - 0xf60050ff (0x100) MX[B]
	[8] -1	0	0xf6004000 - 0xf6004fff (0x1000) MX[B]
	[9] -1	0	0xf6003000 - 0xf6003fff (0x1000) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[16] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[17] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[20] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[21] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[22] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[23] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[26] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[27] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[28] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf5040000 - 0xf5043fff (0x4000) MX[B]
	[5] -1	0	0xf5000000 - 0xf503ffff (0x40000) MX[B]
	[6] -1	0	0xf6001000 - 0xf6001fff (0x1000) MX[B]
	[7] -1	0	0xf6005000 - 0xf60050ff (0x100) MX[B]
	[8] -1	0	0xf6004000 - 0xf6004fff (0x1000) MX[B]
	[9] -1	0	0xf6003000 - 0xf6003fff (0x1000) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[20] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[23] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[24] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[25] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[26] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[27] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[28] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[29] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[30] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[31] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[32] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]

```

---

### Post by Cypfer on 2006-12-13
```
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce FX 5200"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xE0000000
(--) NV(0): MMIO registers at 0xF2000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules/libi2c.so
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...found one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: TTX  Model: 1777  Serial#: 73450
(II) NV(0): Year: 2004  Week: 36
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.631 redY: 0.329   greenX: 0.276 greenY: 0.600
(II) NV(0): blueX: 0.143 blueY: 0.057   whiteX: 0.283 whiteY: 0.297
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NV(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NV(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NV(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 94.5 MHz   Image Size:  310 x 230 mm
(II) NV(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) NV(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 56.2 MHz   Image Size:  310 x 230 mm
(II) NV(0): h_active: 800  h_sync: 832  h_sync_end 896 h_blank_end 1048 h_border: 0
(II) NV(0): v_active: 600  v_sync: 601  v_sync_end 604 v_blanking: 631 v_border: 0
(II) NV(0): Monitor name: 1777
(II) NV(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 72 kHz, PixClock max 110 MHz
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: OQI  Model: 4543  Serial#: 711
(II) NV(0): Year: 1999  Week: 52
(II) NV(0): EDID Version: 1.2
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NV(0): Signal levels configurable
(II) NV(0): Sync:  Separate  CompositeSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) NV(0): Max H-Image Size [cm]: horiz.: 29  vert.: 22
(II) NV(0): Gamma: 2.60
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): GTF timings supported
(II) NV(0): redX: 0.600 redY: 0.340   greenX: 0.280 greenY: 0.595
(II) NV(0): blueX: 0.150 blueY: 0.063   whiteX: 0.283 whiteY: 0.297
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 720x400@88Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@87Hz (interlaced)
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NV(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NV(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NV(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): #4: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #5: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 49.5 MHz   Image Size:  262 x 196 mm
(II) NV(0): h_active: 800  h_sync: 816  h_sync_end 896 h_blank_end 1056 h_border: 0
(II) NV(0): v_active: 600  v_sync: 601  v_sync_end 604 v_blanking: 625 v_border: 0
(II) NV(0): Serial No: CE95200711
(II) NV(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) NV(0): Monitor name: Q55-2
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 262144 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): 1777: Using default hsync range of 30.00-72.00 kHz
(II) NV(0): 1777: Using default vrefresh range of 50.00-160.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(WW) (1280x960,1777) mode clock 148.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(WW) (1280x1024,1777) mode clock 135MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(WW) (1280x1024,1777) mode clock 157.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(WW) (1600x1200,1777) mode clock 162MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,1777) mode clock 175.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,1777) mode clock 189MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,1777) mode clock 202.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,1777) mode clock 229.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(WW) (800x600,1777) mode clock 114.75MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1792x1344,1777) mode clock 204.8MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(WW) (1792x1344,1777) mode clock 261MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(WW) (896x672,1777) mode clock 130.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(WW) (1856x1392,1777) mode clock 218.3MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(WW) (1856x1392,1777) mode clock 288MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(WW) (928x696,1777) mode clock 144MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(WW) (1920x1440,1777) mode clock 234MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,1777) mode clock 117MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(WW) (1920x1440,1777) mode clock 297MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,1777) mode clock 148.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(WW) (1152x864,1777) mode clock 121.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(WW) (1400x1050,1777) mode clock 122MHz exceeds DDC maximum 110MHz
(WW) (1400x1050,1777) mode clock 151MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(WW) (1400x1050,1777) mode clock 155.8MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(WW) (1400x1050,1777) mode clock 184MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(WW) (1680x1050,1777) mode clock 147.14MHz exceeds DDC maximum 110MHz
(WW) (1920x1200,1777) mode clock 193.16MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(WW) (1920x1200,1777) mode clock 230MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(WW) (960x600,1777) mode clock 115MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(WW) (1920x1440,1777) mode clock 341.35MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,1777) mode clock 170.675MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(WW) (2048x1536,1777) mode clock 266.95MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(WW) (1024x768,1777) mode clock 133.475MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(WW) (2048x1536,1777) mode clock 340.48MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(WW) (1024x768,1777) mode clock 170.24MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(WW) (1024x768,1777) mode clock 194.02MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NV(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NV(0): Not using default mode "1152x768" (width too large for virtual size)
(--) NV(0): Virtual size is 1024x768 (pitch 1024)
(**) NV(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) NV(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) NV(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) NV(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) NV(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NV(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) NV(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) NV(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) NV(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0):  Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "840x525"   73.57  840 892 984 1128  525 525 527 543 doublescan
(**) NV(0):  Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "700x525"   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) NV(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) NV(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) NV(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) NV(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) NV(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) NV(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) NV(0):  Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) NV(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) NV(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) NV(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "512x384"   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "512x384"   39.40  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) NV(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) NV(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) NV(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) NV(0): Modeline "320x240"   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 332 352 416  240 244 245 260 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"   12.60  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) NV(0):  Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "360x200"   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync
(**) NV(0):  Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x200"   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync
(**) NV(0):  Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x175"   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync
(--) NV(0): Display dimensions: (320, 240) mm
(--) NV(0): DPI set to (81, 81)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[1] 0	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf5040000 - 0xf5043fff (0x4000) MX[B]
	[7] -1	0	0xf5000000 - 0xf503ffff (0x40000) MX[B]
	[8] -1	0	0xf6001000 - 0xf6001fff (0x1000) MX[B]
	[9] -1	0	0xf6005000 - 0xf60050ff (0x100) MX[B]
	[10] -1	0	0xf6004000 - 0xf6004fff (0x1000) MX[B]
	[11] -1	0	0xf6003000 - 0xf6003fff (0x1000) MX[B]
	[12] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[13] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[14] -1	0	0xf2000000 - 0xf2ffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[21] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[23] -1	0	0x0000e000 - 0x0000e07f (0x80) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[25] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[26] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[27] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[28] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x0000c000 - 0x0000c07f (0x80) IX[B]
	[31] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
	[32] -1	0	0x00002000 - 0x0000203f (0x40) IX[B]
	[33] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[34] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xe0000000,0x10000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(WW) NV(0): Option "TwinView" is not used
(WW) NV(0): Option "TwinViewOrientation" is not used
(WW) NV(0): Option "UseEdidFregs" is not used
(WW) NV(0): Option "MetaModes" is not used
(WW) NV(0): Option "UseDisplayDevice" is not used
(WW) NV(0): Option "ConnectedMonitor" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
```

---

### Post by majoridiot on 2006-12-14
look at the second chunk of your xorg.0.log, cypfer... it can't find a usable mode to run
that monitor in.

you can start by trying a change of:

```
Option "UseEdidFregs" "True"
```

to:

```
Option "UseEdidFregs" "False"
```

to force an ignore of the edids and see if that gets the second monitor running.

---

### Post by Cypfer on 2006-12-14
thanks for the tip....

humm nope didn't work. the log says that its finding the monitors and detecting them accuatly but after the second monitor it starts to fill a bunch of errors, the last code box details what the log shows

```
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...found one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: TTX  Model: 1777  Serial#: 73450
(II) NV(0): Year: 2004  Week: 36
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate

```
```
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...found one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: TTX  Model: 1777  Serial#: 73450
(II) NV(0): Year: 2004  Week: 36
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate

```

```
II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: OQI  Model: 4543  Serial#: 711
(II) NV(0): Year: 1999  Week: 52
(II) NV(0): EDID Version: 1.2
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NV(0): Signal levels configurable
(II) NV(0): Sync:  Separate  CompositeSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) NV(0): Max H-Image Size [cm]: horiz.: 29  vert.: 22
(II) NV(0): Gamma: 2.60
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): GTF timings supported
(II) NV(0): redX: 0.600 redY: 0.340   greenX: 0.280 greenY: 0.595
(II) NV(0): blueX: 0.150 blueY: 0.063   whiteX: 0.283 whiteY: 0.297
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 720x400@88Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@87Hz (interlaced)
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): Manufacturer's mask: 0
II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: OQI  Model: 4543  Serial#: 711
(II) NV(0): Year: 1999  Week: 52
(II) NV(0): EDID Version: 1.2
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NV(0): Signal levels configurable
(II) NV(0): Sync:  Separate  CompositeSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) NV(0): Max H-Image Size [cm]: horiz.: 29  vert.: 22
(II) NV(0): Gamma: 2.60
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): GTF timings supported
(II) NV(0): redX: 0.600 redY: 0.340   greenX: 0.280 greenY: 0.595
(II) NV(0): blueX: 0.150 blueY: 0.063   whiteX: 0.283 whiteY: 0.297
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 720x400@88Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@87Hz (interlaced)
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NV(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NV(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NV(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): #4: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #5: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 49.5 MHz   Image Size:  262 x 196 mm
(II) NV(0): h_active: 800  h_sync: 816  h_sync_end 896 h_blank_end 1056 h_border: 0
(II) NV(0): v_active: 600  v_sync: 601  v_sync_end 604 v_blanking: 625 v_border: 0
(II) NV(0): Serial No: CE95200711
(II) NV(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) NV(0): Monitor name: Q55-2

```
```
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 262144 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): 1777: Using default hsync range of 30.00-72.00 kHz
(II) NV(0): 1777: Using default vrefresh range of 50.00-160.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(WW) (1280x960,1777) mode clock 148.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(WW) (1280x1024,1777) mode clock 135MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(WW) (1280x1024,1777) mode clock 157.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(WW) (1600x1200,1777) mode clock 162MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,1777) mode clock 175.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,1777) mode clock 189MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,1777) mode clock 202.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,1777) mode clock 229.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(WW) (800x600,1777) mode clock 114.75MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(WW) (1792x1344,1777) mode clock 204.8MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(WW) (1792x1344,1777) mode clock 261MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(WW) (896x672,1777) mode clock 130.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "896x672" (hsync out of range)
:
(WW) (1856x1392,1777) mode clock 218.3MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(WW) (1856x1392,1777) mode clock 288MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(WW) (928x696,1777) mode clock 144MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(WW) (1920x1440,1777) mode clock 234MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,1777) mode clock 117MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(WW) (1920x1440,1777) mode clock 297MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,1777) mode clock 148.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(WW) (1152x864,1777) mode clock 121.5MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(WW) (1400x1050,1777) mode clock 122MHz exceeds DDC maximum 110MHz
(WW) (1400x1050,1777) mode clock 151MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(WW) (1400x1050,1777) mode clock 155.8MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(WW) (1400x1050,1777) mode clock 184MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(WW) (1680x1050,1777) mode clock 147.14MHz exceeds DDC maximum 110MHz
(WW) (1920x1200,1777) mode clock 193.16MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(WW) (1920x1200,1777) mode clock 230MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(WW) (960x600,1777) mode clock 115MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(WW) (1920x1440,1777) mode clock 341.35MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,1777) mode clock 170.675MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(WW) (2048x1536,1777) mode clock 266.95MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(WW) (1024x768,1777) mode clock 133.475MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(WW) (2048x1536,1777) mode clock 340.48MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(WW) (1024x768,1777) mode clock 170.24MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(WW) (1024x768,1777) mode clock 194.02MHz exceeds DDC maximum 110MHz
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NV(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NV(0): Not using default mode "1152x768" (width too large for virtual size)
(--) NV(0): Virtual size is 1024x768 (pitch 1024)
(**) NV(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) NV(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) NV(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) NV(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) NV(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NV(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) NV(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) NV(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz

```

---

### Post by majoridiot on 2006-12-15
> **Cypfer said:**
> thanks for the tip.... humm nope didn't work. 

try commenting out the usedisplay device and connectedmonitor settings and see what happens.

if that doesn't help, it may be necessary to explicitly define the frequencies you need.

---

### Post by nami on 2006-12-16
> **Ziox said:**
> [SIZE=4]**Dual Monitor With nVidia TwinView HowTo**[/SIZE]     [LEFT][FONT=Verdana]The following HowTo attempts to enable Dual Monitor support by using the TwinView function of the nVidia binary graphics driver.

 [/FONT][/LEFT]
        [LEFT][B][FONT=Verdana][SIZE=3]System Requirements:

[/SIZE][/FONT][/B][/LEFT]
    [LEFT][FONT=Verdana]A nVidia card with Dual output, whether it is VGA-DVI, VGA-VGA, or DVI-DVI.[/FONT][/LEFT]
    [LEFT][FONT=Verdana]Two Monitors (best if they are the same resolution, but different resolutions will work)[/FONT][/LEFT]
    [LEFT][FONT=Verdana]Installed and Working nVidia Binary graphics driver:[/FONT][/LEFT]
[INDENT][LEFT][FONT=Verdana]    Use the following link to install and enable the binary driver:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[/FONT][/LEFT]
[/INDENT][LEFT][B][FONT=Verdana][SIZE=3]Now get ready for some hardcore copy and pasting (not really).[/SIZE] ;)

[/FONT][/B][/LEFT]
        [LEFT][COLOR=Red]***[FONT=Verdana]1. Open Xorg.conf file by activating ONE of the following command (based on your distribution):[/FONT]***[/COLOR][/LEFT]
        [LEFT][FONT=Verdana]Gnome (Ubuntu):[/FONT][/LEFT]
    [LEFT]```
gksudo gedit /etc/X11/xorg.conf
```[/LEFT]
    [LEFT][FONT=Verdana]KDE (Kubuntu):[/FONT][/LEFT]
    [LEFT]```
kdesu kate /etc/X11/xorg.conf
```[/LEFT]
    [LEFT][FONT=Verdana]Xfce4 (Xubuntu):[/FONT][/LEFT]
    [LEFT]```
gksudo mousepad /etc/X11/xorg.conf
```[/LEFT]
    [LEFT][FONT=Verdana]Command-Line Based:[/FONT][/LEFT]
    [LEFT]```
sudo nano /etc/X11/xorg.conf
```[/LEFT]
        [LEFT][COLOR=Red]***[FONT=Verdana]2. Next navigate to your "Device" Section, which should appear similar to the example shown below, the identifier and BusID WILL be different:[/FONT]***[/COLOR][/LEFT]
    [LEFT]```
Section "Device"
    Identifier    "nVidia 7900"
    Driver        "nvidia"
    BusID        "PCI:1:5:0" 
EndSection
```***[FONT=Verdana][COLOR=Red]3. Add the following lines to that section:[/COLOR][/FONT]***[/LEFT]
    [LEFT]```
Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"   
Option "UseEdidFreqs" "True"
Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
Option "UseDisplayDevice" "string" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
Option "ConnectedMonitor" "string, string-1" #replace 'string' and 'strin-1' with either 'DFP' (Digital Flat Panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
```[/LEFT]

        [LEFT]**[FONT=Verdana]These codes are the bare minimum for enabling TwinView.  This should work most people, however, every system is configured differently, so use the following guide to add more options:[/FONT]**[/LEFT]
    [LEFT][FONT=Verdana][http://download.nvidia.com/solaris/1.0-8762/README/appendix-d.html]("http://download.nvidia.com/solaris/1.0-8762/README/appendix-d.html")

[/FONT][/LEFT]
        [LEFT][I][B][FONT=Verdana][COLOR=Red]4. Save the file, and restarted X (ctrl+alt+backspace), or reboot.

[/COLOR][/FONT][/B][/I][/LEFT]
        [LEFT][B][FONT=Verdana]You should now have TwinView :). If not, then just post the problem's symptoms, along with your xorg.conf file.

[/FONT][/B][/LEFT]
        [LEFT][COLOR=Red]**[FONT=Verdana]Good Luck! :)[/FONT]**[/COLOR][/LEFT]

How do you detect the BusID,  I forgot...

---

### Post by jooaakim on 2006-12-16
I'm trying to get this to work with my Samsung SyncMaster 913v and my newly purchased 32" LCD TV, Samsung LE32R72B.

I've got a GeForce 7600GT card so two DVI connections, both the monitor and the TV are connected via VGA -> DVI connectors though.

Doesn't seem to matter what changes I do in the conf, as soon as TwinView is activated it doesn't seem to output any kind of video to any of the images as both of them goes in to idle mode.

What am I doing wrong? I'm using the 9631 nvidia kernel if that could change anything, and Edgy of course.

xorg.conf:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Module"
#   Load           "ddc"
    Load           "i2c"
    Load           "bitmap"
    Load           "dbe"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "Monitor"
    Identifier     "SyncMaster"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce 7600GT"
    Driver         "nvidia"
     BusID "PCI:5:0:0"
     Option "TwinView" "Ture"
     Option "TwinViewOrientation" "RightOf"
     Option "UseEdidFreqs" "True"
     Option "MetaModes" "1360x768, 1280x1024; 1280x1024, 1360x768;1280x1024, 1024x768; 1024x768, 1280x1024; 1280x1024,1280x1024; 1024x768,1024x768"
     Option "UseDisplayDevice" "DFP" 
     Option "ConnectedMonitor" "DFP, CRT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 7600GT"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

```

---

### Post by nami on 2006-12-16
Hi

Having TwinView problems with my new computer.  I have configured beryl and it works nicely.  I am now trying to configure TwinView and I still only have 1 monitor working.

I have 2 tft monitors and a graphics card which has a vga and a dvi port, but am using a vga adapter on the graphics card for the dvi port of the graphics card because both my tft screens do not have dvi ability.

anyway here is my config and it does not work no errors no nothing, it just stays on a single monitor

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "AL1916"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6200?]"
    Driver         "nvidia"
    BusID          "PCI:5:0:0" 
    Option         "TripleBuffer" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6200?]"
    Monitor        "AL1916"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    Option "AddARGBGLXVisuals" "True"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "RightOf"   
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option "UseDisplayDevice" "CRT"
    Option "ConnectedMonitor" "CRT"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection



can anyone see anything wrong with my config file?

---

### Post by Storyman on 2006-12-16
> How do you detect the BusID, I forgot...

```
grep "PCI:" /var/log/Xorg.0.log
```

---

### Post by mojoman on 2006-12-17
Hi, 

After much worries I've finally configured my Hitachi projector using TwinView (I've posted several times in this thread). :D 

What I did was autogenerating two xorg.conf, one with my monitor and one with the projector. Having the correct values for the monitor and the projector I then merged these two xonrg.conf, which means I actually have two Monitor sections and two Screen sections in my new xorg.conf.

I the added thes lines under Device section

```
Option "TwinView" "True"
Option "TwinViewOrientation" "LeftOf"
Option "MetaModes" "1024x768,1280x720"
```

and edited a line in ServerLayout section to this (adding 0 0, God only knows why but I saw it in another xorg.conf and it works...)

```
Screen "Default Screen" 0 0
```

And thats it! I started with basically all the options from the HowTo but it crashed my X-server and I just couldn't figure out what caused it. I ended adding line after line instead, restarting X-server after each edit. Tedious as h*ll but when something crashed you now why. 

Hope this might help someone. Now I got some serious moviewatching to do! :cool: 

Best regards
/Mojoman

---

### Post by yuv656 on 2006-12-17
I got my TwinView to work by commenting out the ConnectedMonitor option and many other options that I thought might be unnecessary:

```
	Option "NvAGP" "2"
	#Option "RenderAccel" "0"
	#Option "CursorShadow" "1"
	#Option "Coolbits" "1"
	#Option "ConnectedMonitor" "crt, dfp"
	Option "NoPowerConnectorCheck"
	Option "TwinView" "True"
     	Option "TwinViewOrientation" "LeftOf"
     	#Option "UseEdidFreqs" "True"
	Option "Metamodes" "1280x1024, 1280x1024; 1024x768, 1024x768; 800x600, 800x600"
	#Option "SecondMonitorHorizSync" "31-82"
	#Option "SecondMonitorVertRefresh" "56-76"
	#Option "NoTwinViewXineramaInfo"
```

I also made my meta modes more basic. Now it works like a dream.

---

### Post by tazmon95 on 2006-12-17
Well After ready through this entire thread I've learned that I'm not alone with with these issues.  I've been trying to get this working and I'm SOOOOOOO Close.  I'm running two 6600GTs that I like to change back and forth from SLI mode to non-SLI to power 4 monitors, all are different kinds.  

For me I tried this HOW TO in the first post but it didn't like something, then I tried the Xinearama method and it kinda worked, but then I had an Idea.  When you use the nVidia X Server Settings GUI it lets me try to make changes and then looks like it's saving them... but then after you click save and restart gnome,  the settings didn't save.  Well what I finally did was copy the settings in that part that didn't save and apply them and it's working well except for one thing.  One of my 4 monitors is only displaying at 800x600 resolution.  I like to run all 4 at 1600x1200 normally.  Well here's my xorg:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Thu Nov  9 17:55:59 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" Above "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
	Option		"Emulate3Buttons"	"false"
	Option		"Buttons"		"7"
	Option		"ButtonMapping"		"1 2 3 6 7"

EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Dell ULTRASCANP990"
    HorizSync       30.0 - 96.0
    VertRefresh     48.0 - 120.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Daewoo 712D"
    HorizSync       30.0 - 95.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600 GT"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600 GT"
    BusID          "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
	Option		"UseEdidFreqs" "False"
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1600x1200 +0+0, CRT-1: nvidia-auto-select +1600+0; CRT-0: 1280x1024 +0+0, CRT-1: NULL; CRT-0: 1024x768 +0+0, CRT-1: NULL; CRT-0: 800x600 +0+0, CRT-1: NULL; CRT-0: 640x480 +0+0, CRT-1: NULL"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1600x1200 +0+0, CRT-1: 1600x1200 +1600+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```

No I'm pretty sure that my problem is coming from this monitor not being detected right.  When I try to detect it's settings using the nvidia gui, I get this ```
Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "@@@"
    HorizSync       30.0 - 96.0
    VertRefresh     48.0 - 120.0
    Option         "DPMS"
EndSection
```  I've been trying different things for this line ```
CRT-1: nvidia-auto-select 
```  but that's the only setting I've found where anything shows up on that screen.  So anyone have any thoughts on how to fix this?  Thanks

---

### Post by Xzallion on 2006-12-18
I got a Nvidia GeForce FX 5200 with a VGA, S-Video and standard CRT monitor out, and would like to get it to display to my monitor and my tv.  My monitor is the only display that shows anything at this moment.  I should also probably mention the tv is a standard old tv, not HD or anything. :(
The tv is connected using the VGA out.

Xorg

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Identifier	"Nvidia"
	Driver		"nvidia"
	BusID		"PCI:1:4:0"
	Option		"UseFBDev"		"True"
	Option 		"TwinView" 		"True"
	Option 		"TwinViewOrientation" 	"RightOf"   
	Option 		"UseEdidFreqs" 		"True"
	Option 		"MetaModes" 		"1024x768,1024x768; 800x600,800x600; 640x480, 640x480"
	Option 		"UseDisplayDevice" 	"CRT"
	Option 		"ConnectedMonitor" 	"CRT, TV"
EndSection

Section "Monitor"
	Identifier	"DELL E773c"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia"
	Monitor		"DELL E773c"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
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
```

and this thing

```
kenneth@ken-ubuntu:~$ grep "PCI:" /var/log/Xorg.0.log
(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2560 card 1028,0160 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2562 card 1028,0160 rev 01 class 03,80,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24c2 card 1028,0160 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1028,0160 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1028,0160 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1028,0160 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 1028,0160 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1028,0160 rev 01 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1028,0160 rev 01 class 04,01,00 hdr 00
(II) PCI: 01:04:0: chip 10de,0322 card 1b13,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 01:05:0: chip 14f1,2f20 card 14f1,200f rev 00 class 07,80,00 hdr 00
(II) PCI: 01:06:0: chip 13f6,0111 card 13f6,0111 rev 10 class 04,01,00 hdr 00
(II) PCI: 01:09:0: chip 14e4,4401 card 1028,8127 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(--) PCI: (0:2:0) Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 1, Mem @ 0xe0000000/27, 0xfeb80000/19
(--) PCI:*(1:4:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xfd000000/24, 0xf0000000/27, BIOS @ 0xfea00000/17
(II) OS-reported resource ranges after removing overlaps with PCI:
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:1:4:0
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:4:0:
kenneth@ken-ubuntu:~$ 

```

any and all help would be appreciated.

---

### Post by bzaks on 2006-12-18
Okay, I'm sure mine is simple:
I have a single card: GeForce 5600 with a CRT, TV and DFP output in that order from left to right
the CRT output is my usual one. I'm currently home, and I decided to hook up a monitor through my DFP port. I know it's a CRT but it's running through a hardware adapter and it's going in the DFP port.

Attached is my xorg file

I'm not sure if I'm doing anything wrong and any thoughts would be greatly appreciated! :)

Thanks!
Michael

---

### Post by yuv656 on 2006-12-19
@Xzallion:

Commenting or removing the ConnectedMonitor and UseDisplayDevice options in the Device section worked for me.

---

### Post by Xzallion on 2006-12-20
> **yuv656 said:**
> @Xzallion:

Commenting or removing the ConnectedMonitor and UseDisplayDevice options in the Device section worked for me.

Thanks yuv656!  It worked! :)

---

### Post by secular on 2006-12-20
> **yuv656 said:**
> I got my TwinView to work by commenting out the ConnectedMonitor option and many other options that I thought might be unnecessary:

```
	Option "NvAGP" "2"
	#Option "RenderAccel" "0"
	#Option "CursorShadow" "1"
	#Option "Coolbits" "1"
	#Option "ConnectedMonitor" "crt, dfp"
	Option "NoPowerConnectorCheck"
	Option "TwinView" "True"
     	Option "TwinViewOrientation" "LeftOf"
     	#Option "UseEdidFreqs" "True"
	Option "Metamodes" "1280x1024, 1280x1024; 1024x768, 1024x768; 800x600, 800x600"
	#Option "SecondMonitorHorizSync" "31-82"
	#Option "SecondMonitorVertRefresh" "56-76"
	#Option "NoTwinViewXineramaInfo"
```

I also made my meta modes more basic. Now it works like a dream.
I have the same video card and dual analog monitors. 

Would you mind posting your entire working xorg.conf ?

It would save me some time, and I'd really appreciate it.

---

### Post by fiztlen on 2006-12-27
Seem to be having similar troubles as others here.  I've been banging on xorg.conf and attached the current version if someone's willing to take a look.

I have a Geforce FX 5200 of unknown manufacturer (moving sale) with HD-25 and S-Video outs.  I don't know it's a factor, but my TV doesn't have an S-Video input, so I'm using my stereo to do the conversion.  I know that's not an issue because my DVD player is using the same configuration.

I've been working on a TwinView setup with an extended desktop, but not getting far.

I've also attached Xorg.0.log (split in 2), and these lines in particular have me confused:
```
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     Dell E173FP (CRT-0)
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): Dell E173FP (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(WW) NVIDIA(0): TwinView requested, but only 1 display devices found.
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): Invalid display device in Mode Description "TV-0:640x480"
(WW) NVIDIA(0): Not using mode description "TV-0:640x480"; unable to map to
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): Invalid display device in Mode Description "TV-0:640x480"
(WW) NVIDIA(0): Not using mode description "TV-0:640x480"; unable to map to
(WW) NVIDIA(0):     display device
(WW) NVIDIA(0): Invalid display device in Mode Description "TV-0:640x480"
(WW) NVIDIA(0): Not using mode description "TV-0:640x480"; unable to map to
(WW) NVIDIA(0):     display device
(WW) NVIDIA(0): Invalid display device in Mode Description "TV-0:640x480"
(WW) NVIDIA(0): Not using mode description "TV-0:640x480"; unable to map to
(WW) NVIDIA(0):     display device
(WW) NVIDIA(0): Invalid display device in Mode Description "TV-0:NULL"
(WW) NVIDIA(0): Not using mode description "TV-0:NULL"; unable to map to
(WW) NVIDIA(0):     display device
(WW) NVIDIA(0): No valid modes for "CRT-0:1280x1024,TV-0:640x480"; removing.
(WW) NVIDIA(0): Unable to find all display devices requested in TwinView
(WW) NVIDIA(0):     Orientation string "CRT-0 RightOf TV-0".
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT-0:1024x768,TV-0:640x480"
(II) NVIDIA(0):     "CRT-0:640x480,TV-0:640x480"
(II) NVIDIA(0):     "CRT-0:800x600,TV-0:NULL"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768 
```

It seems to me to be saying that it found the display device, but it didn't.  If I comment out ConnectedMonitor the Encoder and refresh lines vanish from the log. :confused: 


I'm sure I've done something stupid, but I think I'm still very nearly there.  If someone could point me to a good guide to the options (like what to start with and which section to put it in), I've not had much luck with Google.](*,) 

**Edit:** don't know if it's probitive, but nvida-xconfig --query-gpu-info yields this:
```
Number of GPUs: 1

GPU #0:
  Name      : GeForce FX 5200
  PCI BusID : PCI:1:0:0

  Number of Display Devices: 1

  Display Device 0 (CRT-0):
     EDID Name             : DELL E173FP
     Minimum HorizSync     : 31.000 kHz
     Maximum HorizSync     : 80.000 kHz
     Minimum VertRefresh   : 56 Hz
     Maximum VertRefresh   : 75 Hz
     Maximum PixelClock    : 140.000 MHz
     Maximum Width         : 1280 pixels
     Maximum Height        : 1024 pixels
     Preferred Width       : 1280 pixels
     Preferred Height      : 1024 pixels
     Preferred VertRefresh : 60 Hz
     Physical Width        : 340 mm
     Physical Height       : 270 mm
```
I'm a little concerned that this particular 5200 won't support two displays, but I had them both running at one point before.  Unfortunately the TV was crappy-looking and I tried some significant changes, and completely lost it (now I'm better with backups).

Thanks much

---

### Post by secular on 2006-12-27
I've now got TwinView working well with my Nvidia FX5200 and two LCD flat panel monitors.

I have one nagging problem, though. New windows open in the second monitor, but I'd like all windows to open in the primary monitor. The reason is that I use the second monitor only in certain situations and keep it off most of the time.

I know there's an answer to this, because I once fixed it on another install--I just can't remember  what I did to fix it. ](*,) 

Thanks to anyone who can help.

---

### Post by me_gustas on 2006-12-27
I want to have twin view with GeForce 5600 on a samsung LCD monitor (1280x1024) and LCD TV 1360x768. When I restart X only the TV is working -monitor has no signal- 1024x762. Can anybody help me? pls ](*,) 

> Section "Device"
	Identifier	"MVIDIA GeForce 5600"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	VideoRam	131072
Option "TwinView" "True"
Option "TwinViewOrientation" "LeftOf"
Option "UseEdidFreqs" "False"
Option "MetaModes" "1024x768,1360x768"
Option "UseDisplayDevice" "CRT, DFP"
Option "ConnectedMonitor" "DFP, CRT"
EndSection

---

### Post by ~LoKe on 2006-12-27
> **secular said:**
> I've now got TwinView working well with my Nvidia FX5200 and two LCD flat panel monitors.

I have one nagging problem, though. New windows open in the second monitor, but I'd like all windows to open in the primary monitor. The reason is that I use the second monitor only in certain situations and keep it off most of the time.

I know there's an answer to this, because I once fixed it on another install--I just can't remember  what I did to fix it. ](*,) 

Thanks to anyone who can help.

I'm pretty sure the new windows open in whichever screen your cursor is sitting in.

Here's my working **/etc/X11/xorg.conf**
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus"             "SendCoreEvents"
    InputDevice    "cursor"             "SendCoreEvents"
    InputDevice    "eraser"             "SendCoreEvents"
EndSection

Section "Files"
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules"           "xorg"
    Option         "XkbModel"           "pc104"
    Option         "XkbLayout"          "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/event9"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device"             "/dev/wacom"
    Option         "Type"               "stylus"
    Option         "ForceDevice"        "ISDV4"
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device"             "/dev/wacom"
    Option         "Type"               "eraser"
    Option         "ForceDevice"        "ISDV4"
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device"             "/dev/wacom"
    Option         "Type"               "cursor"
    Option         "ForceDevice"        "ISDV4"
EndSection

Section "Monitor"
    Identifier     "DELL 1907FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce 7900GS"
    Driver         "nvidia"
EndSection

Section "Screen"
        Identifier                      "Default Screen"
        Device                          "NVIDIA GeForce 7900GS"
        Monitor                         "DELL 1907FP"
        DefaultDepth                    24
        SubSection "Display"
                Depth                   24
                Modes                   "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        Option "TwinView"               "True"
        Option "TwinViewOrientation"    "RightOf"   
        Option "UseEdidFreqs"           "True"
        Option "MetaModes"              "1280x1024,1280x1024; 1024x768,1024x768"
        Option "UseDisplayDevice"       "DFP"
        Option "ConnectedMonitor"       "DFP, DFP"
        Option "AddARGBGLXVisuals"      "True"
EndSection
```

---

### Post by me_gustas on 2006-12-27
this is olso my Xorg.log. please advise me

> (II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP,CRT"
(**) NVIDIA(0): Option "UseEdidFreqs" "False"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "MetaModes" "1360x768,1024x768"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): ConnectedMonitor string: "DFP,CRT"
(WW) NVIDIA(0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5600 at PCI:2:0:0
(--) NVIDIA(0): VideoRAM: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.31.20.28.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5600 at PCI:2:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0):     IQT Q17 Digital (DFP-0)
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(--) NVIDIA(0): IQT Q17 Digital (DFP-0): 140.4 MHz maximum pixel clock
(--) NVIDIA(0): IQT Q17 Digital (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Option "UseDisplayDevice" "DFP" converted to "DFP-0".
(WW) NVIDIA(0): TwinView requested, but only 1 display devices found.
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): Invalid display device in Mode Description "1024x768"
(WW) NVIDIA(0): Not using mode description "1024x768"; unable to map to
(WW) NVIDIA(0):     display device
(WW) NVIDIA(0): No valid modes for "1360x768,1024x768"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(WW) NVIDIA(0): No size information available in DFP-0's EDID; cannot compute
(WW) NVIDIA(0):     DPI from EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(--) Depth 24 pixmap format is 32 bpp

---

### Post by secular on 2006-12-27
Thanks for replying LoKe, but my cursor is in my primary monitor's space when I click to open things, so I don't think that's the cause.

I'm running Edgy and have the 2.6.17.6-1 nvidia driver installed. My video card is an nvidia Geforce FX5200, my two monitors are LCD flat panels, and I'm using a converter for the DFI output to connect to my secondary monitor. Both monitors are CRT's.

Below is my xorg:

> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
#   Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
Identifier "SyncMaster"
Option "DPMS"
HorizSync 30-81
VertRefresh 56-75
EndSection

Section "Monitor"
Identifier "AOC"
Option "DPMS"
HorizSync 30-80
VertRefresh 55-75
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "RightOf"   
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option "UseDisplayDevice" "CRT"
    Option "ConnectedMonitor" "CRT, CRT" 
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by tribble222 on 2007-01-07
I have a DFT and a CRT and I wanted the DFT to be my primary display.  After hours of trying to get it to work I could never get the DFT to be my primary although it would work fine if I wanted my CRT to be the primary.  It turns out it's a limitation of the drivers - they only will detect the CRT first and if you tell them to detect the DFP with the UseDisplayDevice line then it won't find the CRT at all.

What you need to do is get the latest (1.0-9746) drivers and add the line:

Option "TwinViewXineramaInfoOrder" "DFP, CRT"

and comment out UseDisplayDevice and ConnectedMonitor.

This worked great for me and I hope it helps someone else!

---

### Post by mojoman on 2007-01-14
Hi,

I'm using TwinView with nVidia running on Dapper. I got one monitor and one projector configured and basically it's working good. However, there are some minor details that I really would need to tune in for it to be a perfect setup and I'm hoping for some advice.

When I launch an application it opens up on the monitor part of the screen, and that's good because the projector is usually turned off (unless I'm watching movies). However, if I launch another application in that workspace, this will usually launch in the projector part of the screen. Usually, I can just move it (right-clicking on the bar at the bottom of the screen) and move it to the screen I'm actually viewing but this is getting tedious (it doesn't matter in which screen the cursor is in when the applications is launched).

So, Question #1: Is there a TwinView option to make one part of the screen, i.e. the monitor part in my case, the default for applications to launch in?

Next item is that some applications spawn across both screen, making them impossible to use. This holds for some games like TuxRacer or Chromium but the same goes for the start-up screen on OpenOffice, though the OO-program itself launches neatly in one of the two screens. Now, I did not use the option “NoTwinViewXineramaInfo” and I think X-server could respect that but ... no. 

So, Question #2: is there some option opposite to NoTwinViewXineramaInfo (i.e. that forces all launched applications to open in just one of the two screens)?

Other than this, I've managed to get my TwinView to work very nice indeed but, still, I'd really appreciate if anyone could give me some help with this.

Best regards
/Mojoman

---

### Post by benyau on 2007-01-20
For default window location,  i.e. for setting the opening location (and other window attributes) in a workspace, you may want to try devil's pie.

[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)
[http://live.gnome.org/DevilsPie](http://live.gnome.org/DevilsPie)

---

### Post by benyau on 2007-01-20
I am found this one.  It seems a simpler solution.

[http://www.ubuntuforums.org/showthread.php?t=242502](http://www.ubuntuforums.org/showthread.php?t=242502)

cheers,
BY

---

### Post by crumbum on 2007-01-20
I would like to try and get the twinveiw working but the last time I tried it  my screen went black and I had no idea how to fix it .  I ended up having re do the system

---

### Post by crumbum on 2007-01-20
I just tried the code at the begging of this thread it changed my resolution on my primary monitor and I could see the screen on by tv for a few seconds unitl the desktop loaded

---

### Post by Spr0k3t on 2007-01-21
Thank you Ziox for your quick and dirty guide.  This worked like a charm on my system.  Running 3360x1050 now.

---

### Post by Spr0k3t on 2007-01-21
> **crumbum said:**
> I would like to try and get the twinveiw working but the last time I tried it  my screen went black and I had no idea how to fix it .  I ended up having re do the system

Next time before you make changes to the /etc/X11/xorg.conf, make sure you backup the file first so you don't have to reconfigure the xorg configuration.  I made that mistake once, but I was able to figure out how to fix it thanks to a second system.  When I make a backup of the file, I use a standard naming scheme which consists of <original filename>.bak.<year><month><day><hour><minute>.  When rebuilding the corrupted xorg.conf file I only needed to backup to the previous version doing a "cp" over the top of the incorrectly configured file.

---

### Post by jbayone on 2007-01-21
Yeah, this guide is awesome.  Everything worked the first time without having to change anything.

---

### Post by topgun553 on 2007-01-23
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 84.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce Go 6600]"
    Driver         "nvidia"
Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"   
Option "UseEdidFreqs" "True"
Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
Option "UseDisplayDevice" "string" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
Option "ConnectedMonitor" "string, string-1" #replace 'string' and 'strin-1' with either 'DFP' (Digital Flat Panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce Go 6600]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection


```

---

### Post by EvanPMeth on 2007-01-25
To get windows to stop maxamizing accross both string the only thing that is needed is to add 
```
Option "Xinerama" "true"
```
to where ever you define your metamodes. Either in the screen section or the video card device section
here is my xorg.conf (this is with a geforce 6200 dual output). I know i have extra crap, like extra screens but whatever it doesnt change anything. Bellow the break is for when i run single screen mode.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg



Section "Files"

	#FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	#FontPath	"/usr/share/X11/fonts/100dpi"
	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    Option         "DPMS"
#	HorizSync	28-72
#	VertRefresh	43-60
EndSection

Section "Monitor"
    Identifier     "External Monitor"
    Option         "DPMS"
#	HorizSync	28-72
#	VertRefresh	43-60
EndSection


Section "Device"
Identifier "Generic Video Card"
VideoRam 128000
VendorName "nVidia Corporation"
BoardName "Video device"
Driver "nvidia"
BusID "PCI:1:0:0"
Screen 1
Option "TwinView"
Option "MetaModes" "1280x1024, 1024x768; 1280x1024, NULL"
Option "TwinViewOrientation" "LeftOf"
**Option    "Xinerama" "true"**
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "External Screen"
    Device         "Generic Video Card"
    Monitor        "External Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "TWIN"
 #   Screen         "Default Screen" 0 0
 #   Screen         "External Screen" 0 0
    Screen "External Screen"
    Screen "External Screen" RightOf "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

#---------------------------------------------------
Section "Device"
Identifier "Videocard1"
VideoRam 128000
VendorName "nVidia Corporation"
BoardName "Video device"
Driver "nvidia"
BusID "PCI:1:0:0"
Screen 0
EndSection

Section "Screen"
    Identifier     "Screen 0"
    Device         "Videocard1"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection

Section "ServerLayout"
Identifier "SINGLE"
Screen 0 "Screen 0"
   InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

```

---

### Post by onlybui on 2007-01-25
Great Guide, but I had to go through each post, but I don't understand metamodes options. I got Twinview working but the screen resolution is set to 1 option which is 2048x768 and on CRT 0 the screen is shifted to left.
LG 37LC2D-UE (CRT-0) that supports 1024x768 1280x768 1360x768 1366x768 
(DELL 1702FP (CRT-1) that supports 1024x768 1280x1024
I'm using a evga geforce 7900GS that connects via VGA to DVI
How do I make my Dell LCD the primary and change metamodes to get the right resloution for both displays.
```
 Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option "TwinView" "True"
    #Option "TwinViewOrientation" "RightOf"   
    Option "UseEdidFreqs" "False"
    Option "MetaModes 0" "1366x768,1366x768;1024x768,1024x768"
    Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option "ConnectedMonitor" "CRT, CRT"
EndSection

```
```
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux fromroots 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 25 19:09:17 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5950 card 1462,7141 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 1002,5a34 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:11:0: chip 1002,437a card 1462,7141 rev 00 class 01,01,8f hdr 00
(II) PCI: 00:12:0: chip 1002,4379 card 1462,7141 rev 00 class 01,01,8f hdr 00
(II) PCI: 00:13:0: chip 1002,4374 card 1462,7141 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 1462,7141 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 1462,7141 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 1462,7141 rev 04 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 1462,7141 rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 1462,7141 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0292 card 3842,c624 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 1102,0002 card 1102,8027 rev 08 class 04,01,00 hdr 80
(II) PCI: 02:00:1: chip 1102,7002 card 1102,0020 rev 08 class 09,80,00 hdr 80
(II) PCI: 02:01:0: chip 109e,036e card 1822,0001 rev 11 class 04,00,00 hdr 80
(II) PCI: 02:01:1: chip 109e,0878 card 1822,0001 rev 11 class 04,80,00 hdr 80
(II) PCI: 02:03:0: chip 10ec,8139 card 1462,093c rev 10 class 02,00,00 hdr 00
(II) PCI: 02:04:0: chip 1106,3044 card 1462,093d rev 80 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfcffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:20:4), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0292) rev 161, Mem @ 0xfa000000/24, 0xd0000000/28, 0xfb000000/24, I/O @ 0xef00/7
(--) PCI: (2:1:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xfddff000/12
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI I/O resource overlap reduced 0x00004100 from 0x0000411f to 0x000040ff
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xffffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[1] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[2] -1	0	0xfddfe000 - 0xfddfefff (0x1000) MX[B]
	[3] -1	0	0xfe02a000 - 0xfe02a3ff (0x400) MX[B]
	[4] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[5] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[6] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[7] -1	0	0xfe02e000 - 0xfe02e1ff (0x200) MX[B]
	[8] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xfddff000 - 0xfddfffff (0x1000) MX[B](B)
	[11] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[15] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[16] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B]
	[17] -1	0	0x0000df00 - 0x0000df1f (0x20) IX[B]
	[18] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[19] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[20] -1	0	0x0000f500 - 0x0000f50f (0x10) IX[B]
	[21] -1	0	0x0000f600 - 0x0000f603 (0x4) IX[B]
	[22] -1	0	0x0000f700 - 0x0000f707 (0x8) IX[B]
	[23] -1	0	0x0000f800 - 0x0000f803 (0x4) IX[B]
	[24] -1	0	0x0000f900 - 0x0000f907 (0x8) IX[B]
	[25] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[26] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[27] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[28] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[29] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[30] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[1] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[2] -1	0	0xfddfe000 - 0xfddfefff (0x1000) MX[B]
	[3] -1	0	0xfe02a000 - 0xfe02a3ff (0x400) MX[B]
	[4] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[5] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[6] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[7] -1	0	0xfe02e000 - 0xfe02e1ff (0x200) MX[B]
	[8] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[9] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[10] -1	0	0xfddff000 - 0xfddfffff (0x1000) MX[B](B)
	[11] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[15] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[16] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B]
	[17] -1	0	0x0000df00 - 0x0000df1f (0x20) IX[B]
	[18] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[19] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[20] -1	0	0x0000f500 - 0x0000f50f (0x10) IX[B]
	[21] -1	0	0x0000f600 - 0x0000f603 (0x4) IX[B]
	[22] -1	0	0x0000f700 - 0x0000f707 (0x8) IX[B]
	[23] -1	0	0x0000f800 - 0x0000f803 (0x4) IX[B]
	[24] -1	0	0x0000f900 - 0x0000f907 (0x8) IX[B]
	[25] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[26] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[27] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[28] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[29] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[30] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[6] -1	0	0xfddfe000 - 0xfddfefff (0x1000) MX[B]
	[7] -1	0	0xfe02a000 - 0xfe02a3ff (0x400) MX[B]
	[8] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[9] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[10] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[11] -1	0	0xfe02e000 - 0xfe02e1ff (0x200) MX[B]
	[12] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[13] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[14] -1	0	0xfddff000 - 0xfddfffff (0x1000) MX[B](B)
	[15] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[21] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[22] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B]
	[23] -1	0	0x0000df00 - 0x0000df1f (0x20) IX[B]
	[24] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[25] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[26] -1	0	0x0000f500 - 0x0000f50f (0x10) IX[B]
	[27] -1	0	0x0000f600 - 0x0000f603 (0x4) IX[B]
	[28] -1	0	0x0000f700 - 0x0000f707 (0x8) IX[B]
	[29] -1	0	0x0000f800 - 0x0000f803 (0x4) IX[B]
	[30] -1	0	0x0000f900 - 0x0000f907 (0x8) IX[B]
	[31] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[32] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[33] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[34] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[35] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[36] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
	[37] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9746
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9746
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA dlloader X Driver  1.0-9746  Fri Dec 15 09:56:41 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(WW) Warning, couldn't open module wfb
(II) UnloadModule: "wfb"
(EE) Failed to load module "wfb" (module does not exist, 0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[6] -1	0	0xfddfe000 - 0xfddfefff (0x1000) MX[B]
	[7] -1	0	0xfe02a000 - 0xfe02a3ff (0x400) MX[B]
	[8] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[9] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[10] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[11] -1	0	0xfe02e000 - 0xfe02e1ff (0x200) MX[B]
	[12] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[13] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[14] -1	0	0xfddff000 - 0xfddfffff (0x1000) MX[B](B)
	[15] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[21] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[22] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B]
	[23] -1	0	0x0000df00 - 0x0000df1f (0x20) IX[B]
	[24] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[25] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[26] -1	0	0x0000f500 - 0x0000f50f (0x10) IX[B]
	[27] -1	0	0x0000f600 - 0x0000f603 (0x4) IX[B]
	[28] -1	0	0x0000f700 - 0x0000f707 (0x8) IX[B]
	[29] -1	0	0x0000f800 - 0x0000f803 (0x4) IX[B]
	[30] -1	0	0x0000f900 - 0x0000f907 (0x8) IX[B]
	[31] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[32] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[33] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[34] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[35] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[36] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
	[37] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[5] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[6] -1	0	0xfddfe000 - 0xfddfefff (0x1000) MX[B]
	[7] -1	0	0xfe02a000 - 0xfe02a3ff (0x400) MX[B]
	[8] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[9] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[10] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[11] -1	0	0xfe02e000 - 0xfe02e1ff (0x200) MX[B]
	[12] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[13] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[14] -1	0	0xfddff000 - 0xfddfffff (0x1000) MX[B](B)
	[15] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[24] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[25] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B]
	[26] -1	0	0x0000df00 - 0x0000df1f (0x20) IX[B]
	[27] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[28] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[29] -1	0	0x0000f500 - 0x0000f50f (0x10) IX[B]
	[30] -1	0	0x0000f600 - 0x0000f603 (0x4) IX[B]
	[31] -1	0	0x0000f700 - 0x0000f707 (0x8) IX[B]
	[32] -1	0	0x0000f800 - 0x0000f803 (0x4) IX[B]
	[33] -1	0	0x0000f900 - 0x0000f907 (0x8) IX[B]
	[34] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[35] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[36] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[37] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[38] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[39] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
	[40] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ConnectedMonitor" "CRT, CRT"
(**) NVIDIA(0): Option "UseEdidFreqs" "False"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): ConnectedMonitor string: "CRT, CRT"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7900 GS at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.71.22.42.04
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7900 GS at PCI:1:0:0:
(--) NVIDIA(0):     LG 37LC2D-UE (CRT-0)
(--) NVIDIA(0):     DELL 1702FP (CRT-1)
(--) NVIDIA(0): LG 37LC2D-UE (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): DELL 1702FP (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Devices: CRT-0, CRT-1
(WW) NVIDIA(0): No valid modes for "1280x1024,1280x1024"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768,1024x768"
(II) NVIDIA(0): Virtual screen size determined to be 2048 x 768
(--) NVIDIA(0): DPI set to (22, 30); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfdefe000 - 0xfdefe7ff (0x800) MX[B]
	[8] -1	0	0xfdeff000 - 0xfdeff0ff (0x100) MX[B]
	[9] -1	0	0xfddfe000 - 0xfddfefff (0x1000) MX[B]
	[10] -1	0	0xfe02a000 - 0xfe02a3ff (0x400) MX[B]
	[11] -1	0	0xfe02b000 - 0xfe02bfff (0x1000) MX[B]
	[12] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[13] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[14] -1	0	0xfe02e000 - 0xfe02e1ff (0x200) MX[B]
	[15] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[16] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[17] -1	0	0xfddff000 - 0xfddfffff (0x1000) MX[B](B)
	[18] -1	0	0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
	[19] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[20] -1	0	0xfa000000 - 0xfaffffff (0x1000000) MX[B](B)
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[24] 0	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B]
	[28] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[29] -1	0	0x0000de00 - 0x0000de07 (0x8) IX[B]
	[30] -1	0	0x0000df00 - 0x0000df1f (0x20) IX[B]
	[31] -1	0	0x0000f300 - 0x0000f30f (0x10) IX[B]
	[32] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[33] -1	0	0x0000f500 - 0x0000f50f (0x10) IX[B]
	[34] -1	0	0x0000f600 - 0x0000f603 (0x4) IX[B]
	[35] -1	0	0x0000f700 - 0x0000f707 (0x8) IX[B]
	[36] -1	0	0x0000f800 - 0x0000f803 (0x4) IX[B]
	[37] -1	0	0x0000f900 - 0x0000f907 (0x8) IX[B]
	[38] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[39] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[40] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[41] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[42] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[43] -1	0	0x0000ef00 - 0x0000ef7f (0x80) IX[B](B)
	[44] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
	[45] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[46] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768,1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(WW) NVIDIA(0): Option "MetaModes 0" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
```

USE sudo nvidia-settings to change screen res [RESLOVED]

---

### Post by crumbum on 2007-01-26
I have twin veiw working however the tv screen is in black and white.  And the res on the monitor is 1028x768 or so it says but it looks much larger than before.  Help

---

### Post by crumbum on 2007-01-28
I'm lost this is my x config file why wont twin view work.  It works up until the login screen and then nothing.  But the resolution is terrible black and white . Please help

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "hp f1703"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600]"
    Driver         "nvidia"
Option "TwinView" "true"
Option "TwinViewOrientation" "Clone"
Option "TVOutFormat" "SVIDEO"
Option "TVStandard" "NTSC-M"
Option "SecondMonitorHorizSync" "30-50"
Option "SecondMonitorVertRefresh" "60"
Option "MetaModes" "1280x1024,1280x1024,1024x768,1024x768;800x600,800x600;640x480,640x480;    512x384,512x384"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    Monitor        "hp f1703"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection

EndSection

---

### Post by Elpram on 2007-01-28
I've been trying to set up dual monitors on Ubuntu, but have had little luck.  One of the monitors is an LCD, the other  CRT, and I want to use the LCD as primary.  It seems however, that it either will only use my LCD and not recognize my CRT, or it will use my CRT as primary.  I've tried tons of things, and here is the relevant xorg info, maybe I'm missing something
```

Section "Monitor"
    Identifier     "Metro"
    Option         "DPMS"
EndSection


Section "Device"

#	Option		"UseFBDev"		"true"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    BusID		"PCI:1:0:0"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "RightOf"   
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "1680x1050_60, 1280x1024"
    Option "UseDisplayDevice" "DFP"
#    Option "ConnectedMonitor" "DFP, CRT"

EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Metro"
```

---

### Post by jyank on 2007-02-01
I am  having a similar problem, I have two monitors (20" CRT and 17" CRT) hooked up to my 7600GT connected via VGA-DVI connectors.  My problem is that it sees the 17" as the primary monitor, not the 20".  I do, however, have twinview working like this and I was able to work around this by dragging my desktop over to the 20" and adding the panels there, however, my problem lies when I try to play a game through wine or some other program.  The game will load on the 17" rather than the 20" and turn off the 20" until I exit the game/program.  Also, when I log into my system, the login screen is on the 17"

I would like to have the 20" as the primary, I've searched through these forums and google for days without finding a result.  here is my xorg

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 204.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
	Option "TwinView" "True"
	Option "TwinViewOrientation" "LeftOF"   
	Option "UseEdidFreqs" "True"
	Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768; 800x600 ,800x600; 640x480,640x480; 1280x1024"
	Option "UseDisplayDevice" "CRT, CRT" #replace 'string' 		with either 'DFP' (Digital flat panel connected via DVI 	port), 'CRT' (any monitor that is connected via VGA 	ports), or 'TV'
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "4094x4094" "2280x1425" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "4094x4094" "2280x1425" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "4094x4094" "2280x1425" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "4094x4094" "2280x1425" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "4094x4094" "2280x1425" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "4094x4094" "2280x1425" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

I have tried switching the UseDisplayDevice with various combinations, but nothing worked.  I have also tried commenting out usedisplaydevice and adding Option "TwinViewXineramaInfoOrder" "DFP, CRT" but that still didnt work

Thanks in advance

---

### Post by jtmedin on 2007-02-03
FYI Ref: nvidia geforce4 mx 4000, ubuntu 2.6.15-27-386
I spent a lot of time on other threads with no banana. Then followed your thread & installed the binaries like you sugested. Came back here & installed the appropiate from 3 in your post & WOW the lcd came right up. The crt is blank but thats ok. Thanks so much for your good work.

---

### Post by agentq on 2007-02-06
Hi,

I've got Twinview running fine on Edgy, thanks to this guide.  Unfortunately, the driver doesn't seem to support the native resolution of my second screen, a Sony 32" LCD TV, which is 1366x768.  The closest I've got is 1280x768, which looks a bit stretched and my DVDs play at slightly the wrong aspect but otherwise works fine.  When I use 1366x768 in the Metamodes option, the second screen goes blank and displays 'no signal'.  I've tried using Edid and without.  The same resolution works fine using the Windows NVidia driver.

Anyone know if it's meant to work or not?  Or if I have to do anything special to get it to accept this strange resolution?

Thanks for any help you can give,

- Neil

---

### Post by 0850 on 2007-02-10
hello, I have a Latptop with a Nvidia Geforce Go 7400 graphic card on which runs Ubuntu 6.10.
I have also an additional LCD Display and I would like to use them both in "DualView". (Not recognizing both but only using one at a time).
I installed and configured TwinView but at the moment only one at a time works, if the LCD is attached my Ubuntu runs on this, if not, it runs on the laptop screen.
I also find it surprising, that I don't have BusID's.

Attached my xorg
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load           "dbe" #für beryl
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "de"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"

        # 1280x800 @ 60.00 Hz (GTF) hsync: 49.68 kHz; pclk: 83.46 MHz
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    ModeLine       "1280x800_60.00" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
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
    Option         "XAANoOffscreenPixmaps" #beryl
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "UseEdidFreqs" "True"
    Option         "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option         "UseDisplayDevice" "DFP" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
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
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

I would be happy if anyone could help me :)

---

### Post by grusgraven on 2007-02-13
Hi I'm running a similar system, a laptop with a GeForce Go 7600, and i have now succeeded in setting up TwinView with a IBM P76 CRT (laptop res. 1200x800 CRT res 1280x1024). At first a manually added the BusID for the graphics card in xorg.conf (found the address in Xorg.log file and with lshw). From the Xorg.log file i was able to find the device names for the display devices  , in my case CMO or DFP-0 for the laptop, and CRT-0 for the CRT screen. After fiddling with some of the commands found in the nVidia [README]("http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/index.html") i got the system working with the following xorg settings:
```
ection "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    BusID        "PCI:1:0:0"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "LeftOf"   
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "CMO: 1280x800, CRT-0: 1280x1024"
    #Option "MetaModes" "1200x800,1280x1024; 1024x768,1024x768"
    #Option "UseDisplayDevice" "CRT-0,DFP-0" #replace 'string' with either 'DFP' eller 'CRT'
    #Option "ConnectedMonitor" "DFP-0, CRT-0"
    Option "TwinViewXineramaInfoOrder" "CRT-0,CMO"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1280x960" "1152x864" "1280x800"
    EndSubSection
EndSection
```

I have not yet been able to figure out how to set the laptop LCD as primary screen, but otherwise it works perfectly.

---

### Post by QuacoreZX on 2007-02-15
Hello hello

Well, I FINALLY got Twinview working (yay!) but it's on the wrong side,as in primary monitor is on right, secondary on left, and i'm quite used to the other way around (boo!).  I intend to switch this around, but it seems to be causing me quite a bit of trouble, and thus I'm posting here.  There is a couple oddities I should mention, however...

-the nvidia driver believes my DFP is a CRT.
-my primary monitor (in use) is actually connected to my secondary monitor port on accident.

With this in mind, I usually have to do a little bit of switching to get things how I like it, and...well...twinview has been less than helpful.  Normally, I would just change the

Option "UseDisplayDevice" "string"

from CRT to CRT-1, which is the identifier for my secondary monitor, but when i do that, CRT stops working entirely (no signal sent)!  Any idea what's going on here?  Well, here's the section of importance out of my xorg.conf anyways:

```
Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
	Option "TwinView" "True"
	Option "TwinViewOrientation" "LeftOf"   
	Option "SecondMonitorHorizSync"   "30-85"
	Option "SecondMonitorVertRefresh" "48-120"
	Option "MetaModes"   "1280x960, 1024x768"
	Option "UseDisplayDevice" "CRT" 
	Option "NoLogo" "TRUE"
EndSection
```

I hope you guys can help me out.  It's not a big problem right now, but it's rather inconvenient.  Oh, and one last thing.  If you guys know how to raise my refresh rate from 60hz to 75hz for both monitors, I'd be much obliged.  Thanks.

---

### Post by LukeKendall on 2007-02-17
> **allyourzigg said:**
> Hello, I'm trying to set up twinview on both of my monitors, one CRT and one DFP and it will dsetect both but then say the other can't be found. Why is this? The video card I'm using is the nvidia 7950 GT and here are my xorg.conf and xorg.log files
```

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"

```
...
```
	

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel" "true"
	Option		"TripleBuffer" "true"
	Option		"UseDisplayDevice" "DFP-1"
	Option		"TwinView" "true"
	Option		"TwinviewOrientation" "DFP-1 LeftOf CRT-0"
	Option		"MetaModes"	"1680x1050,1680x1050; 1440x900,1140x900; 1280x800,1280x800; 1024x640,1024x640; 1680x1050,NULL; 1440x900,NULL; 1280x800,NULL; 1024x640,NULL"	
	Option		"UseDisplayDevice" "DFP,CRT"
	Option		"NoPowerConnectorCheck"
EndSection


```
Your second "UseDisplayDevice" ("DFP,CRT") is actually the syntax for the option named "ConnectedMonitor".  I guess the first one is the only one being used.  Note also that  "UseDisplayDevice" is mutually exclusive with "ConnectedMonitor".  I suggest
commenting out "UseDisplayDevice".  (Something I read on a forum and used the tip to solve that problem in my setup.)   So try this:

```

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel" "true"
	Option		"TripleBuffer" "true"
	#Option		"UseDisplayDevice" "DFP-1"
	Option		"TwinView" "true"
	Option		"TwinviewOrientation" "DFP-1 LeftOf CRT-0"
	Option		"MetaModes"	"1680x1050,1680x1050; 1440x900,1140x900; 1280x800,1280x800; 1024x640,1024x640; 1680x1050,NULL; 1440x900,NULL; 1280x800,NULL; 1024x640,NULL"	
	Option		"ConnectedMonitor" "DFP, CRT"
	Option		"NoPowerConnectorCheck"
EndSection

```

luke

---

### Post by LukeKendall on 2007-02-17
> **Xzallion said:**
> I got a Nvidia GeForce FX 5200 with a VGA, S-Video and standard CRT monitor out, and would like to get it to display to my monitor and my tv.  My monitor is the only display that shows anything at this moment.  I should also probably mention the tv is a standard old tv, not HD or anything. :(
The tv is connected using the VGA out.

Xorg

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
```
...
```

Section "Device"
	Identifier	"Nvidia"
	Driver		"nvidia"
	BusID		"PCI:1:4:0"
	Option		"UseFBDev"		"True"
	Option 		"TwinView" 		"True"
	Option 		"TwinViewOrientation" 	"RightOf"   
	Option 		"UseEdidFreqs" 		"True"
	Option 		"MetaModes" 		"1024x768,1024x768; 800x600,800x600; 640x480, 640x480"
	Option 		"UseDisplayDevice" 	"CRT"
	Option 		"ConnectedMonitor" 	"CRT, TV"
EndSection

```

any and all help would be appreciated.

Comment out the "UseDisplayDevice" - it's mutually exclusive with the "ConnectedMonitor" option.

luke

---

### Post by LukeKendall on 2007-02-17
> **jyank said:**
> I am  having a similar problem, I have two monitors (20" CRT and 17" CRT) hooked up to my 7600GT connected via VGA-DVI connectors.  My problem is that it sees the 17" as the primary monitor, not the 20".  I do, however, have twinview working like this and I was able to work around this by dragging my desktop over to the 20" and adding the panels there, however, my problem lies when I try to play a game through wine or some other program.  The game will load on the 17" rather than the 20" and turn off the 20" until I exit the game/program.  Also, when I log into my system, the login screen is on the 17"

I would like to have the 20" as the primary, I've searched through these forums and google for days without finding a result.  here is my xorg

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig

```
...
```

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
	Option "TwinView" "True"
	Option "TwinViewOrientation" "LeftOF"   
	Option "UseEdidFreqs" "True"
	Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768; 800x600 ,800x600; 640x480,640x480; 1280x1024"
	Option "UseDisplayDevice" "CRT, CRT" #replace 'string' 		with either 'DFP' (Digital flat panel connected via DVI 	port), 'CRT' (any monitor that is connected via VGA 	ports), or 'TV'
EndSection



```

I have tried switching the UseDisplayDevice with various combinations, but nothing worked.  I have also tried commenting out usedisplaydevice and adding Option "TwinViewXineramaInfoOrder" "DFP, CRT" but that still didnt work

Thanks in advance

Try changing the "UseDisplayDevice" to  "ConnectedMonitor".

luke

---

### Post by mshelton on 2007-02-17
> **tribble222 said:**
> I have a DFT and a CRT and I wanted the DFT to be my primary display.  After hours of trying to get it to work I could never get the DFT to be my primary although it would work fine if I wanted my CRT to be the primary.  It turns out it's a limitation of the drivers - they only will detect the CRT first and if you tell them to detect the DFP with the UseDisplayDevice line then it won't find the CRT at all.

What you need to do is get the latest (1.0-9746) drivers and add the line:

Option "TwinViewXineramaInfoOrder" "DFP, CRT"

and comment out UseDisplayDevice and ConnectedMonitor.

This worked great for me and I hope it helps someone else!

Thanks for posting this, I've been working for quite a few hours trying to get the same setup to work.

With the new drivers and Option, it works perfectly.

---

### Post by tyros8000 on 2007-02-18
Hi,

I have an nvidia geforce4 Ti 4200 graphics card.

i want to hook up a 19" and 15" screen.  i have the main screen (19") working fine but want to put the 15" as a secondary screen at a resolution of 1024x768.  the 19" one is current at 1280x1024.

I have tried the first post code but it doesn't work, i am a beginner to linux and ubuntu and this is the only thing i haven't managed to config.  any help is much appreciated.

dave.

---

### Post by wataru on 2007-02-22
Thanks so much for this. The basic approach you outlined worked perfectly on the first try. This has actually been a decisive factor in causing me to choose Ubuntu as my default distro. 

Setup: nVidia 6800, Sony and Dell 17-inch flat-panel monitors, Dell Dimension 8400

---

### Post by addisor on 2007-02-28
I'd like LCD-15EX via VGA for desktop and Yamaha DXP-830 projector via DVI for films, here's my Xorg that's so nearly working, getting a bit muddled with CRT,DFP options and connected monitor options. Tried a few variations on this theme, both screens GRUB up and I have had both workihng seperatly. p.s its a mobo with integrated graphics and dual output.


Section "Device"
	Identifier	"NVIDIA GeForce 6150"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
	Option		"UseFBDev"		"true"
        Option "TwinView" "True"
        Option "TwinViewOrientation" "LeftOf"
	Option "UseEdidFreqs"           "True"
        Option "ConnectedMonitor"       "DFP,DFP"
        Option "MetaModes" "1024x768,1280x768,1280x720"
EndSection

Section "Monitor"
	Identifier	"LCD-15EX"
	Option		"DPMS"
	HorizSync	31.5-60.0
	VertRefresh	56.0-75.0
EndSection
Section "Monitor"
	Identifier	"Yamaha DPX-830"
	Option		"DPMS"
	HorizSync	28.13-45.0
	VertRefresh	50.0-60.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce 6150"
	Monitor		"LCD-15EX"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce 6150"
	Monitor		"Yamaha DPX-830"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x768" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen" 0 0 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by dgermann on 2007-03-03
Hi folks--

By following this Howto I got a long way down the road, but now I'm stuck. Hope someone can help me.

Running Dapper 6.06 LTS. Have a pc with an Intel D915GAV mobo. The monitors I have are a neovo F-419 (right, main screen) and Acer AL2016W. Both are flat panel screens.

Here is from the latest /var/log/Xorg.log file with the errors:
```

(==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar  3 19:42:22 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "TwinView Configuration"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "F-419"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card"
....
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce 7300 GS"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 0.8
(**) NV(0): Option "UseFBDev" "true"
(==) NV(0): Using HW cursor
(**) NV(0): Using framebuffer device
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
        compiled for 7.0.0, module version = 0.0.2
        ABI class: X.Org Video Driver, version 0.8
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) NV(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
        (you may have to look at the server log to see warnings)
(II) UnloadModule: "nv"
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules/libvgahw.so
(II) UnloadModule: "int10"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
(END)

```

Here is my xorg.conf:
```

Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nv"
	# Driver		"nvideo"
	BusID		"PCI:1:0:0"
BoardName 	"GeForce 7300 GS"
Option 		"NvAGP" "2"
Option 		"NoLogo" "1"
Option 		"RenderAccel" "0"
Option 		"CursorShadow" "1"
Option 		"Coolbits" "1"
Option 		"DisplayDevice" "dfp, crt"
Option 		"NoPowerConnectorCheck"
Option 		"TwinView" "1"
Option 		"Metamodes" "NULL,1680x1050;NULL,1600x1200;1280x1024,1280x1024;1024x768,1024x768;800x600,800x600;640X480,640x480;1280x1024,NULL;1024x768,NULL; 800x600,NULL"
Option 		"SecondMonitorHorizSync" "31-84"
Option 		"SecondMonitorVertRefresh" "56-86"
# Option 	"NoTwinViewXineramaInfo"
Option "TwinViewXineramaInfoOrder" "DFP-0"

	Option		"UseFBDev"		"true"
	# Option "TwinView" "True"
	Option "TwinViewOrientation" "RightOf"   
	Option "UseEdidFreqs" "True"
	# Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
	# Option "UseDisplayDevice" "DFP" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
EndSection

#Section "Device"
#	Identifier	"1 Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
#	Driver		"i810"
#	BusID		"PCI:0:2:0"
#	Screen		1
#EndSection

Section "Monitor"
	Identifier	"F-419"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

#Section "Monitor"
#	Identifier	"1 AL2016W"
#	Option		"DPMS"
#	HorizSync	31-84
#	VertRefresh	56-86
#EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"F-419"
	# Monitor		"Monitor"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		1
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		4
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		8
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		15
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		16
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	# Identifier	"Default Layout"
	# Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
Identifier "TwinView Configuration"
Screen 0 "Default Screen" 0 0
Option "Xinerama" "Off"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Can anybody suggest what I should try next to trouble shoot this? :confused: 

Thanks!

---

### Post by acconrad on 2007-03-04
My setup:
-Dell Latititude D800 w/ nVidia GeForce FX Go5650
-Dell UltraSharp 20'' (CRT connection)

I did everything on here and I can get dual monitor to work on the LOGIN screen for Ubuntu Edgy but the moment the actual GNOME session runs the dual monitor goes away...and oddly enough it thinks my primary monitor is the Dell UltraSharp and not my laptops monitor...any ideas?

---

### Post by dgermann on 2007-03-04
Hi--

OK, have made some progress. I hope.

First, I commented-out the line in the xorg.conf like this:
```

 # Option                "UseFBDev"              "true"

```

Now I finally got into X--on one screen only. This is the screen I have for my main screen, the F-419 Neovo. The other screen simply reports "Input not supported." Both screens showed the scrolling boot-up process till it got to the X login screen. Then the main screen had some zig-zag lines across the bottom half of the screen, then I got the login screen.

Here are some clues from the /var/log/Xorg.0.log file, being all the error messages:

```

...
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
...
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : No such file or directory

```

I'm guessing that only the first one is the problem.

What next? I would like to get the second screen working....

Thanks!

---

### Post by glabouni on 2007-03-05
**WARNING: using this command autmatically backup current xorg.conf to '/etc/X11/xorg.conf.backup' overwriting any previous /etc/X11/xorg.conf.backup keep this in mind when naming your backup file**

what about using the provided nvidia-xconfig command ? as in :

Enable TwinView:
```
sudo nvidia-xconfig --twinview
```
Ddisable Twinvies
```
sudo nvidia-xconfig --no-twinview
```
      Enable Xinerama.
```
sudo nvidia-xconfig --xinerama
```
      Disable Xinerama.
```
sudo nvidia-xconfig --no-xinerama
```

simpler, easier, smarter, less painful

for a complete list of available parameters: 
```
nvidia-xconfig -A 
```

---

### Post by Nikron on 2007-03-05
This is how my device section looks and it works perfectly..  I tried the OP's configuration but it didn't work for me..  

Note:  obviously only two lines apply to TwinView..  And I'm using feisty so TwinView may have been upgraded..
```
Section "Device"
    Identifier "Device0"
    Driver "nvidia"
    Option "TwinView" "True"
    Option "MetaModes" "1024x768,1024x768"
    Option         "AddARGBGLXVisuals" "True"
    Option         "DisableGLXRootClipping" "True"
EndSection
```

---

### Post by n1tro on 2007-03-05
Got a quick question someone may be able to help me with. I got 2 19" LCDs (exact same models) connected and got the Twinview going.  My problem is most of the time when I boot up, the monitor connected to the VGA port looks like crap. By crap, I mean the resolution is not sharp and/or the resolution is not the same as the LCD connected to the DVI port. Sometimes when I fool around with the xorg.conf file and do a quick reboot (ALT CTRL+BACKSPACE), the LCD on the VGA looks as sharp as the other one and in the same resolution but this goes away if I do another reboot. Please help me out. Here is the relevant settings I have in xorg.conf  Thanks!

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"

Section "Monitor"
    Identifier     "Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "LeftOf"
    Option         "UseEdidFreqs" "True"
    #Option         "MetaModes" "2880x900,1440x900,1280x1024,1280x1024;2880x900,1440x900,1024x768,1024x768"
    #Option         "UseDisplayDevice" "DFP, CRT"
    Option         "ConnectedMonitor" "DFP, DFP"

EndSection

Section "Screen"
    Identifier     "Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    DefaultDepth    24
        SubSection     "Display"
        Depth       24
        Modes      "2880x900" "1440x900" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection

EndSection

---

### Post by dgermann on 2007-03-05
n1tro--

Just an off the wall guess--does it maybe "think" the one connected to the VGA port is a CRT? If you tried
Option "ConnectedMonitor" "DFP, CRT"
would that make any difference?

I know less than nothing about this--still trying to get mine going for a second screen at all, but that is something I saw in your setup that caught my eye.

---

### Post by n1tro on 2007-03-05
Having option "ConnectedMonitor" as...

"DFP, DFP" ---> DFP screen good.  VGA screen crap
"DFP, CRT" ---> DFP screen good, VGA screen crap
"CRT, DFP" ---> DFP screen good, VGA screen crap
"CRT, CRT" ---> DFP screen blank, VGA screen good

I know there must be something I'm missing because once in awhile both DFP and VGA are crystal clear!

---

### Post by n1tro on 2007-03-05
Well I # out the modes line under the Screen section and everything is working fine!! Seems the less you put into the xorg.conf the better.

---

### Post by joey on 2007-03-05
FWIW,

The instructions didn't work for me.

I used nvidia-xconfig --twinview and it worked great!  Here is my section:

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800 Ultra/GeForce 6800 GT]"
    Monitor        "Apple Cinema"
    DefaultDepth    24
    Option         "TwinView" "True"
    Option         "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    Option       "TwinViewOrientation" "LeftOf"
    SubSection     "Display"

```

---

### Post by dgermann on 2007-03-07
Hi all--

Joy! Got it working.

Thanks to glabouni and k0fcc for suggesting the nvidia-xconfig --twinview command. It worked for me and now I have two screens.

Now I need help with some (maybe one) tweak. I can only get one screen resolution, 2048x768, under System > Preferences > Screen Resolution. I would like to get something with a bit smaller type size.

I tried (twice, as you can see below) doing nvidia-xconf --mode=1600x1200 and still I only get 2048x768.

Also, and this might be related, the neovo F-419 looks a little yellowish when it is showing a white background.

Third worry: The xorg.conf file now shows only one set of refresh rates, the ones for the Acer Al2016W. The ones for the F-419 should be H 30-65 (this xorg.conf sets both at 31-84) and V 50-75 (xorg.conf set at 56-86). Should something be changed here to keep the screens safe?

Relevant portions of my xorg.conf file:
```
Section "Monitor"
    Identifier     "AL2016W"
    HorizSync       31.0 - 84.0
    VertRefresh     56.0 - 86.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
    Monitor        "AL2016W"
    DefaultDepth    24
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "UseEdidFreqs" "True"
    Option         "MetaModes" "1024x768, 1024x768"
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1600x1200" "1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1600x1200" "1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1600x1200" "1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1600x1200" "1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1600x1200" "1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1600x1200" "1680x1050" "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

So what do I do to change my screen resolution, and do I need to worry about the Horiz and Vert refresh rates?

---

### Post by Temis on 2007-03-10
Trying to get twin view working. OS Edgy. Graphics XFX Geforce MX 4000.
Installed nvidia-glx. No problem. Edited as follows:

Section "Device"
Identifier   "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x].
Driver       "nvidia"
Option      "NoLogo"

ADDED THESE OPTIONS:

Option  "TwinView" "True"
Option  "UseEdidFregs" "False"
Option  "TwinViewOrientation" "Clone"
Option  "TVOutFormat" "SVIDEO"
Option   "TVStandard" "NTSC-M"
Option  "SecondMonitorHorizSync" "30-50"
Option  "SecondMonitorVertRefresh" "60"
Option  "metaModes"  "1024x768, 1024x768; 800x600,800x600;640x480, 640x480;
512x384,512x384"
Option  "UseDisplayDevice"  "CRT,TV"
End of Section
 

Saved edit and restarted. Disaster: The display on TV set showed the ubuntu log on
the computer monitor was black. I rebooted in safe mode trying to edit the nvidia configuration.
No Luck:
root@name-desktop:~# gksudo gedit /etc/xorg.conf



(gksudo:4239):Gtk-WARNING **: cannot open display

Question what did I wrong in first place, how do I edit in command display?

---

### Post by Ziox on 2007-03-13
> **Temis said:**
> Trying to get twin view working. OS Edgy. Graphics XFX Geforce MX 4000.
Installed nvidia-glx. No problem. Edited as follows:

Section "Device"
Identifier   "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x].
Driver       "nvidia"
Option      "NoLogo"

ADDED THESE OPTIONS:

Option  "TwinView" "True"
Option  "UseEdidFregs" "False"
Option  "TwinViewOrientation" "Clone"
Option  "TVOutFormat" "SVIDEO"
Option   "TVStandard" "NTSC-M"
Option  "SecondMonitorHorizSync" "30-50"
Option  "SecondMonitorVertRefresh" "60"
Option  "metaModes"  "1024x768, 1024x768; 800x600,800x600;640x480, 640x480;
512x384,512x384"
Option  "UseDisplayDevice"  "CRT,TV"
End of Section
 

Saved edit and restarted. Disaster: The display on TV set showed the ubuntu log on
the computer monitor was black. I rebooted in safe mode trying to edit the nvidia configuration.
No Luck:
root@name-desktop:~# gksudo gedit /etc/xorg.conf



(gksudo:4239):Gtk-WARNING **: cannot open display

Question what did I wrong in first place, how do I edit in command display?

You can't start a GUI application in a virtual terminal (since X is has not started).  In order to edit the file use:

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by intinig on 2007-03-13
> **tribble222 said:**
> 
Option "TwinViewXineramaInfoOrder" "DFP, CRT"


This is the single best advice for those having problems with device recognition.

---

### Post by Skeorx13 on 2007-03-13
I'm on Ubuntu 6.10 and I have two LCD monitors on an XFX GeForce 7600 gt XXX PCI-E card. One is 19" DVI (which I'm using as my primary screen) and the other is a 15" VGA plugged into a VGA>DVI adapter plug. The 19" is a ViewEra V192WD with max resolution of 1280x1024, Horizontal at 30-81 KHz, and Vertical at 55-75 Hz. The 15" is a KDS rad5 with max res of 1024x768, Horizontal at 30-60 KHz, and Vertical at 55-75 Hz. I ganked some code from my brother's setup (who is far more experienced than I with Linux) and tweaked my way through this thread. I got my monitors to work in twinview, but with a slight problem. The largest graphics mode I can get to is 2304x1024. Problem is my 15" monitor can only support 1024x768. So 256 pixels at the bottom of my small screen (ie the bottom task bar thingy) is cut off. I was curious if someone could recommend an edit to my xorg.conf file to correct the resolution so I am not losing this space (without messing with the Viewera 19" monitor's resolution. I was also wondering if there was a way to split the screens into two separate and individual desktops (like using the tabs at the bottom right corner to switch between them or what have you. I'd really like to have to separate desktop backgrounds (but isn't all that vital as I'm pretty comfortable with my graphical editing skills to make a wide spanning background file that merely incorporates two "individual" jpgs). This seemed WAY easier to setup in windows, but I'm sure that the Linux way is far more tweakable to personal preference... I'm also not sure if the display subsections for depth 1-16 are necessary, but they were in the file I got from my brother so I didn't want to delete something that could possibly have an ill effect. I also have a problem with the login screen having an overly large resolution. The sides scroll when I move my mouse off the screen. I don't understand why it would do that as the metamodes are not above 1280x1024. Anyone that can help me or edit my file to be more efficient and/or organized would be great too. 

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen [0]" 0 0
    Screen      1  "Default Screen [1]" RightOf "Default Screen [0]"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Radius [0]"
    Option         "DPMS"
    HorizSync	   30-60
    VertRefresh	   55-75
EndSection

Section "Monitor"
    Identifier     "ViewEra [1]"
    Option         "DPMS"
    HorizSync	   30-81
    VertRefresh	   55-75
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card0"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen	   0
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card1"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen	   1
EndSection

Section "Screen"
    Identifier     "Default Screen [0]"
    Device         "NVIDIA Corporation NVIDIA Default Card0"
    Monitor        "Radius [0]"
    DefaultDepth    24
    Option         "Twinview" "True"
    Option         "TwinViewOrientation" "LeftOf"
    Option         "SecondMonitorHorizSync" "30-81"
    Option         "SecondMonitorVertRefresh" "55-75"
    Option         "NvAGP" "1"
    Option         "HWCursor" "0"
    Option         "SWCursor" "1"
    Option         "NoLogo" "False"
    Option         "RenderAccel" "True"
    Option         "MetaModes" "1280x1024,1024x768; 1024x768,1280x1024; 1280x1024,1280x1024; 1152x864,1152x864; 1024x768,1024x768; 832x624,832x624; 800x600,800x600; 720x400,720x400; 640x480,640x480; 1280x1024,null; 1152x684,null; 1024x768,null; 832x624,null; 800x600,null; 720x400,null; 640x480,null"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Default Screen [1]"
    Device         "NVIDIA Corporation NVIDIA Default Card1"
    Monitor        "ViewEra [1]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection



---

### Post by Temis on 2007-03-14
> **Ziox said:**
> You can't start a GUI application in a virtual terminal (since X is has not started).  In order to edit the file use:

```
sudo nano /etc/X11/xorg.conf
```
Thank you for the information.

How do I save the edited file? Just exit? Is it possible to print text of the virtual terminal?
I googled but could not find "how to" for the virtual terminal.

Option "UseEdidFregs" "False" , what does is do? Do I need it?

---

### Post by Skeorx13 on 2007-03-14
Well I figured out a few tweaks and edited my xorg.conf file a bit. I got my smaller monitor to pan into the dead space so I can at least view it. But is there a way to squish the screen instead so I don't have to pan down to see it, but without messing with anything on the larger screen? I also got my taskbars split between the two monitors so I can position things along the inside screen split. But the backgrounds are still not able to be set independently. (I can edit a full background in gimp to fit properly if need be, but being able to set them separately would be more desired.) 

> 
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen [0]" 0 0
    Screen      1  "Default Screen [1]" RightOf "Default Screen [0]"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option	   "Buttons" "5"
    Option         "ZAxisMapping" "4 5"
    Option	   "ButtonMapping" "1 2 3 6 7"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Radius [0]"
    Option         "DPMS"
    HorizSync	   30-60
    VertRefresh	   55-75
EndSection

Section "Monitor"
    Identifier     "ViewEra [1]"
    Option         "DPMS"
    HorizSync	   30-81
    VertRefresh	   55-75
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card0"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen	   0
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card1"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen	   1
EndSection

Section "Screen"
    Identifier     "Default Screen [0]"
    Device         "NVIDIA Corporation NVIDIA Default Card0"
    Monitor        "Radius [0]"
    DefaultDepth    24
    Option         "Twinview" "True"
    Option         "TwinViewOrientation" "LeftOf"
    Option         "SecondMonitorHorizSync" "30-81"
    Option         "SecondMonitorVertRefresh" "55-75"
    Option         "NvAGP" "1"
    Option         "HWCursor" "0"
    Option         "SWCursor" "1"
    Option         "NoLogo" "False"
    Option         "RenderAccel" "True"
    Option         "MetaModes" "1024x768 @1024x1024,1280x1024; 1280x1024,1280x1024; 1024x768,1024x768; 832x624,832x624; 800x600,800x600; 720x400,720x400; 640x480,640x480; 1280x1024,null; 1152x684,null; 1024x768,null; 832x624,null; 800x600,null; 720x400,null; 640x480,null"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Default Screen [1]"
    Device         "NVIDIA Corporation NVIDIA Default Card1"
    Monitor        "ViewEra [1]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by yodenss on 2007-03-15
I pieced this together from various bits of this thread, wanted to put it all in one place.  It should probably go in the first post, since trying DFP as primary causes twinview to just fail miserably.

Since CRTs are detected first, xorg/twinview will only work properly with the CRT as the first monitor.  We can get around this by configuring the device section of xorg.conf as:

```

     Option "TwinView" "True"
     Option "TwinViewOrientation" "RightOf"   #primary right of secondary
     Option "TwinViewXineramaInfoOrder" "DFP, CRT"
     Option "ConnectedMonitor" "CRT,DFP"
     Option "MetaModes" "1280x1024 ,1920x1200; NULL,1920x1200" #configure for your monitors

```

My xorg.conf was generated with the DFP connected.  YMMV.
----
I'm not sure the trick works with KDE apps.  Amarok still displays its splash on the CRT (minor issue).

---

### Post by acconrad on 2007-03-16
can someone help me?  i find this one REALLY strange...i can actually get dual monitor view on the LOGIN screen but the moment it loads the main OS gnome manager it reverts back to a single monitor!

i'm running a Dell Latitude D800 laptop screen w/ a Dell Ultrasharp 20'' CRT. 

here's the relevant code to my current xorg.conf file:

```

Section "Device"
    Identifier     "NVIDIA GeForce FX Go5650"
    Driver         "nvidia"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "RightOf"   #primary right of secondary
    Option "TwinViewXineramaInfoOrder" "DFP, CRT"
    Option "ConnectedMonitor" "CRT,DFP"
    Option "MetaModes" "1280x1024 ,1280x800; NULL,1280x800"
EndSection

Section "Screen"

# Enable 32-bit ARGB GLX Visuals
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce FX Go5650"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
# If you are using an older version of compiz that
    Option         "DisableGLXRootClipping" "True"
    Option         "UseFBDev" "true"
    Option         "NvAGP" "2"
    Option         "NoLogo" "1"
    Option         "RenderAccel" "0"
    Option         "CursorShadow" "1"
    Option         "Coolbits" "1"
    Option         "NoPowerConnectorCheck"
    Option         "SecondMonitorHorizSync" "28-64"
    Option         "SecondMonitorVertRefresh" "43-60"
	# Option "NoTwinViewXineramaInfo"
    Option         "TripleBuffer" "true"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option 	   "TwinViewXineramaInfoOrder" "DFP, CRT"
    Option         "Connected Monitor" "CRT,DFP"
    Option         "UseEdidFreqs" "True"
    Option         "MetaModes" "1280x1024, 1280x800; NULL,1280x800"
EndSection

```

any help?

anyone?

---

### Post by Skeorx13 on 2007-03-16
> **acconrad said:**
> can someone help me?  i find this one REALLY strange...i can actually get dual monitor view on the LOGIN screen but the moment it loads the main OS gnome manager it reverts back to a single monitor!

i'm running a Dell Latitude D800 laptop screen w/ a Dell Ultrasharp 20'' CRT. 

here's the relevant code to my current xorg.conf file:

any help?

anyone?
What resolution did you select your screens to be set to in the GUI? For mine, I had to set the meta modes up and then select the combined metamode in the GUI before it would use both screens. (like mine is set to 2304x1024, which is the combined 1280x1024&1024x1024 screens)

---

### Post by Snyper64 on 2007-03-18
Ok, I need some help here also. I know that I am missing my metamodes thanks to my xorg.conf log:
```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEDID" "True"
(**) NVIDIA(0): Option "UseEdidFreqs" "True"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "LeftOf"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     enabled on all display devices.
(WW) NVIDIA(0): No TwinView "MetaModes" specified; will fall back to Display
(WW) NVIDIA(0):     SubSection modes.
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce4 440 Go 64M at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.17.20.49.25
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 440 Go 64M at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     ViewSonic N2750w (CRT-0)
(--) NVIDIA(0):     QDS (DFP-0)
(--) NVIDIA(0): ViewSonic N2750w (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): QDS (DFP-0): 224.0 MHz maximum pixel clock
(--) NVIDIA(0): QDS (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Option "UseDisplayDevice" "DFP" converted to "DFP-0".
(WW) NVIDIA(0): TwinView requested, but only 1 display devices found.
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x800"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (98, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
```
But I am not sure on how I should go about setting that up. My main screen is my laptop monitor that runs at 1280x800 and my second display is a Viewsonic N2750w that runs at 1280x720. What I am trying to do is set up my tv(viewsonic) so that it only shows the background image and no icons or taskbars and if possible show its own background instead of a ultra stretched out background of my current desktop. I only use my Viewsonic for watching movies and not much else. [This]("http://www.kickthedragon.com/forums/attachments.php?id=400") is how my old Win XP setup looked like and I want to do something similar if possible, as you can see the Viewsonic uses the same background as my primary screen(IE: the background is NOT stretched out between both screens). Here is a copy of the relevent section of my xorg file:
```
Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
    Driver         "nvidia"
    BusID          "AGP:1:0:0"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "LeftOf"   
    Option "UseEdidFreqs" "True"
    Option "UseEDID" "True"
    Option "UseDisplayDevice" "DFP"
    Option "ConnectedMonitor" "DFP, CRT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection

```

Is it going to be possible to do this? Any help would be greatly appreciated.
Thanks
Snyper64

---

### Post by acconrad on 2007-03-18
> **Skeorx13 said:**
> What resolution did you select your screens to be set to in the GUI? For mine, I had to set the meta modes up and then select the combined metamode in the GUI before it would use both screens. (like mine is set to 2304x1024, which is the combined 1280x1024&1024x1024 screens)

Thanks for the help, that definitely gets dual monitors, but I run into 2 problems:

1. Ubuntu seems to think my default monitor is the LCD and not the laptop monitor...how do I fix this (see code above)?
1. My max screen rez are 1280x800 for the laptop (widescreen) and 1280x1024 for the LCD...this presents a problem because it thinks my LCD is the main, then I lose a good 200 px below on my laptop (because it sets my laptops rez to 1280x1024 as well, so  ihave to have menu bars on top)...how do I get around this problem?

Thanks!

---

### Post by Snyper64 on 2007-03-19
Try changing:

Option "ConnectedMonitor" "CRT,DFP"

To:

Option "ConnectedMonitor" "DFP, CRT"

This should also fix your resolution problems since it will switch your screens around.

Now, can someone help me with my problem posted 2 posts above.

---

### Post by acconrad on 2007-03-19
i tried beforehand but it didn't help.

i have the same monitor setup as you and i would suggest adding this line to your device options

Option "MetaModes" "2560x800";
it will make your window a bit too tall for your 2nd monitor, but the width will be perfectly stretched across both monitors (that's what I had to do...)

---

### Post by Snyper64 on 2007-03-19
I already figured out my metamodes, but it still won't even detect my second monitor and just reverts back to my laptop monitor. Heres my log:
```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "UseEDID" "True"
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP, CRT"
(**) NVIDIA(0): Option "UseEdidFreqs" "True"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "LeftOf"
(**) NVIDIA(0): Option "MetaModes" "DFP: 1280x800, CRT: 1280x720"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     enabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): ConnectedMonitor string: "DFP, CRT"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce4 440 Go 64M at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.17.20.49.25
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 440 Go 64M at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     ViewSonic N2750w (CRT-0)
(--) NVIDIA(0):     QDS (DFP-0)
(--) NVIDIA(0): ViewSonic N2750w (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): QDS (DFP-0): 224.0 MHz maximum pixel clock
(--) NVIDIA(0): QDS (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Option "UseDisplayDevice" "DFP" converted to "DFP-0".
(WW) NVIDIA(0): TwinView requested, but only 1 display devices found.
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): Invalid display device in Mode Description "CRT:1280x720"
(WW) NVIDIA(0): Not using mode description "CRT:1280x720"; unable to map to
(WW) NVIDIA(0):     display device
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "DFP:1280x800,CRT:1280x720"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (98, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
```

Heres my current xorg file:
```
Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
    Driver         "nvidia"
    BusID          "AGP:1:0:0"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "LeftOf"   
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "DFP: 1280x800, CRT: 1280x720"
    Option "UseEDID" "True"
    Option "UseDisplayDevice" "DFP"
    Option "ConnectedMonitor" "DFP, CRT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection
```

What I don't understand is it looks like it sees both monitors but it just doesn't want to use them both. Any help?

---

### Post by makhand on 2007-03-19
> **tribble222 said:**
> I have a DFT and a CRT and I wanted the DFT to be my primary display.  After hours of trying to get it to work I could never get the DFT to be my primary although it would work fine if I wanted my CRT to be the primary.  It turns out it's a limitation of the drivers - they only will detect the CRT first and if you tell them to detect the DFP with the UseDisplayDevice line then it won't find the CRT at all.

What you need to do is get the latest (1.0-9746) drivers and add the line:

Option "TwinViewXineramaInfoOrder" "DFP, CRT"

and comment out UseDisplayDevice and ConnectedMonitor.

This worked great for me and I hope it helps someone else!

After months of frustration and hours of messing with the configs, the above solution fixed the same problem for me. You must make sure you upgrade to 1.0-9746 drivers. Besides fixing which monitor was the primary one (using above option), these drivers seem to add several other new features/improvements. I used the procedure at [http://ubuntuforums.org/showthread.php?t=296933&highlight=nvidia+9746](http://ubuntuforums.org/showthread.php?t=296933&highlight=nvidia+9746) 
to install the new drivers. Couldn't be happier. Thanks tribble222

---

### Post by Snyper64 on 2007-03-20
Ok, I finally got my screens to go Dual. I realized my mistake when looking at other peoples files and realized that it wasn't loading my screen because I forgot to add it to my UseDisplayDevice option. But now I have two problems, one small one fairly big(not as big as not having a second monitor:lolflag:). The smaller problem is that my background no matter how much I try will not fit on one monitor at a time and is instead centered in between both monitors. I have heard about a Xinerama option, would this fix my background problem and if so what are the negatives about it that could effect my setup. The second and bigger problem is that for some reason my tv seems to be the primary monitor(upon loading desktop all of my icons and taskbars were on my tv screen) and everything I open opens on my tv, is there any way to fix this problem as I primarily do all of my work on my laptop screen and generally have my tv off? Oh, and acconrad, try setting your metamodes up like mine except with your resolutions, it should fix your dead space problem. Other than that we both seem to be having a problem with getting programs to open in our laptop screens.

```
Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "RightOf"   
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "DFP: 1280x800, CRT: 1280x720"
    Option "UseEDID" "True"
    Option "UseDisplayDevice" "DFP, CRT"
    Option "ConnectedMonitor" "DFP, CRT"
EndSection
```

Thanks for any help.
Snyper64

---

### Post by ViGiLnT on 2007-03-23
I'm posting this just in case anyone has the same configuration as I do.

I've got a Asus F3JC Laptop that has a nvidia 7300 dvi.
I've also got an IBM T560 TFT(or lcd I dont quite know the difference) connected to my laptop through the analog connector.

I'm now running a dual-head setup with nvidia twinview when I connect the IBM monitor. If I dont have the IBM monitor connected the screen config stays has if I dont have twinview configured, as it is suposed to be.

This is my xorg.conf:

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Fri Dec 15 10:12:14 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
    Option "Xinerama"  "false"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "pt"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option	   "NoLogo" "true"
    BusID          "PCI:1:0:0"

    Option 	   "TwinView" "True"
    Option 	   "TwinViewOrientation" "LeftOf" # Primary left of secondary
    Option 	   "UseEdidFreqs" "True"
    Option 	   "MetaModes" "DFP-0: 1280x800,CRT-0: 1024x768 ; DFP-0: 1280x800, CRT-0: NULL"
    Option	   "TwinViewXineramaInfoOrder" "DFP-0, CRT-0"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by Snyper64 on 2007-03-23
Are you saying that you have 3 monitors? Your laptop monitor and 2 others? If so I can see what you problem is, you need to label whatever your first crt(whatever uses a VGA connection) device is crt-0 and than label your other monitor crt-1, the same goes for your DFP settings, also get rid of your "crt-null" setting. If your are running only 2 screens(your laptop and another screen) than you may want to change your metamodes to: "MetaModes" "DFP-0: 1280x800; CRT-0: 1024x768"

---

### Post by ViGiLnT on 2007-03-24
I said I've got a dual screen setup...

And I said that I'm only posting this in case anyone has the same setup as I do.

I also said that everything is working as it is supposed to.

I've got no problem :P

Are you really talking to me Snyper64 ?

Anyway, the 
```
DFP-0: 1280x800, CRT-0: NULL
```
line is necessary for when I don't have the IBM monitor connected.

---

### Post by Snyper64 on 2007-03-24
You still shouldn't need it since you use a laptop gpu(read [here]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-i.html")) and it'll detect if you do not have your second monitor attached and run in just single monitor mode. Right now I am running dual x screens and when I do not have my second monitor hooked up it automatically reverts back to just a single monitor, it did the same thing when I used twinview.

---

### Post by wedge2k on 2007-03-25
> **tribble222 said:**
> I have a DFT and a CRT and I wanted the DFT to be my primary display.  After hours of trying to get it to work I could never get the DFT to be my primary although it would work fine if I wanted my CRT to be the primary.  It turns out it's a limitation of the drivers - they only will detect the CRT first and if you tell them to detect the DFP with the UseDisplayDevice line then it won't find the CRT at all.

What you need to do is get the latest (1.0-9746) drivers and add the line:

Option "TwinViewXineramaInfoOrder" "DFP, CRT"

and comment out UseDisplayDevice and ConnectedMonitor.

This worked great for me and I hope it helps someone else!

THANK YOU! *TEAR* Now if only Nvidia would include this in their nice little qui util.  =)

---

### Post by ViGiLnT on 2007-03-26
> **Snyper64 said:**
> You still shouldn't need it since you use a laptop gpu(read [here]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-i.html")) and it'll detect if you do not have your second monitor attached and run in just single monitor mode. Right now I am running dual x screens and when I do not have my second monitor hooked up it automatically reverts back to just a single monitor, it did the same thing when I used twinview.

You're right.

That's not needed.

:D

---

### Post by Jovec on 2007-03-28
Curious to know if anyone has any experience using the seperate X screen configuation, instead of Twinview, especially any performance related issues.  Since I only use my second monitor for tv/movie watching, I'd like to be able to have it go to sleep mode automatically, which Twinview can't do.  Also, TV has a few other annoying issues, such as VLC won't go into fullscreen mode on the 2nd monitor, only the first (under Beryl it will though).  I plan to test it out myself, but just looking for input/advice.

---

### Post by lawrens on 2007-03-29
Thanks for the guide and links, and the help from the followup posts, adding some of the command from some of the posts works, everything is working out fine :)

My setup is a dell m1710 laptop having vga-out to a Sony LCD TV, laptop at 1920x1200 resolution and the LCD TV is at 1360x768, my default monitor is on the laptop, TV on the right, login screen and everything are on the default laptop screen using
```
Option         "TwinViewXineramaInfoOrder" "DFP, CRT" 
```

Now if only I know how to make a script to disable one or another and restart x automatically, anyone have a good solution for that >.>?

Here's my xorg.conf:

```
 # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Feb 26 23:38:46 PST 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
    Option "Xinerama" "Off"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load	   "dbe"
    Load	   "dri"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option	   "Buttons" "5"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Emulate3Buttons" "True"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option         "NvAGP" "0"
    Option         "UseEdidDpi"   "FALSE"
    Option         "DPI"   "96 x 96"
    Option         "TripleBuffer" "True"
    Option	   "MultisampleCompatibility"	"True"
    Option         "AllowGLXWithComposite" "True"
    Option         "DisableGLXRootClipping" "True"
    Option         "RenderAccel" "True"
    Option         "XAANoOffscreenPixmaps"   "True"
    Option         "NoPowerConnectorCheck"
    Option	   "TwinView" "True" 
    Option         "MetaModes" "1920x1200, 1360x768"
    Option         "TwinViewXineramaInfoOrder" "DFP, CRT" 
    Option         "UseDisplayDevice" "DFP, CRT"
    Option 	   "TwinViewOrientation" "DFP LeftOf CRT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
	Viewport   0  0
        Depth       24
        Modes      "1920x1200"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
	Viewport   0  0
        Depth       24
        Modes      "1360x768"
    EndSubSection
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection
 
```

Only problem of my setup is strange little ones that aren't nvidia/xorg related, like beryl's panel shadow doesn't work anymore (window shadow does) and conky is on the wrong screen, sad to see desktop wall to go either from beryl (it works but doesn't look good and doesn't have the option to show seperate ones like desktop cube). Other than that, beryl works completely fine, just a bit confusing now with 2 desktops on every side of the cube linked to eachother lol, and I hope my xorg isn't bad since I put in some of those by trial and error, I'm a noob and I don't really know how some of those lines are working, I hope my tv doesn't blow up from a wrong refresh rate or something which I didn't put in =/

Edit: oh menu shadow fixed itself >_> and conky shows up on second screen because of "Top Right" being the 2nd monitor on the right (slaps face), so a 1379 X Gap fixed it <.<

---

### Post by Jovec on 2007-03-29
> **lawrens said:**
> Now if only I know how to make a script to disable one or another and restart x automatically, anyone have a good solution for that >.>?

Not sure why you want to restart X automatically....But, you can define meta modes with a NULL entry to disable that monitor then use "xivdtune -next" (or possible just pick that   resolution from the Screen preferences)  to cycle between them.

Try changing:

```
Option         "MetaModes" "1920x1200, 1360x768"
```

to

```
Option         "MetaModes" "1920x1200, 1360x768; 1920x1200, NULL; NULL, 1360x768"
```

---

### Post by klato on 2007-03-31
**update**: i got it working! turns out i was using a bad video cable!!  I'm now struggling to get the correct resolution on my TV.  My laptop lcd is 1280x800, but that is too big for my tv...i tried the panning option, but i really just want the resolution to fill up the tv screen nicely.  is this possible? 




I've been through this entire thread but I still can't get twinview working for me.  I'd like to be able to do output to my TV.

Here's what my xorg.conf looks like right now:

Section "Device"
	Identifier	"nVidia Graphics Controller"
	Driver		"nvidia"
	Option		"NoLogo"
	Option 		"TwinView" "true"
	Option 		"TwinViewOrientation" "Clone"
	Option 		"TVOutFormat" "COMPOSITE"
	Option 		"TVStandard" "NTSC-M"
	Option 		"SecondMonitorHorizSync" "30-50"
	Option 		"SecondMonitorVertRefresh" "60"
#	Option 		"MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;    512x384,512x384"
	Option 		"ConnectedMonitor" "DFP,TV"
EndSection


And here's what my xorg.0.log says:

(**) NVIDIA(0): Option "NoLogo"
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP-0,TV-0"
(**) NVIDIA(0): Option "TVStandard" "NTSC-M"
(**) NVIDIA(0): Option "TVOutFormat" "COMPOSITE"
(**) NVIDIA(0): Option "TwinView" "true"
(**) NVIDIA(0): Option "TwinViewOrientation" "Clone"
(**) NVIDIA(0): Option "SecondMonitorHorizSync" "30-50"
(**) NVIDIA(0): Option "SecondMonitorVertRefresh" "60"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Forcing COMPOSITE video output
(**) NVIDIA(0): TV Standard string: "NTSC-M"
(WW) NVIDIA(0): No TwinView "MetaModes" specified; will fall back to Display
(WW) NVIDIA(0):     SubSection modes.
(**) NVIDIA(0): TwinView enabled
(**) NVIDIA(0): ConnectedMonitor string: "DFP-0,TV-0"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce Go 7300 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.41.79
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 7300 at PCI:1:0:0:
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0):     CMO (DFP-0)
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Devices: DFP-0, TV-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x800"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800

I'm using an SVIDEO->Composite adapter for my TV.  My graphics card is a GeForce Go 7300.  Right now I see no activity on the TV :(

Thanks for any advice!

---

### Post by PartisanEntity on 2007-04-02
Complete newb when it comes to TwinView, would really appreciate some help:

I attached a TFT monitor to my Laptop, I am using Analog.

Using the instructions in the first post of this thread I now managed to get a picture on my TFT in the correct resolution but my laptop screen is off. Here is my xorg.conf section:

```
Section "Device"
    Identifier     "NVIDIA Corporation NV40M? [GeForce Go 6200]"
    Driver         "nvidia"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "LeftOf"   
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "1680x1050,1280x800; 1280x1024,1280x1024; 1024x768,1024x768"
    Option "UseDisplayDevice" "CRT" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
EndSection
```

What do I need to edit/change in order to have my laptop screen turn on as well?

Thank you!

---

### Post by Snyper64 on 2007-04-02
```
Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "RightOf"   
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "DFP: 1280x800, CRT: 1280x720"
    Option "UseEDID" "True"
    Option "UseDisplayDevice" "DFP, CRT"
    Option "ConnectedMonitor" "DFP, CRT"
EndSection
```

This is a copy of my twinview settings, copy in what is missing and set your resolutions for your particular monitor. You may not need the connected monitor option like I did. I also run a laptop with a connected monitor like you so it should run just fine.

---

### Post by PartisanEntity on 2007-04-02
> **Snyper64 said:**
> ```
Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 420 Mac 32M/GeForce 440 Go 64M]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "RightOf"   
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "DFP: 1280x800, CRT: 1280x720"
    Option "UseEDID" "True"
    Option "UseDisplayDevice" "DFP, CRT"
    Option "ConnectedMonitor" "DFP, CRT"
EndSection
```

This is a copy of my twinview settings, copy in what is missing and set your resolutions for your particular monitor. You may not need the connected monitor option like I did. I also run a laptop with a connected monitor like you so it should run just fine.

Thanks very much for posting this, it worked, I now have my desktop stretched over both the monitor and the laptop.

Just one more question, what would be the result of this code alteration:

```
    Option "UseDisplayDevice" "CRT"
    Option "ConnectedMonitor" "DFP"
```

---

### Post by Snyper64 on 2007-04-02
The connected monitor option only looks for the screens you select(IE: CRT, DFP, TV) and will not check for any other screens. On mine for example it will check for the CRT and DFP monitors but will not check for a tv attached through my s-video. Its only really needed for a monitor or tv that does not send out an edid signal, but in my case my cable on my monitor is screwey.

The use display device option specifies in what order you graphics card looks for you monitor, by default it looks for: CRT/DFP/TV in that order. In my case I wantit to see my laptop screen first and make it the default screen and set my crt up as a secondary screen. This works very well for desktops but in my case a limitation on my mobile GPU and driver it sets my CRT up as my primary monitor(all of my windows and taskbars appear on it by default) but still keeps my crt to the right of my laptop screen.

---

### Post by klato on 2007-04-02
Does anyone know if it's at all possible to do 2 different resolutions with TwinView, 1 resolution for a laptop LCD (1280x800) and a 2nd resolution for a TV (1024x768)?  Does it make sense to do it?  I can get 2 seperate X screens with different resolutions, but I'd like to know if this is at all possible via TwinView?

---

### Post by PartisanEntity on 2007-04-03
> **klato said:**
> Does anyone know if it's at all possible to do 2 different resolutions with TwinView, 1 resolution for a laptop LCD (1280x800) and a 2nd resolution for a TV (1024x768)?  Does it make sense to do it?  I can get 2 seperate X screens with different resolutions, but I'd like to know if this is at all possible via TwinView?

Yes of course, here is what I have:

```
    Option "MetaModes" "1680x1050,1280x800"
```

My TFT monitor has a resolution of 1680x1050 and my laptop LCD is 1280x800 hence my code above. Just change it to suit your needs. (Make sure to back up xorg.conf first).

---

### Post by PartisanEntity on 2007-04-03
I have been looking through the documentation, and DFP stands for digital flat panel. But what about the LCD

---

### Post by PartisanEntity on 2007-04-03
According to the documentation DFP stands for digital flat panel. What about the LCD screen on my laptop, can i / should i replace DFP with LCD?, does it matter?

---

### Post by Snyper64 on 2007-04-03
CRT stands for anything connected through a vga connection even if its a DFP.

DFP means anything connected through a DVI connection.

---

### Post by klato on 2007-04-03
Hmm, I've tried using the folllwing options with no success:

Option "MetaModes" "1280x800,1024x768"
Option "MetaModes" "DFP: 1280x800, TV: 1024x768"
and
Option "MetaModes" "DFP-0: 1280x800, TV-0: 1024x768"

Every time I do this, my laptop lcd looks fine, but the TV looks like it's also using this resolution.

I just remembered from my xorg.conf log, that the detected devices were TV-0 and CMO-0...so maybe I'll try specifying the MetaModes like that.

---

### Post by Mantis2600 on 2007-04-03
I'm working with a Generic Nvidia 6800 and the drivers that I downloaded off the Nvidia website yesterday for Amd64. I've got a CRT and a REALSync DFP plugged in and I can't seem to A) make the DFP my primary monitor and B) Change the resolution of the DFP from 640x480 to anything reasonable. I've tried a bit of messing with the xorg.conf file, but I'm stumped so I thought I'd post some info and see if anyone else can help.

Ideally this is what I will have:

DFP (primary 1280x1024 higher refresh rate than 50 if at all possible) to the left of my CRT (secondary 1024x768 higher refresh rate than 50 if at all possible)

Thanks 

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Mon Oct 16 22:13:48 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6800]"
    Driver         "nvidia"
    Option	   "UseEDID"  "False"
    Option	   "TwinView" "1"
    Option	   "TwinViewOrientation" "LeftOf"
    Option	   "UseEdidFreqs" "True"
    Option	   "MetaModes" "1280x1024,1024x768; 1152x864,1024x768; 1024x768,1024x768"
    Option	   "UseDisplayDevice" "CRT"
    Option	   "ConnectedMonitor" "DFP,CRT" 
    Option 	   "NoTwinViewXineramaInfo"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes     "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes     "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes     "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes     "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes     "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes     "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by klato on 2007-04-04
OK I'm pretty stumped.  I'm trying to get 1280x800 on my laptop LCD and 1024x768 on my TV, but the TV resolution simply will not change.

Here's my xorg.conf:

Section "Device"
	Identifier	"nVidia Graphics Controller"
	Driver		"nvidia"
	Option		"NoLogo"
	Option 		"TwinView" "true"
	Option 		"TwinViewOrientation" "Clone"
	Option 		"TVOutFormat" "COMPOSITE"
	Option 		"TVStandard" "NTSC-M"
	Option 		"SecondMonitorHorizSync" "30-50"
	Option 		"SecondMonitorVertRefresh" "60"
	Option		"MetaModes" "DFP: 1280x800, TV: 1024x768"
EndSection

I've tried a whole bunch of different options, but it still doesn't work.  Any ideas?

---

### Post by Jovec on 2007-04-04
> **klato said:**
> OK I'm pretty stumped.  I'm trying to get 1280x800 on my laptop LCD and 1024x768 on my TV, but the TV resolution simply will not change.

Here's my xorg.conf:

Section "Device"
	Identifier	"nVidia Graphics Controller"
	Driver		"nvidia"
	Option		"NoLogo"
	Option 		"TwinView" "true"
	Option 		"TwinViewOrientation" "Clone"
	Option 		"TVOutFormat" "COMPOSITE"
	Option 		"TVStandard" "NTSC-M"
	Option 		"SecondMonitorHorizSync" "30-50"
	Option 		"SecondMonitorVertRefresh" "60"
	Option		"MetaModes" "DFP: 1280x800, TV: 1024x768"
EndSection

I've tried a whole bunch of different options, but it still doesn't work.  Any ideas?

What do you mean by "the TV resolution simply will not change."  Not sure how well Clone mode will work with 2 different resolutions.  Perhaps the Nvidia docs will help here (see my next post on how to enable panning, which might help if the different resolutions are your problem.)

---

### Post by Jovec on 2007-04-04
> **PartisanEntity said:**
> Yes of course, here is what I have:

```
    Option "MetaModes" "1680x1050,1280x800"
```

My TFT monitor has a resolution of 1680x1050 and my laptop LCD is 1280x800 hence my code above. Just change it to suit your needs. (Make sure to back up xorg.conf first).

You can also enable Panning which can be useful for devices with different resolutions with something like:

```
    Option "MetaModes" "1680x1050, 1280x800 @1280x1050"
```

---

### Post by PartisanEntity on 2007-04-04
> **Jovec said:**
> You can also enable Panning which can be useful for devices with different resolutions with something like:

```
    Option "MetaModes" "1680x1050, 1280x800 @1280x1050"
```

Hmm that sounds interesting, what does 'Panning' do exactly? Or how would it differ from my current set up?

---

### Post by klato on 2007-04-04
> **Jovec said:**
> You can also enable Panning which can be useful for devices with different resolutions with something like:

```
    Option "MetaModes" "1680x1050, 1280x800 @1280x1050"
```

Yep I've tried panning, but that doesn't really help because I only want to use TV out to watch videos/DVDs.  What I meant by "the resolution doesn't change" was that the TV resolution is basically set to 1280x800 with no panning even if I set my metamodes to 1280x800 and 1024x768.  The only way I can get 1024x768 on the TV is if I set my LCD to 1024x768 as well, which is not a good solution because it's a widescreen and looks pretty horrible at that resolution (and I don't want to have to switch resolutions ;) 

I guess I'll just stick with doing 2 X screens for now, since that seems  to work for me (plus, X/TwinView locks up if I close my laptop lid for an extended period of time anyway)

---

### Post by Jovec on 2007-04-04
> **PartisanEntity said:**
> Hmm that sounds interesting, what does 'Panning' do exactly? Or how would it differ from my current set up?

Panning sets the internal resolution to be larger than the displayed resolution, and you scroll to see the hidden parts of the screen.  IOW, it's a way to increase your resolution (including non-standard resolutions) beyond what your hardware is capable of displaying.

[quote=Klato]Yep I've tried panning, but that doesn't really help because I only want to use TV out to watch videos/DVDs. What I meant by "the resolution doesn't change" was that the TV resolution is basically set to 1280x800 with no panning even if I set my metamodes to 1280x800 and 1024x768. The only way I can get 1024x768 on the TV is if I set my LCD to 1024x768 as well, which is not a good solution because it's a widescreen and looks pretty horrible at that resolution (and I don't want to have to switch resolutions [/quote]
Well again, I'm not sure how you can clone between two display devices of different resolutions.   If the LCD is 1280x800, how do you expect to clone that onto 1024x768 worth of pixels?  Try changing Option "TwinViewOrientation" "Clone" to "RightOf" or "LeftOf" as appropriate to see if that allows independant resolutions (or 2 X screens like you suggest).


[quote=Klato]I guess I'll just stick with doing 2 X screens for now, since that seems to work for me[/quote]

I run 2 X screens also (primarily because VLC won't fullscreen on my second monitor (unless I'm running Berlyl)), and have no problems.  WoW runs fine too with maxed settings (sans forced AA, never tried it), but I wonder if the "performance hit" my show up with something a little more graphically demanding than WoW.

---

### Post by klato on 2007-04-04
I run 2 X screens also (primarily because VLC won't fullscreen on my second monitor (unless I'm running Berlyl)), and have no problems.  WoW runs fine too with maxed settings (sans forced AA, never tried it), but I wonder if the "performance hit" my show up with something a little more graphically demanding than WoW.[/QUOTE]

I noticed that when running 2 screens like that, most of the notification stuff (i.e. Beryl, network, etc) appears on my first screen (laptop LCD) .  However, if I try running Beryl on that second screen, it automatically appears on my LCD.  Is there any way around that, or is that the intended effect? (dunno, I might be getting off topic here =)

---

### Post by klato on 2007-04-04
I run 2 X screens also (primarily because VLC won't fullscreen on my second monitor (unless I'm running Berlyl)), and have no problems.  WoW runs fine too with maxed settings (sans forced AA, never tried it), but I wonder if the "performance hit" my show up with something a little more graphically demanding than WoW.[/QUOTE]

I noticed that when running 2 screens like that, most of the notification stuff (i.e. Beryl, network, etc) appears on my first screen (laptop LCD) .  However, if I try running Beryl on that second screen, it automatically appears on my LCD.  Is there any way around that, or is that the intended effect?

---

### Post by Jovec on 2007-04-04
> **klato said:**
> I noticed that when running 2 screens like that, most of the notification stuff (i.e. Beryl, network, etc) appears on my first screen (laptop LCD) .  However, if I try running Beryl on that second screen, it automatically appears on my LCD.  Is there any way around that, or is that the intended effect?

Both X screens will use the same window manager, which is why when you enable Beryl, both screens become...Berylized.  I do not know if it is possible to run separate Window managers on separate X screens - it's something I've never tried.

As to the first part of your question, I'm not sure what can be done about that either.  On Windows, the NVidia driver allows you to choose where notification/dialog box windows will appear - i.e. always on your primary, always on your secondary, or, more intuitively, on the monitor the app that put up the dialog box is running on.  On Linux, I do not think the Nvidia driver is able to integrate that closer with the window manager you are running.  Because my personal use of the second monitor was only for media playing, I never bothered to investigate controlling dialog box placement.  Because of the way Twinview works, presenting a single, larger resolution to the X-server and hiding the fact that the resolution is spread across two (or more) monitors, I doubt that the WM will be able to more intelligently control dialog bog/notification window placement.

---

### Post by klato on 2007-04-04
Weird, for me, only the 1st X screen gets the Beryl effects.  The other screen stays as is.

---

### Post by herbster on 2007-04-05
How do I stop windows from being maximized/fullscreen'd across BOTH MONITORS?? I had this working like 2 hours ago using nvidia-settings then I rebooted and the sucker didn't save my xorg, now I've been trying to figure this out and am pulling teeth.

Right now both monitors act as one workspace, I have them both 1600x1200, it is fine but whenever I maximize or anything it spreads across both and I hate it, how can I get each one separate but still one big workspace? I had it earlier!!!

---

### Post by SGulseth on 2007-04-09
Hey, ive tested the twin view, but i cant get it to work. If "UseDisplayDevice" is "TV,DFP" it only show image at the TV in black and white, and not on my monitor. If i change the "UseDisplayDevice" to "DFP" it shows on my monitor. Also "TV,DFP" shows me the boot screen when im starting up, both in colours.

GraphicCard: XFX GeForce 7900 GT 256 MB Extreme Edition,  DVI, double DVI, TV-out

Heres my device section
> 
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "RightOf"   
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option "UseDisplayDevice" "DFP,TV"
EndSection



Heres my xorc.conf
> 
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "dbe"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "no"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "RightOf"   
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
    Option "UseDisplayDevice" "DFP,TV"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1280*1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280*1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280*1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280*1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280*1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280*1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection




Thx

---

### Post by Kuroyume on 2007-04-11
i have a problem with this... instead of getting one screen server per monitor, or one big one that covers both screens, i get the screen server in the middle of both screens, but covering only a small area on the center...

my xorg.conf:


```
Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7300 GT]"
	Driver		"nvidia"
	BusID		"PCI:3:0:0"
        Option          "AddARGBGLXVisuals" "True"
        Option "TwinView" "True"
        Option "TwinViewOrientation" "RightOf"
        Option "UseEdidFreqs" "True"
        Option "MetaModes" "1440x900,1440x900; 1440x900,NULL"
        Option "UseDisplayDevice" "CRT"
        Option "ConnectedMonitor" "CRT, CRT"
EndSection

Section "Monitor"
	Identifier	"VA1703wSERIE"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7300 GT]"
	Monitor		"VA1703wSERIE"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection
```

i suspect that i need to change something in my Screen section, but i am not sure what...
i am running kubuntu feisty...

---

### Post by jzwill on 2007-04-14
Well, I have been trying and trying for two sraight days (reading countless howto's and other info) to get this working.  I feel like I am very close but no cigar yet.  Here are my specs:

GeForce FX 5500
VGA: Dell CRT monitor
DVI: Apple 23 " HD Cinema Display

The Dell displays perfectly.  On the Apple display, I can see light, but I can not distinguish anything. The display is basically the color of the Gnome desktop, with some colorful "virtical bars" on the right side of the screen.  If I drag a window to that display, it changes colors, but it is all just a big blur.  What is scary is that when I plug the Apple display back into my Mac, the "vertical bars" are burned into the screen (ie I can still see them), though they seem to have faded out over a period of about 10 minutes or so (thank goodness). Now I am scared to do any more tinkering as I do not want to permanently damage my $1000 display.  I am hoping that someone can offer some advice as to what to try next.

I am posting my xorg.conf and Xorg.0.log files below.

xorg.conf
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Mon Oct 16 22:13:48 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#Section "InputDevice"
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "stylus"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "stylus"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection
#Section "InputDevice"
#                                                      # for USB
#    Identifier     "eraser"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "eraser"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection
#Section "InputDevice"
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "cursor"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "cursor"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "ServerLayout"

#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
#    Identifier     "Default Layout"
#    Screen      0  "Crt" RightOf "Cinema"
#    Screen      1  "Cinema" 0 0
#    InputDevice    "Generic Keyboard"
#    InputDevice    "Configured Mouse"
#    Option         "Xinerama" "on"
#EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
#    Load           "ic2"
    Load           "bitmap"
    Load           "ddc"
#    Load	"dri"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load           "dbe"
    Load           "speedo"
    Load           "xtt"
    Load           "record"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

#
#Monitor Section
# ************************************************** ********************

# Any number of monitor sections may be present
#Section "Monitor"
#    Identifier     "CRT"
#    HorizSync       30.0 - 80.0
#    VertRefresh     50.0 - 80.0
#    Option         "DPMS"
#EndSection

Section "Monitor"
Identifier "Apple Cinema Display"
VendorName "Apple Inc."
ModelName "Apple Cinema Display 23"
HorizSync 28-96
VertRefresh 43-60
# 1680x1050 @ 59.9 Hz hsync: 64.7 kHz; PixelClock: 119.00 MHz
#Modeline "1680x1050" 119.00 1680 1728 1760 1840 1050 1053 1059 1080
#Modeline "1920x1200" 155.0 1920 1984 2016 2144 1200 1203 1206 1212 -HSync +Vsync
    Option "DPMS"
EndSection

# ************************************************** ********************
# Graphics device section
# ************************************************** ********************

Section "Device"
Identifier "NVIDIA GeForce 5500"
VendorName "nvidia"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "NoLogo" "False"
Option "NvAGP" "3"
Option "HWCursor" "True"

Option "TwinView" "True"
Option "UseEdidFreqs" "True"
Option "TwinViewOrientation" "RightOf"
Option "MetaModes" "1280x1024,1600x1200;1280x1024,1600x1200"
#Option "Xinerama" "True"
#Option "ConnectedMonitor" "DFP,CRT"
Option "UseDisplayDevice" "DFP,CRT"
Option "ExactModeTimingsDVI" "True"
Option "FlatPanelProperties" "Scaling = scaled, Dithering = default"
Option "DigitalVibrance" "50" #when using the Apple monitors
Option "CursorShadow" "1"
Option "CursorShadowAlpha" "64"
Option "CursorShadowYOffset" "2"
Option "CursorShadowXOffset" "4"
Option "RenderAccel" "1"
Option "WindowFlip" "false"
#Option "Xinerama" "on"
Option "AllowGLXWithComposite" "true"
EndSection

# ************************************************** ********************
# Screen sections
# ************************************************** ********************

Section "Screen"
  Identifier "Apple"
  Device "NVIDIA GeForce 5500"
  Monitor "Apple Cinema Display"
  DefaultDepth 24

  SubSection "Display"
  Depth 24
    Modes "1280x1024" "16001200" "1920x1200"
  EndSubSection
EndSection


#Section "Screen"
#Identifier "Crt"
#Device "NVIDIA GeForce 5500"
#Monitor "CRT"
#DefaultDepth 24

#SubSection "Display"
#Depth 24
#Modes "1600x1200"
#EndSubSection
#EndSection

# ************************************************** ********************
# ServerLayout sections.
# ************************************************** ********************

Section "ServerLayout"
Option "OffTime" "10"
Identifier "GeForce 6600 Dual Configuration"
Screen 0 "Apple" 0 0
#Screen 1 "Apple" RightOf "Crt"
InputDevice    "Generic Keyboard"
InputDevice    "Configured Mouse"
EndSection


Section "Extensions"
Option "Composite" "Enable"
EndSection

```


```
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 x86_64 
Current Operating System: Linux ubuntu64 2.6.17-11-generic #2 SMP Tue Mar 13 22:06:20 UTC 2007 x86_64
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 14 22:52:12 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "GeForce 6600 Dual Configuration"
(**) |-->Screen "Apple" (0)
(**) |   |-->Monitor "Apple Cinema Display"
(**) |   |-->Device "NVIDIA GeForce 5500"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "OffTime" "10"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,00e1 card 1043,813f rev a1 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00e0 card 1043,813f rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00e4 card 1043,813f rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00e7 card 1043,813f rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00e7 card 1043,813f rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00e8 card 1043,813f rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:05:0: chip 10de,00df card 1043,80a7 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:08:0: chip 10de,00e5 card 1043,813f rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0a:0: chip 10de,00e3 card 1043,813f rev a2 class 01,01,85 hdr 00
(II) PCI: 00:0b:0: chip 10de,00e2 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,00ed card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0326 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:07:0: chip 1282,9102 card 4554,434e rev 31 class 02,00,00 hdr 00
(II) PCI: 02:08:0: chip 4444,0016 card 0070,8801 rev 01 class 04,00,00 hdr 00
(II) PCI: 02:0a:0: chip 1102,0004 card 1102,2001 rev 04 class 04,01,00 hdr 80
(II) PCI: 02:0a:1: chip 1102,7003 card 1102,0040 rev 04 class 09,80,00 hdr 80
(II) PCI: 02:0a:2: chip 1102,4001 card 1102,0010 rev 04 class 0c,00,10 hdr 80
(II) PCI: 02:0b:0: chip 1106,3044 card 1043,808a rev 80 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc900000 - 0xfe9fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc4800000 - 0xe47fffff (0x20000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:14:0), (0,2,2), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xe4800000 - 0xec7fffff (0x8000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5500] rev 161, Mem @ 0xfd000000/24, 0xd0000000/28, BIOS @ 0xfe9e0000/17
(--) PCI: (2:8:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xe8000000/26
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfeafd000 - 0xfeafd7ff (0x800) MX[B]
	[1] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[2] -1	0	0xfeafd800 - 0xfeafdfff (0x800) MX[B]
	[3] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[4] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[6] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[7] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[8] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[9] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[10] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[14] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[15] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[19] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[20] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[21] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[22] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[25] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[26] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[27] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeafd000 - 0xfeafd7ff (0x800) MX[B]
	[1] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[2] -1	0	0xfeafd800 - 0xfeafdfff (0x800) MX[B]
	[3] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[4] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[5] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[6] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[7] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[8] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[9] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[10] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[14] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[15] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[17] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[18] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[19] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[20] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[21] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[22] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[25] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[26] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[27] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafd000 - 0xfeafd7ff (0x800) MX[B]
	[5] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[6] -1	0	0xfeafd800 - 0xfeafdfff (0x800) MX[B]
	[7] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[8] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[10] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[11] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[12] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[13] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[14] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[20] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[24] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[25] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[26] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[27] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[28] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[31] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[32] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[33] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "speedo"
(WW) Warning, couldn't open module speedo
(II) UnloadModule: "speedo"
(EE) Failed to load module "speedo" (module does not exist, 0)
(II) LoadModule: "xtt"
(WW) Warning, couldn't open module xtt
(II) UnloadModule: "xtt"
(EE) Failed to load module "xtt" (module does not exist, 0)
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:56:44 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafd000 - 0xfeafd7ff (0x800) MX[B]
	[5] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[6] -1	0	0xfeafd800 - 0xfeafdfff (0x800) MX[B]
	[7] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[8] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[10] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[11] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[12] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[13] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[14] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[20] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[24] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[25] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[26] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[27] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[28] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[31] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[32] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[33] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafd000 - 0xfeafd7ff (0x800) MX[B]
	[5] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[6] -1	0	0xfeafd800 - 0xfeafdfff (0x800) MX[B]
	[7] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[8] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[10] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[11] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[12] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[13] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[14] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[23] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[24] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[25] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[27] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[28] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[29] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[30] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[31] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[32] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[33] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[34] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[35] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[36] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "False"
(**) NVIDIA(0): Option "HWcursor" "True"
(**) NVIDIA(0): Option "NvAGP" "3"
(**) NVIDIA(0): Option "RenderAccel" "1"
(**) NVIDIA(0): Option "CursorShadow" "1"
(**) NVIDIA(0): Option "CursorShadowAlpha" "64"
(**) NVIDIA(0): Option "CursorShadowXOffset" "4"
(**) NVIDIA(0): Option "CursorShadowYOffset" "2"
(**) NVIDIA(0): Option "UseEdidFreqs" "True"
(**) NVIDIA(0): Option "TwinView" "True"
(**) NVIDIA(0): Option "TwinViewOrientation" "RightOf"
(**) NVIDIA(0): Option "MetaModes" "1280x1024,1600x1200;1280x1024,1600x1200"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Option "ExactModeTimingsDVI" "True"
(**) NVIDIA(0): Option "UseDisplayDevice" "DFP,CRT"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Enabling cursor shadow
(**) NVIDIA(0): Cursor shadow alpha = 64
(**) NVIDIA(0): Cursor shadow offset = 4
(**) NVIDIA(0): Cursor shadow offset = 2
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     enabled on all display devices.
(**) NVIDIA(0): TwinView enabled
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5500 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.69.01
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5500 at PCI:1:0:0:
(--) NVIDIA(0):     Dell  M991 (CRT-0)
(--) NVIDIA(0):     Apple Cinema HD (DFP-0)
(--) NVIDIA(0): Dell  M991 (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): Apple Cinema HD (DFP-0): 135.0 MHz maximum pixel clock
(--) NVIDIA(0): Apple Cinema HD (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Option "UseDisplayDevice" "CRT, DFP" converted to "CRT-0,
(II) NVIDIA(0):     DFP-0".
(II) NVIDIA(0): Assigned Display Devices: CRT-0, DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024,1600x1200"
(II) NVIDIA(0):     "1280x1024,1600x1200"
(II) NVIDIA(0): Virtual screen size determined to be 2880 x 1200
(--) NVIDIA(0): DPI set to (72, 72); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfeafd000 - 0xfeafd7ff (0x800) MX[B]
	[7] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[8] -1	0	0xfeafd800 - 0xfeafdfff (0x800) MX[B]
	[9] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[10] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[11] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[12] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[13] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[14] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[15] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[16] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[25] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b43f (0x40) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[28] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[29] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[30] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[31] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[32] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[33] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[34] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[36] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[37] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[38] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1280x1024,1600x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(WW) NVIDIA(0): Option "FlatPanelProperties" is not used
(WW) NVIDIA(0): Option "DigitalVibrance" is not used
(WW) NVIDIA(0): Option "WindowFlip" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

```

---

### Post by OsakaWilson on 2007-04-21
Ziox,

I love my new dual monitors and I love you!:)

---

### Post by shickidyshade on 2007-04-23
Hey guys 
here is my xorg.conf file I feel however that the resolutions are not accurate.  I would like to have 1680x1050.

Any ideas thanks for everything

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "FPD2275W"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"   
Option "UseEdidFreqs" "True"
Option "MetaModes" "1680x1050,1680x1050;1280x1024,1280x1024"
Option "UseDisplayDevice" "string" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "FPD2275W"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1440x1440" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1440x1440" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1440x1440" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1440x1440" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1440x1440" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1440x1440" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

---

### Post by Ziox on 2007-04-23
ATTENTION:

For anyone here who has a 9.xxx driver. Do the following:

gksudo nvidia-settings

Select X Server Display Configuration

After getting the correct setup (with resolution and such), hit "Save to X Configuration File.

If no dialog box appears, then hit th button again.

After the dialog box appears, just hit Save to file (or you can preview it and add it to your customized xorg.conf file)

Note: If you just hit Save to File, it'll overwrite any customized xorg.conf file.

---

### Post by Snyper64 on 2007-04-23
shickidyshade, remove all of your other metamodes except for the resolution you want your monitor to be at for depth 24. You should do this for your other depths also.

---

### Post by 7sudden on 2007-04-23
> **Ziox said:**
> [SIZE=4]**Dual Monitor With nVidia TwinView HowTo**[/SIZE]     [LEFT][FONT=Verdana]The following HowTo attempts to enable Dual Monitor support by using the TwinView function of the nVidia binary graphics driver.

 [/FONT][/LEFT]
        [LEFT][B][FONT=Verdana][SIZE=3]System Requirements:

[/SIZE][/FONT][/B][/LEFT]
    [LEFT][FONT=Verdana]A nVidia card with Dual output, whether it is VGA-DVI, VGA-VGA, or DVI-DVI.[/FONT][/LEFT]
    [LEFT][FONT=Verdana]Two Monitors (best if they are the same resolution, but different resolutions will work)[/FONT][/LEFT]
    [LEFT][FONT=Verdana]Installed and Working nVidia Binary graphics driver:[/FONT][/LEFT]
[INDENT][LEFT][FONT=Verdana]    Use the following link to install and enable the binary driver:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[/FONT][/LEFT]
[/INDENT][LEFT][B][FONT=Verdana][SIZE=3]Now get ready for some hardcore copy and pasting (not really).[/SIZE] ;)

[/FONT][/B][/LEFT]
        [LEFT][COLOR=Red]***[FONT=Verdana]1. Open Xorg.conf file by activating ONE of the following command (based on your distribution):[/FONT]***[/COLOR][/LEFT]
        [LEFT][FONT=Verdana]Gnome (Ubuntu):[/FONT][/LEFT]
    [LEFT]```
gksudo gedit /etc/X11/xorg.conf
```[/LEFT]
    [LEFT][FONT=Verdana]KDE (Kubuntu):[/FONT][/LEFT]
    [LEFT]```
kdesu kate /etc/X11/xorg.conf
```[/LEFT]
    [LEFT][FONT=Verdana]Xfce4 (Xubuntu):[/FONT][/LEFT]
    [LEFT]```
gksudo mousepad /etc/X11/xorg.conf
```[/LEFT]
    [LEFT][FONT=Verdana]Command-Line Based:[/FONT][/LEFT]
    [LEFT]```
sudo nano /etc/X11/xorg.conf
```[/LEFT]
        [LEFT][COLOR=Red]***[FONT=Verdana]2. Next navigate to your "Device" Section, which should appear similar to the example shown below, the identifier and BusID WILL be different:[/FONT]***[/COLOR][/LEFT]
    [LEFT]```
Section "Device"
    Identifier    "nVidia 7900"
    Driver        "nvidia"
    BusID        "PCI:1:5:0" 
EndSection
```***[FONT=Verdana][COLOR=Red]3. Add the following lines to that section:[/COLOR][/FONT]***[/LEFT]
    [LEFT]```
Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"   
Option "UseEdidFreqs" "True"
Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
Option "UseDisplayDevice" "string" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
```[/LEFT]

        [LEFT]**[FONT=Verdana]These codes are the bare minimum for enabling TwinView.  This should work most people, however, every system is configured differently, so use the following guide to add more options:[/FONT]**[/LEFT]
    [LEFT][FONT=Verdana][http://download.nvidia.com/solaris/1.0-8762/README/appendix-d.html](http://download.nvidia.com/solaris/1.0-8762/README/appendix-d.html)

[/FONT][/LEFT]
        [LEFT][I][B][FONT=Verdana][COLOR=Red]4. Save the file, and restarted X (ctrl+alt+backspace), or reboot.

[/COLOR][/FONT][/B][/I][/LEFT]
        [LEFT][B][FONT=Verdana]You should now have TwinView :). If not, then just post the problem's symptoms, along with your xorg.conf file.

[/FONT][/B][/LEFT]
        [LEFT][COLOR=Red]**[FONT=Verdana]Good Luck! :)[/FONT]**[/COLOR][/LEFT]
Okay, I finally got Feisty up and running on my 8800GTX. Now, I'd like to get Twinview going. As a newbie, I'm a little nervous with trying this out. Any suggestions?  Is the process the same?

---

### Post by mattman on 2007-04-23
I just got twin view setup and both my monitors are working but the resolution is stuck at 1600x600 which is huge. I would like both monitors to display at 1280x1024. Any help would be appreciated. Heres my xorg.conf

> Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
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
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option "AddARGBGLXVisuals" "True"
	Option "TwinView" "True"
	Option "TwinViewOrientation" "RightOf" 
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Generic Video Card"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout" 
	Screen          "Default Screen" 0 0 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by ngtmagicks on 2007-04-24
Argh,  Alright I think I got it, but one thing that has really been bugging me.  
Every couple of times I try this with my Nvidia Geforce Fx 5200 dual vga outs, I set it up, I think it's working, change something like the resolution, and on my next reboot or a restart of the x server, I get nothing.
It's not like I can log into the console and change the xorg.conf to a backup, it's really just blown out and I've had to reinstall 3 times while learning this.

any suggestions as to what could be causing it.  It's happened in both gdm and gnome, and 3 times in kubuntu.. so that's kdm and kde.  

thanks.

---

### Post by ignitionnight on 2007-04-28
I am attempting to set up TwinView on my Ubuntu 7.04.

My video card is a simple GeForce4 MX 440 AGP 8x. I have a Samsung SyncMaster 914v connected through VGA, and I am attempting to set up my 720p HDTV through S-Video (yeah I know, its not hd but thats not my problem). My monitor supports up to 1280x1024, and my TV supports up to 1024x760.

When booting up it shows the Ubuntu splash on both screens, but as soon as I hit the log in screen it turns off the connection to my TV. I have gotten it to work with my TV only, but not with both.

Also, idealy I would like to have it set up as two monitors that I can drag my windows over to on different workspaces, not one big extended monitor.

Here is my xorg.conf file. Any help setting this up would be GREATLY APPRECIATED, this is the only issue that keeps windows on my computer. You can either post any tips here, or IM me at AIM: XignitionXnightX or MSN: [email]ignitionnight@hotmail.com[/email] or you can E-Mail me at [email]ignitionnight@gmail.com[/email]. Thanks Homies!

```

Section "Device"
	Identifier	"nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"			"true"
	Option		"AddARGBVisuals"		"True"
	Option		"AddARGBGLXVisuals"		"True"
	Option		"NoLogo"			"True"
	Option 		"TwinView" 			"True"
	Option 		"TwinViewOrientation" 		"RightOf"   
	Option 		"UseEdidFreqs" 			"True"
	Option 		"MetaModes" 			"1280x1024,1280x1024; 1024x768,1024x768"
	Option 		"UseDisplayDevice" 		"CRT" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
EndSection

Section "Monitor"
	Identifier	"SyncMaster 914v"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"SyncMaster 914v"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

---

### Post by ignitionnight on 2007-04-29
So I am pretty much a HUGE idiot.

I spent almost 4-5 hours trying to get this figured out. I went to work and when I got back figured I should start from the very beginning of this thread. Thats when I noticed the updated instructions.

took me almost 10 clicks to get it working right.

Sometimes I hate myself, but sometimes I love me some ubuntu!

---

### Post by Guranic on 2007-05-10
I have problems with my laptop and projector. I have Asus A6K laptop with nVidia go 6800 and 1280x800 widescreen. I'm using restricted drivers. This thread shows how to set up things with nvidia-settings gui. I can set twinview on, but problem is that I can't set right resolutions. If I hit the detect displays button projector will support only 320xsomethin or 640xsomething. The right resolutions would be either 1280x800 on both screens (clone) or 1024x768 on both screens. I can set laptops screen to 1024x768 but nvidia-settings won't let me set higher resolutions for projector? All screes I've connected to my laptop shows up in nvidia-settins as CRT (projector and lcd-tv) I could use some help to get clone twinview working with projector...

---

### Post by Esmo2000 on 2007-05-13
I couldn't get this to work on my laptop.

I'm running an nvidia geforce 7600 GO with dvi output to a samsung syncmaster 206bw.  My laptop monitor runs at 1920x1200 and the monitor runs at 1680 X 1050.  When i run the nvidia settings manager it registers the second monitor as being there and correctly infers information about it, however, it does not seem to drive a signal to it.  I have the monitor up and working in Windows so I know its not the monitor's fault.

Could anyone help?

---

### Post by Ziox on 2007-05-13
> **Esmo2000 said:**
> I couldn't get this to work on my laptop.

I'm running an nvidia geforce 7600 GO with dvi output to a samsung syncmaster 206bw.  My laptop monitor runs at 1920x1200 and the monitor runs at 1680 X 1050.  When i run the nvidia settings manager it registers the second monitor as being there and correctly infers information about it, however, it does not seem to drive a signal to it.  I have the monitor up and working in Windows so I know its not the monitor's fault.

Could anyone help?

You must enable TwinView in order to send signal to the other monitor.

Select your external monitor and hit "configure" and then select Twinview.

---

### Post by Esmo2000 on 2007-05-13
Yes, i did that but it still didn't work.  Possibly something else??

---

### Post by consultlinks on 2007-05-14
similar issues I tried posting elsewhere they referred me here.  I am getting the monitor not defined erroe
#etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Load	"nv"
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
	Identifier	"0 NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nv"
	BusID		"PCI:0:8:0"
	Screen		0
	Option		"DDCMode" "True"
	Option		"MonitorLayout"	"Main Monitor, Second Monitor"
EndSection

Section "Device"
	Identifier	"1 NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"AOC Spectrum"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device		"0 NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"Main Monitor"
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

Section "Screen"
	Identifier	"Second Screen"
	Device		"1 NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"Second Monitor"
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
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	0	"Main Screen"
	Screen	1	"Second Screen"	RightOf	"Main Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	Option		"Twinview" "true"
EndSection


Section "DRI"
	Mode	0666
EndSection

---

### Post by mviroli on 2007-05-15
It is a matter of fact that the Ctrl-Fn8 key is not switching graphics mode very well on many Ubuntu laptops with nvidia cards and driver, e.g. on my DELL D620, (NVIDIA quadro NV110 and 1.0-9755 driver)

However, I was observing that the nvidia-settings application is able to correctly send switching commands to the driver: each time a new mode is applied through that application, things switch perfectly and a new line of the kind

(II) NVIDIA(0): Setting mode "CRT:NULL,DFP:nvidia-auto-select+0+0"

appears on the X log file.

So, I'm wondering whether there is a command from the terminal which I can use to tell the driver to switch to a new mode.

Using nvidia-settings each time is not very practical, and no command-line argument seems to fit my needs. Should I just hope for a new version of the driver?

---

### Post by dvazriel on 2007-05-15
Okay i have two problems with twinview. 

1-) Everytime i reset my computer or X, it defaults back to single screen ( and yes i have both screens on ). I have to go back to nvsettings and enable it again.

2-) When i maximize, it spans the window across both screens. Anyway to make it just maximize to the parent screen?

thanks.

---

### Post by johnnyphive on 2007-05-15
So far so good, just one problem.

The system seems to want to use my right monitor as my "main" monitor (login screen is there, apps default to that screen when opening, etc).  How can i change this to my left monitor?

Sorry, forgot to post my config

```

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VA902b"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6800 LE"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1280x1024 +1280+0, CRT-1: 1280x1024 +0+0; CRT-0: 1024x768 +1024+0, CRT-1: 1024x768 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

---

### Post by Sladi on 2007-05-21
Johnnyphive try ```
Option "TwinViewXineramaInfoOrder" "DFP-1, CRT-0"
``` You should check xorg.0.log for the names of your displays. 

I have a problem too: Can I prevent games using the wrong metamode for fullscreen? When I put ```
"CRT 1280x1024, DFP NULL"
``` as first metamode, games will use it but I don't know how to use both displays for the desktop. 
I already tried adding ```
"CRT 1280x1024, DFP 1280x1024" 
``` as a second metamode.

---

### Post by kruppe on 2007-05-21
Thanks all, this seemed to work perfectly. Now off to Beryl country.

---

### Post by frock on 2007-05-24
I just purchased 2 new lcd widesceen monitors

Everything seems to work perfect, the only problem Im having is  -

With my old monitors when you maximized something it maximized on one screen, now it maximizes across both monitors, also sometimes windows open up in between screens which is annoying.

My gnome menu is also stretched across both monitors when before it would just stretch across one.

Any help would be appreciated.  I am running my new monitors at 1440x900 thanks.

---

### Post by taliosfalcon on 2007-05-27
> **dvazriel said:**
> Okay i have two problems with twinview. 

1-) Everytime i reset my computer or X, it defaults back to single screen ( and yes i have both screens on ). I have to go back to nvsettings and enable it again.

2-) When i maximize, it spans the window across both screens. Anyway to make it just maximize to the parent screen?

thanks.

the only way i've found to do this is setting it to run two seperate X windows, one on each monitor..but this tends to make my xorg.conf randomly blow up for some reason..i also hate how twinview spans the lower and top bars across both screens, and stretches them horribly..anyone know any way to change that and the aofre mentioned window mode with twinview?

---

### Post by B3rt on 2007-05-27
> **frock said:**
> I just purchased 2 new lcd widesceen monitors

Everything seems to work perfect, the only problem Im having is  -

With my old monitors when you maximized something it maximized on one screen, now it maximizes across both monitors, also sometimes windows open up in between screens which is annoying.

My gnome menu is also stretched across both monitors when before it would just stretch across one.

Any help would be appreciated.  I am running my new monitors at 1440x900 thanks.

I have a simular problem.

I am using 3 screens, 1 connetted to th DVI port of my nvidia 6200AGP en the 2 other screens connected to my other 6200 on the PCI port.
1 is working normal but the other 2 have the same problem as mentioned above, when I maximize something it is spreaded across 2 screens, on the other monitor (first monitor) it works normal

this is my xorg.conf
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:56:12 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Hitachi CML174SX"
    HorizSync       24.0 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Philips 170C4"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    BusID          "PCI:2:2:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1280x1024_75 +0+0; 1280x1024 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1280x1024_75 +1280+0, DFP: 1280x1024_75 +0+0; CRT: 1024x768 +0+0, DFP: NULL; CRT: 800x600 +0+0, DFP: NULL; CRT: 640x480 +0+0, DFP: NULL"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

---

### Post by slapys on 2007-05-28
Hi everyone -

I am running two 19" LCD monitors, both 1280x1024 native resolution, connected to an nVidia GeForce 5250 graphics card, one with a VGA connection and one with DVI. I just upgraded from Edgy to Feisty, and discovered the new nvidia-settings dialog. I was able to get TwinView to recognize my monitors correctly in Edgy, but now that I've upgraded, the nvidia-settings will only recognize the monitor connected with VGA as 800x600 resolution. I've tried all the xorg.conf edits in this thread - they either do nothing, or cause X to fail to load, requiring me to restore my xorg.conf by typing sudo nvidia-xconfig --twinview. Is there any way I can get my monitor running at its native resolution?

---

### Post by Cows on 2007-05-29
Thanks this tut worked like a charm :). 

[http://s6.photobucket.com/albums/y213/Nibbler26/?action=view&current=Screenshot-1-2.png](http://s6.photobucket.com/albums/y213/Nibbler26/?action=view&current=Screenshot-1-2.png)

---

### Post by Sir P on 2007-06-01
Hi ziox, good work on the useful thread, cheers..

have a problem with it though... trying to get daul monitors .. the second monitor is a flat screen Acer monitor... when im at the console it will show on both screens but when startx the second monitor losses image "signal not supported"

Il post my xorg below, if anyone has any ideas it be much apperciated

many thanks
Sir P :D

> 
Section "Device"
        Identifier      "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"
Option "UseEdidFreqs" "True"
Option "MetaModes" "1024x768,1024x768"
Option "UseDisplayDevice" "DFP" 
EndSection



additionally- now, i notice errors when startx closes... unable to open device /dev/webcom - if that helps?

---

### Post by Ziox on 2007-06-02
Sir P: You need to install the binary nvidia driver. On Feisty go to System>Admin.>Restrict Drivers Manager and then enable your card's driver. Reboot and retry the tutorial.

Good luck!

Ziox

---

### Post by rghering on 2007-06-05
I have done all I can find on making this work. I am trying to run a FX 5600 with DVI and CRT to 2 acer AL1715 monitors. I get both desktops in view, however the secondary display is unaccessible, and is nearly an exact replica of the first display including menubars etc, minus desktop icons. can anyone please help me here?

I have this same setup at home using a FX 6200 Turbo with dual 19's and it works fine. PLEASE HELP.

Ryan

---

### Post by Snyper64 on 2007-06-05
rghering please post a copy of your xorg.conf file so that we may see if you have any errors or have missed anything. Also make sure you have the Nvidia driver downloaded for your card.

---

### Post by rghering on 2007-06-05
Below is a copy of my xorg.conf, I have loaded and reload the nvidia driver many times used the standard nvidia-glx nvidia-glx-new and nvidia-glx-legacy (of course removed using the purge option).

Ryan


> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVidia GeForce FX 5600"
    Driver         "nvidia"
    Option "TwinView" "True"
    Option "TwinViewOrientation" "LeftOf"
    Option "UseEdidFreqs" "True"
    Option "MetaModes" "1280x1024,1280x1024,1024x768,1024x768"
    Option "UseDisplayDevice" "DFP" 
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "ATI"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "0"
EndSection

---

### Post by rghering on 2007-06-08
Can anyone help me with this?

---

### Post by Snyper64 on 2007-06-08
Sorry about the wait. I'm not that famillier with Nvidias twinview but if you want to set up a dual desktop(which I personally prefer over twinview)  than I can help with that. Just copy what I have below into you Xorg.conf file and make adjustments where necessary such as your connection type for you monitor and your resolution:

Section "ServerLayout"
    Identifier      "Xinerama"
        Screen          0 "Default Screen[0]" 0 0
        Screen          1 "Default Screen[1]" RightOf "Default Screen[0]"
    EndSection

Section "Device"
        Identifier      "Device[0]"
        Driver          "nvidia"
        Screen          0
        VendorName      "Nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"   "true"
        Option          "UseEdidFreqs"  "true"
EndSection

Section "Device"
        Identifier      "Device[1]"
        Driver          "nvidia"
        Screen          1
        VendorName      "Nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"   "true"
        Option          "UseEdidFreqs"  "true"
EndSection

Section "Monitor"
        Identifier      "TFT Monitor"
        Option          "DPMS"
        VertRefresh     43-60
EndSection

Section "Monitor"
        Identifier      "CRT Monitor"
        Option          "DPMS"
        HorizSync       28-130
        VertRefresh     43-100
EndSection

Section "Screen"
        Identifier      "Default Screen[0]"
        Device          "Device[0]"
        Monitor         "TFT Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Default Screen[1]"
        Device          "Device[1]"
        Monitor         "CRT Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           24
                Modes           "1280x720"
        EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

If you have anymore problems or questions feel free to ask.

---

### Post by Ziox on 2007-06-08
> **rghering said:**
> Can anyone help me with this?

Change Device "ATI" in the Screen Section to Device "NVidia GeForce FX 5600"

---

### Post by rghering on 2007-06-08
I did as suggested and both screens did come up, however they were very slow, and the secondary screen was just a grey cross grid, no background etc, could not right click on it etc etc.

Any other ideas?

Ryan

---

### Post by Snyper64 on 2007-06-08
Post up your newest copy of your xorg.conf. Maybe you just misplaced an option or forgot something.

---

### Post by boralyl on 2007-06-08
Ok so I installed the nvidia restricted drivers and am able load X on my main monitor using the nvidia driver.  The 2nd monitor is connected to the same video card, and shows the same information as the main until X starts.  Then it says no signal input.

Looking in my Xorg.0.log I see this pertinent info:
```

(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.69.51
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     Acer AL1714 (CRT-0)
(--) NVIDIA(0): Acer AL1714 (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Option "UseDisplayDevice" "CRT" converted to "CRT-0".
(WW) NVIDIA(0): TwinView requested, but only 1 display devices found.
(II) NVIDIA(0): Assigned Display Device: CRT-0

```

So it makes it sound like it only detects the main monitor.

Here are the relevant sections of my xorg.conf:
```

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       22.0 - 82.0
    VertRefresh     57.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce FX 2500"
    Driver         "nvidia"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "LeftOf"
    Option         "ConnectedMonitor" "crt"
    Option         "UseEdidFreqs" "True"
    Option         "Metamodes" "1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 1024x768,1024x768; 800x600,800x600; 1280x1024,NULL; 1024x768,NULL"
    Option         "SecondMonitorHorizSync" "30-80"
    Option         "SecondMonitorVertRefresh" "55-75"
    Option         "UseDisplayDevice" "CRT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce FX 2500"
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
        Viewport    0 0
        Depth       24
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
    EndSubSection
EndSection

```
Anyone see anything obvious, or is there any other information I can provide?  Thanks in advance.

---

### Post by Snyper64 on 2007-06-08
Are both of your monitors connected through VGA? Anyways try removing your connected monitors option, you should only need this option if you are going through a kvm or have an older card that can't detect what is connected to it.

---

### Post by boralyl on 2007-06-09
ok I commented out the line you are referring to, and decided to comment out everything in that section except for enabling twinview.  And magically it works, I believe it was because the 2nd monitor didn't support one of the resolutions.  The only problem is the resolution is ugly, icons are huge.  I'd love to have both 1280x1024.  I know my main monitor supports it, but I 'm wondering if the 2nd one does or doesn't.  If I use only 1280x1024 for the meta modes, only the main monitor works.  So based off of that I am assuming it doesn't support that resolution, even though the website reccomends 1280x1024 for the monitor.  It's maybe a year and 1/2 old 17" lcd monitor, so I can't imagine it wouldn't support it.  I would be fine with having the 2nd monitor at a smaller resolution, but it doesn't look like you can have two different resolutions for your monitors.  

Regardless something is off, because the only resolution I can select from kcontrol is 1600 x 600, aka each monitor is 800x 600.

My revised Xorg.conf:
```

Section "Device"
    Identifier     "NVIDIA GeForce FX 2500"
    Driver         "nvidia"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "LeftOf"
    #Option         "ConnectedMonitor" "crt"
    #Option         "UseEdidFreqs" "True"
    #Option         "Metamodes" "1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 1024x768,1024x768; 800x600,800x600; 1280x1024,NULL; 1024x768,NULL"
    Option         "SecondMonitorHorizSync" "30-80"
    Option         "SecondMonitorVertRefresh" "55-75"
    #Option         "UseDisplayDevice" "CRT"
EndSection

.
.
.

    SubSection     "Display"
	Viewport    0 0
        Depth       24
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "800x600"
    EndSubSection

```

Any ideas on how to get a larger resolution then 800x600 on each monitor?

---

### Post by boralyl on 2007-06-09
I also wanted to add, that when I restart X via Ctrl + Alt + Backspace, the login screen looks great, both monitors are at 1280x1024.  But as soon as I login the screen flashes, then the loading KDE screen and the other monitor have switched back to 800x600.

---

### Post by Snyper64 on 2007-06-09
Try changing the metamodes option to "1024x768; 1024x768" and tell me if both monitors load with 1024x768 for their resolutions.

---

### Post by boralyl on 2007-06-09
I found the solution.  I created a Xorg.conf file with the folloing command:
```
sudo nvidia-xconfig --twinview
```

And then compared it to my config file.  The only difference I noticed was the following:
```

Option         "MetaModes" "nvidia-auto-select, nvidia-auto-select"

```

After adding this it seems to auto select the maximum resolution, making me a happy camper, hopefully this helps someone else.  :D

Thanks for your assistance Snyper64

---

### Post by Snyper64 on 2007-06-09
Your welcome, enjoy your dual monitors.

---

### Post by Tim T on 2007-06-09
I first saw this right after coming to ubuntu, and have since used this 4 times, the most recent of which is right now! I love the recent update, it's so simple now! Thank you for all the information.

---

### Post by oliveri on 2007-06-17
I've been trying and failing both with the GUI and the manual method.  The second monitor is an LCD-TV with a 1360x780 resolution. The first is a monitor with a 1680x1050 resolution.  The driver keeps mapping the 1680 resolution onto both -- the TV shows the upper-left hand side of the desktop, cutting off the right side and bottom. What am I doing wrong? Thanks for any help.

[FONT="Courier New"]
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7950 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: 1680x1050_60 +0+0, DFP-1: 1360x768_60 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection[/FONT]

---

### Post by steveneddy on 2007-06-17
I use an extra monitor with my laptop and I really like the nvidia-settings gui. It really helps.

---

### Post by chasetoys on 2007-07-02
can someone take a look at my xorg conf file?  i could not get this working even though i followed the instructions

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:56:12 PST 2006
# i have a geforce fx 5200 and i'm trying to get dual displays working
# i've already tried with twinview, but twinview couldn't detect my second lcd properly (set a max resolution to 800x600, so I tried Xinerama)... which you can see below
# this config file makes my first monitor fine (1280x10240)... but i get no output from my second monitor (that should also be 1280x1024".... both monitors are lcs with vga connections only
# ideas?  thanks!

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option "Xinerama" "true"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "TVT FCT1904Z2"
    HorizSync       24.0 - 80.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "VisonLCD"
    HorizSync       24.0 - 81.0
    VertRefresh     56.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
Screen 0
Option "DDCMode" "True"
Option "MonitorLayout" "CRT,CRT"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
Screen 1
Option "DDCMode" "True"
Option "MonitorLayout" "CRT,CRT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    #Option         "TwinView" "1"
    #Option         "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: nvidia-auto-select +1280+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    #Option         "TwinView" "1"
    #Option         "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: nvidia-auto-select +1280+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by jerydstrom on 2007-07-02
Can no longer open terminal window to get back to nVidia GUI.  Followed your instructions for getting two monitors working with my nVidia card - all went well until I checked a box on the nVidia GUI called "Xtender" or some such and now I cannot reopen a terminal window to get back to the GUI (or do anything else).  Any guidance on this??

---

### Post by Snyper64 on 2007-07-02
Chasetoys, try making your layout look more like mine but just with your hardware settings:

```
Section "ServerLayout"
    Identifier      "Xinerama"
        Screen          0 "Default Screen[0]" 0 0
        Screen          1 "Default Screen[1]" RightOf "Default Screen[0]"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Device[0]"
        Driver          "nvidia"
        Screen          0
        VendorName      "Nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"   "true"
        Option          "UseEdidFreqs"  "true"
EndSection

Section "Device"
        Identifier      "Device[1]"
        Driver          "nvidia"
        Screen          1
        VendorName      "Nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"   "true"
        Option          "UseEdidFreqs"  "true"
EndSection

Section "Monitor"
        Identifier      "TFT Monitor"
        Option          "DPMS"
        VertRefresh     43-60
EndSection

Section "Monitor"
        Identifier      "CRT Monitor"
        Option          "DPMS"
        HorizSync       28-130
        VertRefresh     43-100
EndSection

Section "Screen"
        Identifier      "Default Screen[0]"
        Device          "Device[0]"
        Monitor         "TFT Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Default Screen[1]"
        Device          "Device[1]"
        Monitor         "CRT Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           24
                Modes           "1280x720"
        EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by chasetoys on 2007-07-02
Hey I really appreciate the suggestion Snyper64.  

So I tried your setup (I think the magic piece was BusID: PCI:... etc.)  ... and i got output on my second monitor.

however, even though i told it to do 1280x1024 on my second monitor .... it only did 800x600... :( same problem I had with it when i tried twinview.

any suggestions?  i've already spent 5 or so hours on this  :(

---

### Post by Snyper64 on 2007-07-03
Try going into your screen resolution and changing your second monitor to 1280x1024 resolution. I had the same problem and this fixed it.

---

### Post by ps851112 on 2007-07-03
HHHEEELPPP ME!!!!!!
I have finally given up, played with the xorg.conf file for about 2 weeks now off and on.  
I have gotten both LCD's to display but my right display only displays at 800x640 H:37khz V:60hz while my left displays at 1280x1024 H:79khz V:75hz.
I am trying to get my right display the same as my left display.
What I have tried doing is manually setting the resolution as well as the H and V sync.  
When i do this it makes my left display extremely large so when i move the pointer to one side of the screen the desktop starts to move, also my right display turns off.
Nvidia Settings does not give me the option to change the resolution for my right display. #-o
Ubuntu 7.04 Feisty Fawn x64 v: 2.18.1
Here are my settings
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Thu Nov  9 17:56:28 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL1714"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: nvidia-auto-select +1280+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

---

### Post by Snyper64 on 2007-07-03
I've never had much luck with twinview, try doing a dual desktop setup like mine 4 posts above.

---

### Post by ps851112 on 2007-07-04
Oh man i finally got it working.  Stuck with Twinview setup and decided maybe its the driver that came with Feisty.  So i installed Automatix and selected to install the Nvidia driver it provides, Manually set the Resolution for both monitors and now it works!
GOOD BYE WINDOWS, Hello VMWare Server lol.  :D

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Thu Nov  9 17:56:28 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL1714"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1280x1024 +0+0, CRT-1: 1280x1024 +1280+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by hpf1979 on 2007-07-06
Good guide.

However, I have a problem which is really annoying:

Every time I boot up Ubuntu with Twin view, my right screen is not accessible (I can see that it's there, e.g. background image is there, but I cannot move the mouse pointer to that screen, only the left one.)
Then I run the Nvidia settings, and it says I'm not using the correct drivers and I need to run nvidia-xconfig as root and then restart X. This, however does not solve the problem.

Then I have to go through a process where I kill the /tmp/.X0-lock, stop gdm, start gdm, run xinit a couple of times as root, and then I can use startx, and finally (and mysteriously) it just works. I have not found exactly how and what sequence makes this work.
Anyone else have this problem?

I run Feisty 7.04 with NVIDIA drivers: 100.14.09, this is on a Dell XPS M170 with Nvidia GeForce Go 7800 GTX

---

### Post by Snyper64 on 2007-07-08
What program did you use to install your Nvidia drivers? If you manually installed the drivers try downloading Envy and uninstalling the driver and reinstalling the driver through Envys automated process.

---

### Post by hpf1979 on 2007-07-09
I used Envy to install..

---

### Post by hpf1979 on 2007-07-10
I found out just now that if I go to tty1, log in, su, then run nvidia-xconfig, kill /tmp/.X0-lock, and then run startx, it works! But the other X is still running on tty7 and only has one active screen. tty9 with X works on both screens. I am just happy it works, but it is a bit annoying..

---

### Post by hamburglar6 on 2007-07-10
I am having some problems getting twinview or separate desktops working.  My video card has one VGA port and one DVI, whichever monitor I have connected to the DVI one won't work.  I have installed the nvidia driver with Envy, and if it matters, I am using the 64 bit version of Feisty.  Here is my xorg.conf:

```

  # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Wed Jun 13 16:54:14 PDT 2007

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Wed Jun 13 16:54:50 PDT 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony SDM-S51"
    HorizSync       28.0 - 61.0
    VertRefresh     48.0 - 65.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 LE"
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: 1024x768 +0+0, DFP: 1024x768 +1024+0; CRT: 800x600 +0+0, DFP: nvidia-auto-select +800+0; CRT: 640x480 +0+0, DFP: nvidia-auto-select +640+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "True"
    Option         "MetaModes" "nvidia-auto-select, nvidia-auto-select"
    SubSection     "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```


Thanks!

---

### Post by MetalGeek on 2007-07-19
Hi, Just hoping you guys could help out a Ubuntu n00b with your knowledge.

I just installed Ubuntu, and I am running an NVidia 7600GS PCI-E graphics card.

Now, I am looking to have a dual monitor set up (using a ProView 22" widescreen through a DVI, and a Dell 20" through VGA), but I have encountered several problems:

1. Whenever I do *anything* with 
```
gksudo nvidia-settings
```
it always ends up 'blanking out' my terminal (in that, I open the terminal and it appears as a white block. However, it still works, I just can't see the input/output)

2. When I enable Xinerama, it 'kills' my terminal (it will begin to load, then just...not)

3. For some reason, It doesn't allow me to set my ProView monitor as my primary monitor (this could just be due to n00bish configuration on my part).

4. When I input the code suggested in the original post, (see below), it stopped XServer from loading all together.

> Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"   
Option "UseEdidFreqs" "True"
Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
Option "UseDisplayDevice" "DFP"

The following is a paste from my xorg.conf file:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G70 [GeForce 7600 GS]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by sameoldude on 2007-07-21
hi, i have a vaio laptop, has a geforce mx4, works perfectly with extended desktop on xp, i tried the code 
> gksudo nvidia-settings

and the console returned the following:

> ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.




the desktop effects used to work perfectly, now they're gone.
nvidia x server settings shows some ticking boxes and never mentions anything about monitors. what went wrong?

---

### Post by Ziox on 2007-07-23
make sure that you have nvidia-glx driver installed correctly

---

### Post by Jonah on 2007-07-26
@MetalGeek:
How did you install the nVidia drivers? If you didn't use [Envy](http://www.albertomilone.com/nvidia_scripts1.html) it might be worth uninstalling the driver and then reinstalling with Envy.

If you do succeed in getting TwinView working, here's how to make the ProView your primary monitor. Add the following line to the "Device" section of your xorg.conf (or to the "Screen" section, if you prefer):
```
Option "TwinViewXineramaInfoOrder" "DFP, CRT"
```
This will make whichever monitor is connected to the DVI port the primary monitor. (It took me quite a bit of poking around to find this setting. It would be nice if it could be added to the first post.)

---

### Post by RubberSideUp on 2007-07-27
Ok, so i followed the guide and i´m now using dual monitors. brilliant! However now i can´t open terminal :\ when i try to run it the taskbar says ¨terminal starting¨ then dissapears. no terminal appears.

Ideas anyone?

Edit - All fixed, needed to disable Xinerama.

---

### Post by jba6511 on 2007-07-27
did anyone ever resolve the issue of the screen being stretched across both monitors? I have a nvidia 7600 gt and would like the screens to be more like windows setup, with the secondary as a place to drag and drop windows to.

---

### Post by geek777 on 2007-08-03
Hi, I am trying to get Twinview with Xinerama to pay nicely with  triple head.

I am using 2 dual vga out FX5500 pci cards (4 monitor capable, only using 3 displays).

3 Dell 1970FP displays (running at 1280x1024).

Have 100.14.11 nvidia drivers installed and xorg is configured in a working fashion however I can only run Xinerama and NOT Twinview.

I want Twinview as I understand that it will resolve my performance rendering problems with apps like Firefox and Thunderbird (terrible image tearing while dragging).  According the below  thread....there is an xorg hack to allow for triple head Xinerama and Twinview....although the instructions for the fix are non Ubuntu/Debian friendly (damn those Fedora people !! ;-) )

Thread which describes my problem and a possible solution although I can't establish how to fix it on Ubuntu 7.04.

[http://www.nvnews.net/vbulletin/showthread.php?t=85604](http://www.nvnews.net/vbulletin/showthread.php?t=85604)

Is there an easy way (or at least detailed) in which I can download and compile Xorg for Ubuntu 7.04, implement/apply JaXXoN's patch and still have X work afterward??

Thanks for any help or suggestions.

Mike

---

### Post by mattgaunt on 2007-09-15
I followed the how-to using the nVidia GUI to fix the xorg.conf file, it worked.

But i have a tiny bug in it, if u move the mouse to the bottom of the screen, the screen kind of scrolls down, does anyone know why this is??

Edit : Solved it - Gnome resultion was set to size of both screen widths, but height was 960 instead of 900, so this worked for me thanks for the how to

---

### Post by J77 on 2007-09-18
The manual way of TwinView seemed to work for me...

I've got a nvidia quadro graphics card, machine is a fujitsu siemens r630...

**Am I using the right method?**

---

### Post by J77 on 2007-09-18
One small thing:

I have one monitor going into the standard VGA port of my workstation, the other into the digital port via a VGA adapter from the monitor.

As both monitors are digital, I'd rather use that...

However, using one fully digital (ie. the one without the adaptor) and one VGA doesn't work.

Any ides?

---

### Post by qweac on 2007-09-18
I need help! I have a laptop with GeForce 7600go card and a resolution on 1280x768. I want to use my TV to watch movies on from the laptop. I now get picture on both screens in clone, but since my laptop is widescreen and my TV is not, I can't have it that way! I want to use "leftof" but it do not work! It works perfectly in the "login" screen, but once my password is entered correctly, and the desktop appears, the TV turns black. Why? This is a part of my X:

Section "Device"
Identifier "Generic Video Card"
Driver "nvidia"
Option "NoLogo" "1"
Option "ConnectedMonitor" "crt, crt"
Option "NoPowerConnectorCheck"
Option "TwinView" "1"
Option "Metamodes" "1280x768,800x600; 1024x640,800x600; 1280x768,NULL; 1024x640,NULL"
Option "SecondMonitorHorizSync" "31-50"
Option "SecondMonitorVertRefresh" "30-50"
Option "TwinViewOrientation" "LeftOf"
EndSection

Thanks!

---

### Post by bensode on 2007-09-21
Made my shorts wet when I saw this and it worked.  Well sort of worked.  I'm able to do the big desktop split across both monitors but I wanted to try having separate X screens.  When I attempt to save the X config file I get this

> 
ERROR: Unable to determine valid vertical refresh ranges for display device
       'Sharp' (GPU: Quadro FX 350M)!


ERROR: Failed to add display device 'Sharp' to screen 1!


ERROR: Failed to add X screen 1 to X config.


ERROR: Failed to add X screens to X config.


ERROR: Failed to generate an X config file!





I can save the config using the TwinView option with no problems so what is it that I'm not doing correctly?  I'm running the Quadro FX 350M on a Dell Precision M65 with 7.04 Desktop edition.

---

### Post by kuahyeow on 2007-09-27
```
gksudo nvidia-settings
``` is really the easy part of this all :)

My main trouble was finding and installing the right driver. The link to install the binary driver had a helpful list of drivers supported in the current version.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Mine (Geforce 8300 GS) was not. However it is supported in the driver released by Nvidia. Tried installing that using the manual Nvidia way, did not work (X could not start - some API mismatch ?).

Then I found Envy

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

That installed everything correctly!

---

### Post by boast on 2007-10-24
Is twinview only for dual-head monitors? I feel like I get poor video performance with xinerama.

And when trying to enable twinview I get the following in logs:
```

[color=red]
(**) NVIDIA(1): Option "TwinView" "True"
(**) NVIDIA(1): TwinView enabled
...
(WW) NVIDIA(1): TwinView requested, but only 1 display devices found.
[/color]

```

---

### Post by crossan007 on 2007-10-28
When i try to use the nvidia-settings graphical tool  to set up  twinview, it says 

"failed to set metamode (1) 'CRT-0: 1280x1024 @ 1280x1024 + 1024+0, CRT-1: 1280x1024 @ 60 @1280x1024 +0+0' (Mode 2304x1024, id:64) on X screen 0" would you like to remove this meta mode.   

when i remove it, it just goes through a list of meta modes that dont work.  i have (2) 17 inch screens, and they work in dualview in windows XP at 1280x1024 resolution at 60 Hertz, so they should work like that in linux too, no? 

I have managed to get both screens running (at different resolutions?), im not really sure how, but it seems that the secondary screen was running a native 1024x768 resolution, but i could pan around on the screen which seemed to be 1280x1024.  Like i said, im not sure how i did it.  

so far i love the general feel of Ubuntu, but i really want my duial screen setup.

Any help would be appreciated,
Charles Crossan

---

### Post by tarotoast on 2007-11-01
> **crossan007 said:**
> When i try to use the nvidia-settings graphical tool  to set up  twinview, it says 

"failed to set metamode (1) 'CRT-0: 1280x1024 @ 1280x1024 + 1024+0, CRT-1: 1280x1024 @ 60 @1280x1024 +0+0' (Mode 2304x1024, id:64) on X screen 0" would you like to remove this meta mode.   

when i remove it, it just goes through a list of meta modes that dont work.  i have (2) 17 inch screens, and they work in dualview in windows XP at 1280x1024 resolution at 60 Hertz, so they should work like that in linux too, no? 

I have managed to get both screens running (at different resolutions?), im not really sure how, but it seems that the secondary screen was running a native 1024x768 resolution, but i could pan around on the screen which seemed to be 1280x1024.  Like i said, im not sure how i did it.  

so far i love the general feel of Ubuntu, but i really want my duial screen setup.

Any help would be appreciated,
Charles Crossan

I'm actually looking for way not to use panning but able to access dead space. But maybe changing the metamodes line to something like this will work?

```
Option          "metamodes"     "CRT-0: 1280x1024 +0+0, CRT-1: 1360x768 
+1280+0; CRT-0: 1280x1024@60 +0+0, CRT-1: nvidia-auto-select +1280+0"

```

It's working on mine ;)

---

### Post by Jovec on 2007-11-08
Experiencing the following problem myself, I'd thought I'd pass along what I've learned.

Regarding **Option "UseDisplayDevice" "string"** doesn't do what many of you think it is supposed to do.Instead, what many of you are looking for is:

**Option "TwinViewXineramaInfoOrder" "string"**

When to use this?

Example:  You have one DVI port and one D-Sub port on your graphics card, and the nvidia driver will use the monitor connected to the D-Sub port as the primary display (login window, default panels, etc).  Instead, you want the monitor connected to the DVI port to be the primary monitor.  The fix is to use:

Option "TwinViewXineramaInfoOrder" "DFP, CRT"

Example 2:  You have two DVI ports on your video card and two monitors connected to them, but the primary monitor is the wrong one.  You can switch the DVI ports the monitors are connected to, or you can use:

Option "TwinViewXineramaInfoOrder" "DFP-1, DFP-0"

Notes:  The nvidia driver provides its Xinerama extension info by default, unless you manually disable it with Option "NoTwinViewXineramaInfo" "1".  You'll also want to make sure the you aren't trying to load xorg's Xinerama's extension as it conflicts.

More notes:  What is Xinerama?  Xinerama is an extension that tells the x-server information about the connected monitors.  Assume two monitors each running at 800x600 (for easy math).  Without Xinerama, the X-server and window manager just see a single 1600x600 display, and will stretch your windows across both monitors mindlessly, for example, when maximizing a window.  With Xinerama, the window manager will know that the 1600x600 resolution is really two 800x600 monitors, and will place and maximize windows more intelligently (ie. on one, although you can still manually position windows between both monitors)

---

### Post by SilverJester on 2007-11-27
I want to setup a "clone" dual monitor system so that I can watch movies/games tv, and do everything else on my monitor. I have a 7600gt using dvi to the monitor and a dvi/vga adapter to connect to the tv. I have been trying for days to get it to work and nothing sems to work. So here is what I have so far:

1) I ran the command "sudo dpkg-reconfigure xserver-xorg" to start with a clean xorg.conf file.
2) I tried to run the command "gksudo nvidia-settings" but got this error message: "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "
3) So I ran the command "sudo nvidia-xconfig"
4) Still no luck with a gui nvidia-settings program (same error message even after rebooting) :(
5) So I started editing the file manually, and this is where I'm at now. The computer works fine with my monitor but doesn't seem to send any signals to my tv. Any suggestions?

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Oct  4 10:33:51 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
EndSection

Section "Monitor"
    Identifier     "HP w22"
    HorizSync       30.0 - 130.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver         "nvidia"
	Option "TwinView" "True"
	Option "TwinViewOrientation" "Clone"
	Option "UseEdidFreqs" "False"
	Option "Metamodes" "1680x1050,1680x1050; 1280x800,1280x800; 1024x768,1024x768; 1024x640,1024x640; 1680x1050,NULL; 1440x900,NULL; 1280x800,NULL; 1024x640,NULL"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "HP w22"
    DefaultDepth    24
    Option         "UseFBDev" "true"
    SubSection     "Display"
		Viewport 0 0
        Depth       24
        Modes      "1680x1050" "1280x800" "1024x768" "1024x640"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier		"Default Layout"
	Screen 0		"Default Screen" 0 0
    InputDevice		"Generic Keyboard"
    InputDevice		"Configured Mouse"
	#Option			"Xinerama" "Off"
EndSection

```

Sorry for the long post, but I figured better chance of getting help if I posted the whole file. I'm not sure why I can't run the nvidia settings program (as you can see that is the driver I am using, installed with envy).
I also noticed that the failsafe safe settings will clone and use both the monitor and tv. I tried a little experiment starting with that file and changing the driver to nvidia (failsafe is versa), but then it would not let me log in...after the logging in (at the gui login screen), it would start to load the desktop, then restart X bringing me back to the login screen.

---

### Post by dartworth on 2007-12-02
nm

---

### Post by dartworth on 2007-12-02
nm

---

### Post by bond17_007 on 2007-12-04
Hi, 
I am facing a real annoying problem and I do not know how to resolve it. 

I have a nvidia 7900GS. I am connecting two monitors one 1680X1050 and 1280X1024.

I used the nvidia-settings to set up my xorg.conf. 

everything is great until I  take screen shots of a 3D cube.
 
when I rotate my cube i see that parts of the cube are not in-sync.
I have attached a screen shot to show what I am seeing. 

Can you point out what am I missing here??

PS: I had set up exact same thing on my OLD HDD and it worked fine. images were in-sync. However, I just got a new HDD for ubuntu, I did a fresh install on it. 

To solve this issue I have also copied over the xorg.conf file from the Old Hdd to new one but still the same issue.

---

### Post by belfasttim on 2007-12-11
Hi guys-- I am trying to get my dual monitor setup configured, and having a hell of a time.

I have two (basically) identical Dell flat panel monitors I want to run off my laptop docking station (hopefully the docking station is not the issue). One is a 1905FP, one is 1907FPt

Because of the way the docking station is built, theres one analog and one digital out. So one monitor is in CRT mode, one in DFP (I hope).

I installed nvidia drivers using envy in my latest try at making this thing work (been trying for days with limited success). The DFP monitor works during bios and boot, but once we get to login it shuts off and the CRT side takes over-- even though the view is only half a screen. So basically it appears twinview is working just not on the DFP monitor.

Initially I had both monitors working, but the CRT side was only showing up at super low resolution. So I rewrote the xorg.conf a dozen times trying various info from this thread, with very little success.

I attach my xorg.conf and xorg.0.log (snipped some from this to meet upload limit) in the hopes one of the gurus can help.

Thanks for taking a look.

---

### Post by bond17_007 on 2007-12-11
Hi there.. 
did u try to manage ur resolution through nvidia settings or one from ubuntu?

u can do it through.

sudo nvidia-settings

things to remember is that you do have to click on "Save Configuration" to have it save it in your xorg.conf file.

hope this helps.

---

### Post by belfasttim on 2007-12-11
> **bond17_007 said:**
> Hi there.. 
did u try to manage ur resolution through nvidia settings or one from ubuntu?

u can do it through.

sudo nvidia-settings

things to remember is that you do have to click on "Save Configuration" to have it save it in your xorg.conf file.

hope this helps.
hi bond--

yeah, I did use the nvidia-settings utility, but while it usually detects the dual monitors initially, on reboot is just loses one of the monitors again. Its very quirky-- sometimes it says I cant configure the dual monitors excepts by doing separate X (not twinview).

thanks for the thought.

---

### Post by bond17_007 on 2007-12-11
hmmm

and u did save the Configuration through the utility.. ie. (click on "Save Configuration" not "Apply" button?)

also did u check the frequency of the monitor if its 60Hz or 75Hz.. not sure if has anything do with it... 

if i understand correctly its two dell monitors, one CRT one LCD but same resolution ?

---

### Post by belfasttim on 2007-12-11
> **bond17_007 said:**
> hmmm

and u did save the Configuration through the utility.. ie. (click on "Save Configuration" not "Apply" button?)

also did u check the frequency of the monitor if its 60Hz or 75Hz.. not sure if has anything do with it... 

if i understand correctly its two dell monitors, one CRT one LCD but same resolution ?

yeah, I did save the config-- still doesn't autodetect the DFP monitor after boot. I htought it might be part of the DPMS setting but that's enabled. Refresh rates are correct.

and yes, you are correct, same basic monitor, same resolution, but since I don't have two DVI outs, I use one analog and one digital out from the docking station.

thanks

---

### Post by belfasttim on 2007-12-12
> **belfasttim said:**
> yeah, I did save the config-- still doesn't autodetect the DFP monitor after boot. I htought it might be part of the DPMS setting but that's enabled. Refresh rates are correct.

and yes, you are correct, same basic monitor, same resolution, but since I don't have two DVI outs, I use one analog and one digital out from the docking station.

thanks

Got it!

I don't have a good answer for anyone why, but I swapped the monitors making the DVI go to the 1905FP and the analog to the 1907FP-- I then reinstalled everything using envy.

I think what was the main problem turned out to be the older monitor may not have been able to send its config settings via EDID over analog while the newer one can.

Or maybe I got lucky. Either way-- damn. That was a fun 3 days.

---

### Post by pettijok on 2007-12-12
So i am rather new to ubuntu and linux in general and im really having some hard times getting my display on my samsung TFT-LCD LN-T4053H. I am working on a sony fs-660/w laptop (GeForce 6200 Go) with a VGA out. I know this is possible because i had it running in XP and loved it. I have been trying to follow the instructions in many different threads but with no success. 

Something that might be note worthy is my TV i think only supports the resolution of 1360x768 @60hz

Any help would be most welcomed. Thanks!

P.S i know my xorg.conf is a bit messy and i apologies. 






 ```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:29:35 PDT 2007
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "Monitor"
    Identifier     "Failsafe Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1280x800"
    HorizSync       31.5 - 50.0
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
EndSection

Section "Monitor"

 # 
    Identifier     "monitor1"
    Gamma           1
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 49.0
    VertRefresh     0.0 - 61.0
EndSection

Section "Device"
    Identifier     "Failsafe Device"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device" # 
    Identifier     "device1"
    Driver         "nv"
    BoardName      "vesa"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Failsafe Device"
    Monitor        "Failsafe Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1280 800
        Depth       24
        Modes      "800x600@60" "1280x768@60" "800x600@56" "1280x720@60" "1280x800@60"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x800 +0+0; 800x600@60 +0+0; 800x600@56 +0+0; 1280x720@60 +0+0"
EndSection

```

---

### Post by Zaff on 2007-12-13
hi everyone, 
this may already have been answered but I didn't find it.
I got twinview working perfectly with my toshiba satellite A100-307 nvidia Geforce 7300. However if my second screen isn't pluged and I turn it on, my main screen display my desktop as if IU had the second screen (on log in I can't see the login input because it's supposed to be on my other screen).
Anyway I can set it up so that it automaticaly displays it right on start up detecting if the second screen is there ? 
Thanks

---

### Post by pettijok on 2007-12-14
Anyone have any ideas on post #252 ? Any ideas or tips would be much appreciated. Thanks.

---

### Post by elcign on 2007-12-14
This updated guide opened my eyes and everything worked beautifully.  All I had to do was use the binary's little program from the console and type "gksudo nvidia-settings" and everything was right there.

---

### Post by lpsmith on 2007-12-18
Using nvidia-settings worked great getting my two monitors to display one big desktop.  The only foible was that clicking the 'apply' button didn't always work, but the 'Save to X Configuration File' worked fine.

However, ideally I would like each monitor to display separate desktops so I can better keep track of my windows.  If I click 'Configure' and then select 'Separate X Screen', it basically gets things set up the way I want, but there are problems.  I tried (for example) to open a new terminal window in the second screen, and it did indeed appear, but without the 'frame' (or whatever it's called--the bit that you can grab to resize the window and has the minimize/maximize/close buttons in the corner).  Messing around with it a bit more once even caused *all* my terminal windows in both screens to spontaneously crash.

The TwinView version works as advertised, so this isn't anything pressing, but it would be nice if it worked.  My main problem now is that I'm not even sure where to start looking, or if this is one of those unused corners of the distribution that I'll need to file a bug report on somewhere.

Thanks for any insight you might have!

---

### Post by oneiota on 2008-01-04
> **Ziox said:**
> 

...

[SIZE=4][COLOR=Red][FONT=Arial Black]MAJOR (and Delayed) UPDATE:
NEW GRAPHICAL METHOD:
[/FONT][/COLOR][/SIZE]With the recent and awesome release of Ubuntu 7.04 Feisty Fawn, (almost) every nVidia card user's dream of dual monitors is just a few clicks away. LITERALLY! 
Here's the basic breakdown:

[INDENT][B][U][COLOR=Red]For users of nVidia cards with driver 9.xxx, there is a GUI application installed to configure X. 

To access the application, enter:
```
gksudo nvidia-settings
```

And configure to your heart's desire! :guitar:

After all the configuration is done, make sure to save the configuration file.


This has put an end to all of my suffering!  Two monitors now running, happily and correctly. Thank you Ziox!

---

### Post by michaee on 2008-01-13
Hi, I'm new to Linux and I got my dual-screen up and running (after some help from a friend :) ), but I my secondary screen (connected via VGA) is stuck in 800x600, something that, although not a tragedy, does beg to be fixed.

My *xorg.conf* file:
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Dec 13 19:10:32 PST 2007


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # Copied manually from other file
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "no"
EndSection

Section "Monitor"

    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       81.0 - 81.0
    VertRefresh     76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    Option 	   "NvAGP" "2"
    Option         "NoLogo" "1"
    Option         "ConnectedMonitor" "DFP, CRT"
EndSection

Section "Screen"

# Removed Option "MetaModes" "800x600,1680x1050"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +800+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Changing the line
```
Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +800+0"
```
To something like:
```
Option         "metamodes" "CRT: 1280x1024 +0+0, DFP: 1680x1050 +800+0"
```
Causes the secondary screen to go blank. I know that it can handle 1280x1024 as I have done it before in windows (and 1680x1050 is the resolution of the primary screen as set by nvidia). Using the nvidia-settings dialog is to no avail either as I can either choose Auto or set it to Off.

--
edit:
By the way, I am on Xubuntu 7.10. The card is a GeForce 7600GS and my screens are a 19-inch 4:3 (Benq FP91G+) and a 22-inch 16:9 (Samsung SyncMaster 225MW) which is my primary one.


--
Edit:
I messed around with the xorg.conf file and got it to work out. In case it could be useful, my *xorg.conf* file is as follows:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Dec 13 19:10:32 PST 2007


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "DefaultKeyboard" "CoreKeyboard"
    InputDevice    "DefaultMouse" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "DefaultMouse"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # Copied manually from other file
    Identifier     "DefaultKeyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "no"
EndSection

Section "Monitor"

    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       80.0 - 80.0
    VertRefresh     75.0
    Option         "DPMS"
EndSection

Section "Device"

#    Option	   "SecondMonitorVertRefresh" "76.0"
    Identifier     "NvidiaCard"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
    Option         "NvAGP" "2"
    Option         "NoLogo" "1"
    Option         "ConnectedMonitor" "DFP, CRT"
#    Option	   "SecondMonitorHorizSync" "81.0"
    Option         "MetaModes" "CRT: 1280x1024, DFP: nvidia-auto-select"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "DefaultScreen"
    Device         "NvidiaCard"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1280x1024 +0+0, DFP: nvidia-auto-select +1280+0"
EndSection


```

---

### Post by indymcse on 2008-01-21
Helo, I am a complete N00b when it comes to LINUX and UBUNTU.  I have a fresh install of UBUNTU 7.10 using the NVIDIA binary drivers from ENVY.  I have a GeForce 8400GS with DVI and VGA outputs.  I have a Dell 2405FPW connected via DV!/VGA cable to the analog input on the monitor from the DVI port on the video card.  I have a Dell 2005FPW plugged into the VGA port on the video card.  I get display on the 2405 fine.  I tried the NVIDIA-Settings app, but that doesn't seem to see my second monitor, the 2005FPW.  Below in the pertinent sections of my xorg.conf file.  Any help would be GREATLY appreciated.

Section "Monitor"
    Identifier     "Generic Monitor"
    VendorName     "Dell"
    ModelName      "Dell 2405FPW (Analog)"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@75" 107.2 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
    ModeLine       "1280x768@75" 103.0 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1440x900@75" 136.5 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    ModeLine       "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
    ModeLine       "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1680x1050@75" 188.1 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1920x1200@60" 193.2 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2405FPW"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8400 GS]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8400 GS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Virtual     1920 1200
        Depth       24
        Modes      "1920x1200@60" "1680x1050@75" "1680x1050@60" "1600x1024@60" "1440x900@60" "1440x900@75" "1280x800@60" "1280x768@75" "1280x800@75" "1280x720@60" "1280x768@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0; 1680x1050@60 +0+0; 1600x1024@60 +0+0; 1440x900@60 +0+0; 1440x900@75 +0+0; 1280x800@60 +0+0; 1280x768@75 +0+0; 1280x800@75 +0+0; 1280x720@60 +0+0; 1280x768@60 +0+0; 800x600@60 +0+0; 800x600@75 +0+0; 800x600@72 +0+0; 800x600@56 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


P.S.  I really want to install KUBUNTU once I get this working.  Will KUBUNTU "inherit" the settings from UBUNTU?

---

### Post by Kejoxen on 2008-01-22
Hi, 

I hate to do this because i'm pretty sure that the answer is buried in this thread somewhere and i know I've seen it mentioned but i can't seem to find it. 

I've got twinview running exactly how i want it with one exception, games that run in full screen mode span both monitors, now while this looks cool (especially in EVE) it pretty annoying, how can i get games to run on only one monitor at a time?

7800GTX dual DVI to two Hyundai L90D+ monitors 1280x1024 (2560x1024).

---

### Post by Kejoxen on 2008-01-22
This is my xorg.conf file as configure by nvidia-settings

> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Failsafe Monitor"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Monitor"

 #   
    Identifier     "monitor1"
    VendorName     "Unknown"
    ModelName      "HIQ L90D+ DVI"
    HorizSync       31.0 - 67.0
    VertRefresh     59.0 - 61.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HIQ L90D+ DVI"
    HorizSync       31.0 - 67.0
    VertRefresh     59.0 - 61.0
EndSection

Section "Device"
    Identifier     "Failsafe Device"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"

 #   
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GTX"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7800 GTX"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Failsafe Device"
    Monitor        "Failsafe Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1400 1050
        Depth       24
        Modes      "1280x1024@60" "1400x1050@60" "1280x960@60" "1024x768@60" "800x600@60" "640x480@60"
    EndSubSection
EndSection

Section "Screen"

 #   
    Identifier     "screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP-0: 1280x1024@60 +0+0; DFP-0: 1280x960@60 +0+0; DFP-0: 1024x768@60 +0+0; DFP-0: 800x600@60 +0+0; DFP-0: 640x480@60 +0+0"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0; DFP-0: 1280x960@60 +0+0; DFP-0: 1024x768@60 +0+0; DFP-0: 800x600@60 +0+0; DFP-0: 640x480@60 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1280+0"
EndSection


---

### Post by vwfix on 2008-01-22
Hi guys can someone please help me set up my dual monitors its my first time messing with xorg.conf
I have a 20 inch dell and a 21 inch viewsonic. the dell is hooked up to the vga on my nvidia 8400 gs and the viewsonic is hooked up to the dvi the issue is Ubunut does not see the viewsonic at all neither does the little nvidia utility. so can some one help me out, here is a copy of my config file.


> # xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Dell"
	Modelname	"Dell 1907FP (Analog)"
	Horizsync	30.0-81.0
	Vertrefresh	56.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"800x600@72"	"800x600@75"	"800x600@56"	"800x600@60"	"640x480@75"	"832x624@75"	"640x480@72"	"1024x768@75"	"640x480@60"	"1024x768@70"	"1024x768@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1600x1200@65"	"1600x1200@60"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "ServerFlags"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

---

### Post by vwfix on 2008-01-23
bump can someone please help me out.

---

### Post by vwfix on 2008-01-23
Also when i try to use the nvidia gui, it always fails to write to xorg.con saying it could not create a back up. And only vga works, i tried hooking up just dvi and did not get anything. only vga works, but in windows both work, so I know the video card is good.

---

### Post by Sam_GR on 2008-01-29
Can somebody help me?I made all the seetings correctly ,but my TV saw me a message."Out of range".I change the resolution but i had the same error.My tv supports resolution of 1360X768.This is my xorg.conf.
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Dec 13 19:10:32 PST 2007

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SONY TV"
    HorizSync       30.0 - 50.0
    VertRefresh     58.0 - 62.0
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6400"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1280x720@60 +0+0, DFP: nvidia-auto-select +0+0; CRT: NULL, DFP: 1280x720@60 +0+0; CRT: NULL, DFP: 800x600@60 +0+0; CRT: nvidia-auto-select +0+0, DFP: NULL; CRT: NULL, DFP: 800x600@56 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


Thanks

---

### Post by aksim on 2008-02-05
Hello everyone!

This is my first post on the forum but I've used it for a source of information and help many times before.  And yes, I'm still a newbie. The reason for posting is that I have not found a working solution to a seemingly uncomplicated matter:

I can only get black and white trough my nvidia GFn6200 card's composite tv-out.

 I've tried every how-to, I've "re-compiled" the xorg.conf,  I've re-installed the nvidia driver, I've used "gksudo nvidia-settings", I've tried everything within the limits of my abilities but no solution yet...

In the xorg.conf file I've tried both "SVIDEO" and "COMPOSITE" options with the only difference being that the "SVIDEO" gives sharper (B n' W) image on my PAL-B 4:3-TV! I'm using an s-video cable with composite-adapter in the graphics card and a scart-adapter in the tv. The cable works so it's not the problem. My monitor is an old LG 17" CRT. I'm running an up-to-date version of Gutsy. The problem originally started when I updated to Gutsy from Feisty. The following xorg.conf is the one that used to work in feisty.

Here's my xorg.conf:

```

Section "ServerLayout"
# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "fi"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "LG 702B"
    HorizSync       30.0 - 60.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG 702B"
    HorizSync       30.0 - 71.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV44A [GeForce 6200]GeForce 6200"
    Driver         "nvidia"
    Option         "UseFBDev" "true"
    Option         "TwinView" "true"
    Option         "TwinViewOrientation" "Clone"
    Option         "TVOutFormat" "COMPOSITE"
    Option         "TVStandard" "PAL-B"
    Option         "SecondMonitorHorizSync" "30-50"
    Option         "SecondMonitorVertRefresh" "60"
    Option         "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;    512x384,512x384"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV44A [GeForce 6200]GeForce 6200"
    Monitor        "LG 702B"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1024x768_70 +0+0, TV: 1024x768 +0+0; CRT: 1024x768_70 +0+0, TV: nvidia-auto-select +0+0"
EndSection

```

---

### Post by aksim on 2008-02-05
I tried yet another fix: re-installed the nvidia driver using [**[COLOR="Blue"]"Envy"[/COLOR]**]("http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu")

No help there, still black and white...
Any thoughts?

Now my xorg.conf looks like this:

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "Screen0" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"0"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"LG 702B"
	Horizsync	30.0	-	60.0
	Vertrefresh	50.0	-	75.0
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Unknown"
	Modelname	"LG 702B"
	Horizsync	30.0	-	71.0
	Vertrefresh	50.0	-	160.0
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV44A [GeForce 6200]GeForce 6200"
	Driver		"nvidia"
	Option		"UseFBDev"	"true"
	Option		"TwinView"	"true"
	Option		"TwinViewOrientation"	"Clone"
	Option		"TVOutFormat"	"COMPOSITE"
	Option		"TVStandard"	"PAL-B"
	Option		"SecondMonitorHorizSync"	"30-50"
	Option		"SecondMonitorVertRefresh"	"60"
	Option		"MetaModes"	"1024x768,1024x768;800x600,800x600;640x480,640x480;    512x384,512x384"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
	Boardname	"GeForce 6200"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV44A [GeForce 6200]GeForce 6200"
	Monitor		"LG 702B"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	Defaultdepth	24
	Option		"TwinView"	"1"
	Option		"metamodes"	"CRT: 1024x768_70 +0+0, TV: 1024x768 +0+0; CRT: 1024x768_70 +0+0, TV: nvidia-auto-select +0+0"
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
```

---

### Post by lakersforce on 2008-02-05
Great post Ziox! Nice and easy! Less is more :)

---

### Post by Sam_GR on 2008-02-23
Hello guys.I am desperated with the vga out of my laptop.i am trying to connect my laptop with a sony 26' LCD but with no success.


That is m xorg.conf.Can somebody help me with my problem?
I have an nvidia 6400 GeForce.Sony Tv is out of range.

Thanks

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Fri Jan 11 15:06:57 PST 2008

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Fri Jan 11 15:05:59 PST 2008
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "true"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us,gr"
    Option         "XkbOptions" "grp:alt_shift_toggle"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "Monitor"
    Identifier     "Failsafe Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1280x800"
    HorizSync       31.5 - 50.0
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "monitor1"
    VendorName     "Sony"
    ModelName      "Sony KL-W7000"
    HorizSync       30.0 - 50.0
    VertRefresh     50.0 - 85.0
    Gamma           1
    ModeLine       "640x400@85" 31.5 640 672 736 832 400 401 404 445 -hsync +vsync
    ModeLine       "640x350@85" 31.5 640 672 736 832 350 382 385 445 +hsync -vsync
    ModeLine       "720x400@85" 35.5 720 756 828 936 400 401 404 446 -hsync +vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1152x768@54" 65.0 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
    ModeLine       "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x720@50" 60.5 1280 1328 1456 1632 720 721 724 741 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SONY TV"
    HorizSync       30.0 - 50.0
    VertRefresh     58.0 - 62.0
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Failsafe Device"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "device1"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 6 Series"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "UseEdidFreqs" "True"
    Option         "MetaModes" "1280x768,1280x768; 1024x768,1024x768"
    Option         "UseDisplayDevice" "TV"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"

# Removed Option "TwinView" "True"
# Removed Option "MetaModes" "1280x768,1280x768; 1024x768,1024x768"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6400"
    Option         "TwinViewOrientation" "RightOf"
    Option         "UseEdidFreqs" "True"
    Option         "UseDisplayDevice" "TV"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Failsafe Device"
    Monitor        "Failsafe Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1280 800
        Depth       24
        Modes      "1280x800@60" "1280x720@60" "1280x768@60" "800x600@60" "800x600@56"
    EndSubSection
EndSection

Section "Screen"

	# 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x768@60" "1280x720@60" "1280x854" "1280x720@50" "1152x768@54" "1280x800@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56" "720x400@85" "640x350@85" "640x400@85"
    EndSubSection
EndSection

Section "Screen"

	# Removed Option "TwinViewXineramaInfoOrder" "CRT-0"
	# Removed Option "metamodes" "CRT: NULL, DFP: 1280x720@60 +0+0; CRT: NULL, DFP: 800x600@60 +0+0; CRT: nvidia-auto-select +0+0, DFP: NULL; CRT: NULL, DFP: 800x600@56 +0+0; CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +0+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT: 1280x768 +0+0, DFP: nvidia-auto-select +0+0; CRT: nvidia-auto-select +0+0, DFP: NULL"
# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by Sam_GR on 2008-02-25
plz help

---

### Post by umefarooq on 2008-04-15
Hi i tried this method but nothing happen here is my conf file.

```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8500 GT]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Option "TwinView" "True"
	Option "TwinViewOrientation" "RightOf"   
	Option "UseEdidFreqs" "True"
	Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
	Option "UseDisplayDevice" "string" #replace 'string' with either 'DFP' (Digital flat panel connected via DVI port), 'CRT' (any monitor that is connected via VGA ports), or 'TV'
EndSection

Section "Monitor"
	Identifier	"T710SH"
	Option		"DPMS"
	HorizSync	30-71
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8500 GT]"
	Monitor		"T710SH"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```
tell me what is wrong in it or i have to try any other method

---

### Post by ezland00 on 2008-04-24
Hello,
This is my first time using Linux, i want to run dual monitors set.  i currently have 2 pci-e cards in my system.  first one is 7600GT and the second one is 6600gt.  i have using 2 samsung 940bw on 7600gt and Sharp HDTV LCD tv on 6600gt.  Can someone please send me the codes how to run my setup.

---

### Post by evilbond on 2008-05-14
> **tronica said:**
> for anyone who this helps, all i have to do is just put 

Option  "twinview" to in the device section, and all is good.


Cheers worked imedietly for me.  My first day trying ubunto and this is the most usefull post ive seen so far lol:)

---

### Post by FooAtari on 2008-05-29
I'm a bit lost here, wonder if someone can help.

I have two TFT's

One 24" connected to two computers. My Vista box via DVI and Linux via VGA.

I have as second 20" monitor connected to my linux box via DVI.

I wont to clone the desktop to both displays at their native resolutions

1920x1200 and 1680x1050.

At the moment I seem to have each screen running at the correct resolutions.
However it is displaying the desktop as 1920 if that makes sense.  I can only see the top right corner, I would need to scroll around the screen to see the full desktop. Obviously that isn't much use. How do I scale the display to 1680 on the second monitor? Is it even possible?

One of my displays is being detected as a CRT.  Is there anyway to tell which is display is being dected as which device in linux?

Thanks

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Tue Mar  4 20:28:57 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "uk"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       31.5 - 74.5
    VertRefresh     56.0 - 59.88
    Gamma           1
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1280x768@60" 80.1 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
    ModeLine       "1280x720@60" 74.5 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
    ModeLine       "1280x800@60" 83.5 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
    ModeLine       "1440x900@60" 106.5 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
    ModeLine       "1600x1024@60" 136.4 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
    ModeLine       "1680x1050@60" 147.1 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1920x1200@60" 193.2 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
EndSection

Section "Monitor"

 # 
    Identifier     "monitor1"
	Option		"DPMS"
	Horizsync	30-74.55
	Vertrefresh	56-59.88
    Gamma           1
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "UseFBDev" "true"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GT"
EndSection

Section "Device"

 # 
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "nvidia"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT: 1920x1200_59 +0+0, DFP: 1680x1050_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

 # 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
EndSection
```

---

### Post by FooAtari on 2008-05-29
Anyone?

---

### Post by Jovec on 2008-05-29
> **FooAtari said:**
> I wont to clone the desktop to both displays at their native resolutions

1920x1200 and 1680x1050.

At the moment I seem to have each screen running at the correct resolutions.
However it is displaying the desktop as 1920 if that makes sense.  I can only see the top right corner, I would need to scroll around the screen to see the full desktop. Obviously that isn't much use. How do I scale the display to 1680 on the second monitor? Is it even possible?

I am fairly certain it's not possible.  The desktop on the 1680x1050 monitor is being panned.

> 
One of my displays is being detected as a CRT.  Is there anyway to tell which is display is being dected as which device in linux?

Any monitor connected to the VGA port is considered a CRT for the purposes of the Nvidia driver, regardless if the monitor is a TFT.  The nvidia-settings app will identify your monitors.

---

### Post by FooAtari on 2008-05-30
> **Jovec said:**
> I am fairly certain it's not possible.  The desktop on the 1680x1050 monitor is being panned.


That's quite annoying... Would have been really handy to do that.

---

### Post by FooAtari on 2008-05-30
Is there any kind of work around for this, such as a way to create some kind of shortcut to easily change the resolution?

---

### Post by r5gtt2k3 on 2008-05-30
Hi, I'm currently running Twinview, But i hate the way the windows pan out to both screens Here is my config, Could you please shed some light on what I'm doing wrong ? 


```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Tue Mar  4 20:24:34 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier "TwinView Configuration"
	Screen 0 "Default Screen" 0 0
	InputDevice "Configured Mouse"
	InputDevice "Generic Keyboard"
	Option "Xinerama" "Off"
EndSection

Section "Module"
    Load           "dbe"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HSD HC194D"
    HorizSync       31.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option "NoTwinViewXineramaInfo"
EndSection
```

---

### Post by jjbarrows on 2008-06-02
hi,
thanks for the info, i have setup xorg.conf before, but now i wish to use the GUI for two reasons (1-my setup is constantly changing, as i have a laptop and only use two screens when performing, 2-xorg.conf seems to be ignored anyway)

the problem i have is the nvidia GUI application refuses to allow any resolution higher than 640x480 on anything connected to the VGA port (it allows much higher resolution on connections to the s-video port!)

i have this problem on two different systems (the desktop one i have tested with two different nvidia cards, and both desktop and laptop have been tested with a variety of second screens (on the desktop they are recognized fine if they are the only screen connected))

any advice on forcing  the GUI to use higher resolutions?

thanks,
Joseph

---

### Post by besidethewoods on 2008-06-11
nVidia GUI:  First check to see if you already have it.

sudo nvidia-settings

If it doesn't pop up try typing

sudo apt-get install nvidia-settings

and then try the previous command.  This should bring up the GUI and make setting up TwinView a breeze.
Note I'm pretty sure you need to have the Nvidia proprietary driver installed for this to work, but that's pretty easy to do with the new distros.

-Nick

---

### Post by abhiroopb on 2008-06-14
You should be using gksudo nvidia-settings.

---

### Post by dexterslab on 2008-06-17
I tried different guides for almost 3 month. I'm running Ubuntu 8.04 on a Dell Latitude D620 with an NVIDIA card. 

After trying almost everything including editing the xorg.conf file, I finally got it.

Install from synaptic Package Manager
1. nvidia-glx-new
2. nvidia settings

you can also find this from add/remove application.

Then, you can find the NVIDIA X server Settings under System->Administration

And you will be able to manage your screen with a GUI tool.

---

### Post by dexterslab on 2008-06-17
This is what you will get.

[IMG]http://ubuntuforums.org/picture.php?albumid=278&pictureid=875[/IMG]

---

### Post by GOTFrog on 2008-06-18
Hi now that I rebooted  after installing all those i still only have 1 screen and its stuck on 640x480. I cant change anything I dont even have app that fits on the screen completely.  Ive tried renaming my backup xorg.conf and nothing happened. pls help.

Dont know what happened last night nothing worked and this morning everything is great and works like a charme

---

### Post by SyReN on 2008-06-25
my twinview doesnt work as intended, when i plug my tv to the vga port the only available resolutions are 320x240 and 640x480 even though my tv is capable of doing 1280x768.

im using the nvidia gui and 169.xx drivers

this is my xorg.conf:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Tue Mar  4 20:24:34 UTC 2008

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "dk"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: 1280x768 +0+0, DFP: 1280x768 +0+0"
EndSection

```

---

