---
title: "Can't get dual screen with ATI 7000 &amp; 9200SE. What am i doing wrong?!"
date: 2005-12-22
forum: Multimedia &amp; Video
---

### Post by djgenesis on 2005-12-22
This is getting me so frustrated....... I am going through hell with this.... 
So here goes... I am running Ubuntu hoary hedgehog and i have two graphics cards on my box.
ATI Radeon 9200SE and
ATI Radeon  7000

I read a million howto's but i still can't get it right. 
I list my pci devices by lspci and i get:
```

0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)
0000:02:09.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] 
```

So i edited my xorg config as this:
```

Section "Monitor"
	Identifier	"Monitor 0"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Monitor"
	Identifier	"Monitor 1"
	HorizSync	30-70
	VertRefresh	50-160
EndSection






# **********************************************************************
# Graphics device section
# **********************************************************************



Section "Device"
    Identifier  "ATI 7000"
    VendorName  "ATI"
    BoardName   "Unknown"
    Driver      "vga"
    BusID       "PCI:2:9:0"
EndSection


Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
    Option "DesktopSetup"               "Single"
    Option "ScreenOverlap"              "0" 
    Option "GammaCorrectionI"           "0x06419064"
    Option "GammaCorrectionII"          "0x06419064"
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
    Option "VideoOverlay"               "on"
    Option "OpenGLOverlay"              "off"
    Option "CenterMode"                 "off"
    Option "PseudoColorVisuals"         "off"
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

Section "Screen"
    Identifier  "Screen 0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor 0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
    EndSubsection

EndSection

Section "Screen"
    Identifier  "Screen 1"
    Device      "ATI 7000"
    Monitor     "Monitor 1"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
    EndSubsection

EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************
Section "ServerLayout"
	Identifier     "Dual Screen"
        option 	        "Xinerama" "on"
  	Screen      0  "Screen 0" 0 0
  	Screen      1  "Screen 1" RightOf "Screen 0"
	InputDevice "Mouse1" "CorePointer"
	InputDevice "Keyboard1" "CoreKeyboard"
EndSection

```

The second monitor turns on but instead of displaying the extended desktop it is black and displays 
"RADEON 7000 32MB ELIXIR DDR BIOS B8480.D3110A.002"

I am pretty sure my xorg is correct but what seems to trouble me is that the Radeon 7000 has two heads (VGA,DVI) and on the list of the PCI devices I can't see the "secondary".

Have i configured anything wrong? Do i need any other drivers? I am waiting for the dual display to migrate from Windows to Ubuntu once and for all, but this is doing my head!! 

Please.. PLEASE PLEASE! any suggestions would do.

---

### Post by varunus on 2005-12-23
I can see the issue, I think.

You have the driver set to "vga" for your radeon 7000 in your xorg.conf.

Reading from the vga man page:
       vga  is  an Xorg driver for generic VGA video cards.  It can drive most
       VGA-compatible video cards, but only makes use of  the  basic  standard
       VGA  core that is common to these cards.  The driver supports depths 1,
       4 and 8.  

Instead, you want to use the radeon driver:
       radeon  is a Xorg driver for ATI RADEON based video cards.  It contains
       full support for 8, 15, 16 and 24 bit pixel  depths,  dual-head  setup,
       flat  panel, hardware 2D acceleration, hardware 3D acceleration (except
       R300 and IGP series cards), hardware  cursor,  XV  extension,  Xinerama
       extension.

Also, the fglrx driver does not support Xinerama, it instead has its own strange Xinerama clone.

Since you have a 9200SE and a 7000, both cards are fully supported (with 3d acceleration, even!) by the open source radeon driver.  I recommend you scrap the often buggy fglrx driver and go with the open source one.  Also, because your cards are both 9250 or below, you can use poofyhairguy's composite manager howto to get vista-like effects with little performance hit!

Therefore, I recommend you backup your current xorg.conf, and change your xorg.conf to:
```
Section "Monitor"
	Identifier	"Monitor 0"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Monitor"
	Identifier	"Monitor 1"
	HorizSync	30-70
	VertRefresh	50-160
EndSection






# **********************************************************************
# Graphics device section
# **********************************************************************



Section "Device"
    Identifier  "ATI 7000"
    VendorName  "ATI"
    BoardName   "Unknown"
    Driver      "radeon"
    BusID       "PCI:2:9:0"
    Option "RenderAccel" "true"
EndSection


Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "radeon"
    BusID "PCI:1:0:0"    
    Option "RenderAccel" "true"
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

Section "Screen"
    Identifier  "Screen 0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor 0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
    EndSubsection

EndSection

Section "Screen"
    Identifier  "Screen 1"
    Device      "ATI 7000"
    Monitor     "Monitor 1"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
    EndSubsection

EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************
Section "ServerLayout"
	Identifier     "Dual Screen"
        option 	        "Xinerama" "on"
  	Screen      0  "Screen 0" 0 0
  	Screen      1  "Screen 1" RightOf "Screen 0"
	InputDevice "Mouse1" "CorePointer"
	InputDevice "Keyboard1" "CoreKeyboard"
EndSection
```

This should get you dual head; if it does not, post back here.  There have been some issues with using DRI and Xinerama, but I think because you have two video cards, you'll be ok.

A quick question though; why can't you just connect both monitors to the 9200SE?  Does it not have two heads?  If you do this, you can use the MergedFB option, which is very nice compared to Xinerama...
If you're just trying to take some of the load off of the card, that makes sense.

Good luck, and post back here with issues/questions.

---

### Post by djgenesis on 2005-12-23
> 
A quick question though; why can't you just connect both monitors to the 9200SE? Does it not have two heads? 
The card has only a TVout, thats why i connected the second one. 

After applying the changes to xorg.conf, the first monitor has switched on OK, but the other one is off. It does not even display the Model number on the monitor. 

Might it be that i am still using fglrx?

Thanks for the reply , really appreciated.

---

### Post by djgenesis on 2005-12-23
Oooooh... and by the way is the radeon HowTo on [this ]("http://www.rage3d.com/content/articles/atilinuxhowto/Linux_ATI.html#SECTION000121000000000000000") page?

---

### Post by varunus on 2005-12-23
Only one monitor switches on?  Can you post the file /var/log/Xorg.0.log here please?  Then we can see what's going on..

---

### Post by djgenesis on 2005-12-24
This is the Xorg.1.log file:
```

X Window System Version 6.8.2 (Ubuntu 6.8.2-10.1 20050831033957 root@)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntuj 2.6.10-5-386 #1 Mon Oct 10 11:15:41 UTC 2005 i686
Build Date: 31 August 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Mon Oct 10 11:15:41 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sat Dec 24 21:13:44 2005
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 338 of section Monitor in file /etc/X11/xorg.conf
	"ection" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.


```


And this is the Xorg.0.log file is attached:

---

### Post by varunus on 2005-12-28
From the log you posted, it looks like you're using the fglrx driver still...Did you try what I told you with the radeon driver?  Or did something go wrong with changing xorg.conf?

---

### Post by djgenesis on 2005-12-29
[QUOTE=djgenesis]Oooooh... and by the way is the radeon HowTo on [this ]("http://www.rage3d.com/content/articles/atilinuxhowto/Linux_ATI.html#SECTION000121000000000000000") page?[/QUOTE]

Is this the Howto for the free ati drivers?

---

### Post by varunus on 2005-12-29
No, that's for the ATI official drivers.  Try what I said with the "radeon" driver; that's the open source driver.

---

### Post by djgenesis on 2005-12-29
Is this what we are talking about?

[quote]
Knowledge Base  	
ATI Customer Care > Drivers and Software > Linux > Linux x86 > RADEON >
ATI Proprietary Linux x86 Display Drivers for XFREE86 / X. Org Version 8.20.8
[quote]

I also saw this website
 [http://nurkka.org/linux_on_travelmate_3210/](http://nurkka.org/linux_on_travelmate_3210/)
but there's no link to the "Radeon" driver ....

And i ask you ..... am i stupid or is it just me ?!?!?

---

### Post by varunus on 2005-12-31
Those drivers you're referring to are the official ATI drivers.  These are called the fglrx drivers.

The "radeon" driver is the open source driver that can be used with ATI cards below a 9600 with no penalties.

Information about the open source radeon driver can be found if you open a terminal, and type "man radeon".

I think I described how to get Xinerama with your two cards above...do you have a log file for that, to see if the driver rejects one of your cards?

---

### Post by djgenesis on 2006-01-02
Yeeeees!!!!! It's working !!!


I have dual screen extended desktop showing on both of my displays although i have an error coming up showing three times when i log on:
```

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of <b>xprop -root | grep XKB</b>
- The result of <b>gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd</b>

```


Does that have to do anything with my Xorg.conf? 

Also, my wallpaper has split into two onto both screens. Is this normal?

And finally both of the displays are flickering. Will i have to change the refresh rate from xorg.conf?

Thank you EVER so much !!!! :D :D :D

---

### Post by varunus on 2006-01-03
Awesome!  Glad to hear its working.

The wallpaper being split is normal; you have to get a large wallpaper (or just fuse two in the GIMP) to make a two-screen wallpaper.  [www.studiotwentyeight.com](www.studiotwentyeight.com) has some nice wallpapers that work on dual monitors.

For screen flickering, I'm pretty sure that you're right; there's a howto in the Tips and Tricks section on how to change your refresh rate.

I'm not sure why the XKB error is coming up, can you post your new xorg.conf file maybe?

---

### Post by djsroknrol on 2006-04-04
> S Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Mon Oct 10 11:15:41 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sat Dec 24 21:13:44 2005
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 338 of section Monitor in file /etc/X11/xorg.conf
	"ection" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Did you guys see the missing "S" ???? you guys had him chasing for drivers he didn't really need to get the job done...although, I must agree that the "Radeon" driver is best all around...

---

### Post by djgenesis on 2006-04-05
Well even if they didn't.... i should have noticed it before posting but i saw it only after playing around with it ](*,) 


Have you seen that keyboard error above anywhere else?

---

### Post by adambot on 2006-04-05
Greetings,

I have followed the directions exactly as you have posted (with the necessary changes, but with radeon drivers and everything else) however, when i try to start gdm (or X) my second screen is a corrupt image and then the system completely freezes.

below is the pertinant parts of my xorg.config:

```
Section "Device"
	Identifier "7500"
	VendorName "ATI"
	Driver "radeon"
	BusID "PCI:1:0:0"
	Option "RenderAccel" "true"
EndSection

Section "Device"
	Identifier "7000"
	Driver "radeon"
	BusID "PCI:5:9:0"
	Option "RenderAccel" "true"
EndSection

Section "Monitor"
	Identifier	"CML170SX Plu"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen 0"
	Device		"7000"
	Monitor		"CML170SX Plu"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen 1"
        Device          "7500"
        Monitor         "CML170SX Plu"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Option		"Xinerama" "on"
	Screen 0	"Screen 0" 0 0
	Screen 1	"Screen 1" RightOf "Screen 0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

the only BIG difference i can think of is that i am using dapper flight-6 which has the modular xorg7, but i did a default install, so everything should be there.

---

### Post by djgenesis on 2006-04-05
Uuuuum... you are using what?!?!  :-D  
Its all greek to me hehe.
I can't help you so lets hope that someone will read the thread and give you a hand ;)

---

### Post by adambot on 2006-04-06
[QUOTE=djgenesis]Uuuuum... you are using what?!?!  :-D  
Its all greek to me hehe.
I can't help you so lets hope that someone will read the thread and give you a hand ;)[/QUOTE]

i hope they do too since this is painful -- as a recent convert from gentoo, this is not promising (since i had a triple screen setup working there)

---

### Post by djsroknrol on 2006-04-06
Hey adambot...It looks like you're missing an identifier for the second monitor...correct me if I'm wrong...but, I don't see it..I see the profile for it, but not the identifier...anyone?....

---

### Post by adambot on 2006-04-06
both of the screens are the same...  I did have a second one in there for awhile, however it didn't seem to make much of a difference...   however i was probably testing other things at the time, so i will try again and let you know what happens...  Also --- it does look like it is some kind of weird driver issue, but that is just my $.02

---

