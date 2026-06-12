---
title: "GUSTY 7.10 ATI Radeon Compiz + ati Dual Monitor + dual-head + big desktop :EASY WAY"
date: 2007-10-26
forum: Multimedia &amp; Video
---

### Post by twizler on 2007-10-26
This is from all over -- i cant take credit for any of it ... ATI  RADEON X600 ATI  RADEON X800 ATI  RADEON X1300 ATI RADEON X1600 ATI RADEON 9000 and OTHER radeons

[COLOR="Red"][SIZE="4"][COLOR="Red"]How to for almost all ATI Radeon cards Gusty 7.1 [/COLOR]: [/SIZE][/COLOR]
[COLOR="Red"][SIZE="4"]Compiz (scroll down for dual-head dual ATI setup / ATI big deskop)[/SIZE][/COLOR]
fresh install of Gutsy 7.10 

> BACK UP YOUR XORG.conf FILE -- NEVER TRY ANY THING unless you have ur orig conf file ... if the *SH$P hits the fan and your config is totall jacked you can always go back.
[COLOR="Red"]sudo cp /etc/X11/xorg.conf   /etc/X11/xorg.cong.BACKUP[/COLOR]

__ HOW do I revert back to my old working  xorg.conf 

COOL un fuk trick of Linux: ( [COLOR="Red"]REMEMBER  ( CRTL + ALT + F7 )  is the display you are in now[/COLOR] you can switch out of a session and back to a terminal login session by pressing ( CRTL + ALT + F4 )  to go back to your display
( CRTL + ALT + F7 ) 
TRY IT OUT --  hit ( CRTL + ALT + F7 ) -- your still here --- now hit ( CRTL + ALT + F4 ) and then again ( CRTL + ALT + F7 ) ..ur back

so if you some how you mess up doing this --- just hit **( CRTL + ALT + F4 )**
Login to the terminal and do a cp from ------ xorg.conf.BACKUP to xorg.conf ___________________________________
sudo apt-get update

   1. Enable fgrlx driver.

      Install linux-restricted-modules and restricted-manager provied in the restricted repositories:
      Code:
 > 
      sudo apt-get update 
      sudo apt-get install linux-restricted-modules-generic restricted-manager
 
     >  Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver".
   2. Install xserver-xgl package
      Code:
 > 
      sudo apt-get install xserver-xgl
 
   3. Install compiz
      Code:
 > 
      sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0
 
   4. Reboot
   5. Log in. 3D effects should be enabled!
   6. Customize Compiz Fusion. > 
      Select System &#8594; Preferences &#8594; Advanced Desktop Effects Settings
      In the new window, General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size. Set it to 4. 
_________________________test out compiz_________
verify you have fglrx  :) it works 
fglrxinfo
_______________[COLOR="Red"]If you have only one monitor  quit while your ahead[/COLOR]____
[SIZE="4"]For those of us with dual  monitors -- dual-head cards -- keep going for some more fun. [/SIZE]
My setup is an ati radeon dual-head x1300 - but  I hv done this on three diff radeon ATI cards now. all being x series 
_I have two 24 inch dell DUAL 24 inch LCD with a dual-head ATI card_____

[COLOR="Red"][SIZE="5"]ATI DUAL MONITOR GUSTY  dual-head ati
 == dual monitor --- dual LCD -- dual Display 2 monitor-- [/SIZE][/COLOR][SIZE="2"]ATI RADEON X600 ATI RADEON X800
 ATI RADEON X1300 ATI RADEON X1600 
ATI RADEON 9000 and OTHER radeons[/SIZE]

1.Run terminal 
  > sudo fglrxinfo 
                ---- spits out something like ----
OpenGL vendor string: ATI Technologies Inc.
Foo FOOO xxxxx 
OpenGL renderer string: Radeon 
This should NOT say mesa-if mesa go back make sure ur using restricted drivers and go over above how to.
 SHOULD BE similar to above: OpenGL vendor string: ATI Technologies Inc.
__________________
2.Run terminal : > 
 aticonfig --query-monitor 
     ____ out put______
Connected monitors: crt1, crt2
  EnableF d monitors: crt1, crt2
******[COLOR="Red"]WARNING IF YOU GET  the infamous __ 
 Connected monitors: noneREAD
  Enabled monitors: none[/COLOR] > 
 in terminal window type :  export DISPLAY=:0 
    [SIZE="3"][COLOR="Blue"] export DISPLAY=:0[/COLOR][/SIZE]
(explanation at [http://www.lunders-and.no/wp/?p=96](http://www.lunders-and.no/wp/?p=96) )
This will export your proper display:
____________
3.In terminal: 
Type again:       aticonfig &#8211;query-monitor
( NUTS of Bolts ATI aticonfig settings  things you will want to know once it works VERY GOOD Read!
[http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941)   
 )
4.In  terminal  > 
sudo aticonfig --initial &#8211;overlay-type=Xv

 sudo aticonfig &#8211;desktop-setup=horizontal
 

 > 
[COLOR="Red"]-----------WARNING-----[/COLOR]this command  will bounce you out of ur desktop so save and bookmark stuff.  
[COLOR="Red"] BEFORE YOU DO THIS ____READ ___ BELOW[/COLOR] 
> 
( CRTL + ALT + BACKSPACE )  
[COLOR="Red"]READ[/COLOR]
You should see one window with a login and another window that is blank not a clone.
once logged into the desktop you should see a clone again--- on both screens. 
You have to enable big desktop 
 > --> system --> preferences--> screen resolutions ---> 
There should be a VERY LARGE display:> mine is 3800 x 1200 
WOW __ IT WORKS :) 
( again If you need other type configurations for your monitor setup-- go to the site below
Some cards may need another step so Look at this site -- if your card still doesn't work. mine have all worked just by following the  steps i provided. 
[http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941) 

This is from all over -- i cant take credit for any of it ... BUT I DID FIND IT ALL and posted it in one place. There are many others that I want to thank that made all this work &#8211; THANK YOU TO THEM ALL 
Here are a few pages -- 

I have compiz on an ati x1300 dual head with dual monitors working with out a hitch --- the compiz rain effect doesnt seem to like the x1300 .... but the rain effect works on my x600 card?? 

credits: 
 [http://www.lunders-and.no/wp/?p=96](http://www.lunders-and.no/wp/?p=96) 
[http://www.phoronix.com/scan.php?page=redblog_entry&item=2550](http://www.phoronix.com/scan.php?page=redblog_entry&item=2550)
[http://ubuntuforums.org/showthread.php?t=301941&page=3](http://ubuntuforums.org/showthread.php?t=301941&page=3)
[http://ubuntuforums.org/showthread.php?t=569654](http://ubuntuforums.org/showthread.php?t=569654)


WORKING xorg.confile > 
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
#Section "InputDevice"
#       Identifier      "Configured Mouse"
#       Driver          "mouse"
#       Option          "CorePointer"
#       Option          "Device"        "/dev/input/mice"
#       Option          "Protocol"      "ImPS/2"
#       Option          "ZAxisMapping"  "4 5"
#       Option          "Emulate3Buttons"       "true"
#EndSection

Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Identifier     "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

###5 button mouse forward / bk in fire fox
Section "InputDevice" 
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "false"
        Option      "ButtonMapping" "1 2 3 6 7 4 5"
EndSection

Section "InputDevice"
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/input/wacom"
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "DELL 2407WFP"
        Option      "DPMS"
EndSection

[COLOR="Red"]Section "Device"
        Identifier  "Generic Video Card"
        Driver      "fglrx"
  Option      "DesktopSetup" "horizontal"     [COLOR="DarkSlateBlue"] 
##THIS IS FOR MY SETUP --- YOU MAY NOT NEED THIS LINE        
Option      "OverlayOnCRTC2" "1"[/COLOR]
        BusID       "PCI:1:0:0"
EndSection[/COLOR]

Section "Screen"
        Identifier "Default Screen"
        Device     "Generic Video Card"
        Monitor    "DELL 2407WFP"
        DefaultDepth     24
        SubSection "Display"
                Modes    "1920x1200" "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection


---

### Post by okst666 on 2007-10-26
useless..does not work at all...
and now I even lost my configuration for single monitor copmiz blabla...

i go back to feisty and bigscreen..that worked perfectly...**** you gutsy

---

### Post by ZenZan on 2007-10-26
Hi

Thanks for the brilliant Tut, 

Worked like a charm, 
had a bit of bother with the "sudo export" command (had to use it because I had no monitors present or enabled according to ati config ) dropped the sudo and it worked.

Thanks once again

Z

---

### Post by IanWatson on 2007-10-26
Yeah, "sudo export" returns an error, but "export" on its own seems to work fine.

Otherwise? Seems to have made things worse. :/ Monitors are still cloned, stuck at 800x600 now.

---

### Post by pinoyskull on 2007-10-27
will this work on my ATI Radeon 9550? with 8.41 driver or should I use 8.42?

---

### Post by Zavior on 2007-10-28
Thanks for the Tutorial. Got compiz working great. I cannot get ATI Big-Desktop to work though. I have tried this tutorial and several others with the lasting result of killing X-windows. Even restoring backed-up xorg.conf files will not help when that happens. I have a Radeon 9800 and any help you might have would be greatly appreciated! I am at my wits end and about install 3 of Gutsy.

---

### Post by leonya on 2007-10-29
I have laptop with ATI X1400 with internal monitor 1400x1050, and external monitor 1920x1200.
I used to have it working in Ubuntu Feisty 7.04 with resolution of 3320x1200 (note 3320 = 1400+1920), without Xgl and Compiz.
Now I have installed Gutsy 7.10, I actually got it to work with Xgl and Compiz - awesome!  
However, the resolution can now only be set to 3840x1200 (3840 = 1920x2).  I can't get it set to 3320, and therefor I am getting about 500 pixels invisible beyond the right border of my monitor.
I cannot figure out how to set it back to 3320.  It used to be an option in Preferences->Screen Resolution, but isn't any more.
Anyone know how I can manually (which files to modify) to set the resolution?

---

### Post by HaMMeReD on 2007-10-29
I can get Compiz running on a single head fine, and get the fglrx drivers installed and running with accel perfectly. As well as a working non-compiz ati big desktop going at 2560x1024, but when I try to start compiz it gives me the following.

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 1002:5b63 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity 

```

From what I understand this guide seems to bypass the 2048 check somehow, if I do that by running compiz with the checks disabled, I get bad screen corrruption on the 2048 horizontal boundary and everything else doesn't seem to look so good either (corruption on moving windows etc)

Is there a way in 7.10 to have 2 seperate xgl/gnome sessions running on each display like was documented in 7.04?.

---

### Post by michael37 on 2007-10-30
Thank you for the post and thank you for the credits. 

There seems to be a lot of interest in the BigDesktop stuff, so I will be forwarding them here :)
Also, I saw you made a post in Tutorials and Tips forum.  Could you please include a link to that post?

Best,
michael37

---

### Post by sperlyjinx on 2007-10-31
Hammered, I have exactly the same issue.  Keep me posted if you find a fix.  Will do the same.

---

### Post by aresazi on 2007-11-01
I followed your steps and it works perfectly for dual monitors on a X300, BUT ONLY THE FIRST TIME.

After a reboot (and subsequent login) I just get dumped at the login screen again.  Disabling XGL (touch ~/.config/xserver-xgl/disable) allows me to login with dual screens, but then Compiz is gone again.

What can I do or where can I find appropriate log files?

---

### Post by saj0916 on 2007-11-01
This is a great tutorial and I appreciate you putting it together, but I'm having a minor problem. I have all of the drivers installed and desktop effects are working but when I get type: > sudo aticonfig --initial –overlay-type=Xv 
I receive this output
> Found fglrx primary device section
Nothing to do, terminating.


I appreciate the help. Thanks.

---

### Post by Light- on 2007-11-01
the command "sudo aticonfig --initial &#8211;overlay-type=Xv" replaces the driver in the device section of xorg.conf with "fglrx". If the driver is already set at "fglrx", it gives the "nothing to do, terminating" message.

---

### Post by saj0916 on 2007-11-02
haha ahh thanks I'm just a newbie

---

### Post by Yv12345vY on 2007-11-02
I'm in the same boat as aresazi.  Just keep getting dumped to the login screen.

---

### Post by Light- on 2007-11-03
happened to me too. then I realised that the resolutions of my monitors exceeded the MAX_TEXTURE_SIZE of my card (2048x2048, and my monitors were 1680x1050 and 1024x768). In this case, you will have to reduce the resolution of your displays until they fit inside the MAX_TEXTURE_SIZE of your video card, or you will not be able to have compiz running

---

### Post by kidguayas on 2007-11-04
I have a All-in-Wonder pro X600 and AMD64 if I run a dual head my compiz doesn't work Do you have any idea why? or what am i"m doing wrong?
Thanks

---

### Post by mk4umha on 2007-11-05
I have a lenovo T60 with the x1300 card and a screen that's 1400x1050. All 3D effects work great, the only problem I have is trying to get the screen to change from 1024x768 to 1400x1050. no matter what I do, I can only change it to 1024x768 or below. 

If I change it to 1400x1050, the desktop resolution is 1400x1050, but my display is still 1024x768. How can i fix this? Here's my xorg.conf, thanks,


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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"Generic Video Card"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1400x1050"
	Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"1400x1050@60"	"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"dbe"
	Load		"v4l"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
Section "device" #   
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Screen	1
EndSection
Section "screen" #   
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #   
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by nadarockyraccoon on 2007-11-07
that would be /etc/x11/xorg.conf
back it up before messing with it

---

### Post by criesca on 2007-11-11
I had the same problem that Light had, and actually had the same solution, I was using 1280x1024+1280x1024 and I could get either compiz on clone OR dualhead, but not both...

Now, I followed what he said, that the max texture size could be top at 2048, and it was, I use now 1024x768+1024x768 and it works wonders.

the only problem I have now is that the gnome bars are displayed across both screens, and when I click maximize it maximizes to both displays :|

I'll see if I can fix that, but thanks a lot for the info Twizler!

---

### Post by jubajuba on 2007-11-28
> **criesca said:**
> I had the same problem that Light had, and actually had the same solution, I was using 1280x1024+1280x1024 and I could get either compiz on clone OR dualhead, but not both...

Now, I followed what he said, that the max texture size could be top at 2048, and it was, I use now 1024x768+1024x768 and it works wonders.

the only problem I have now is that the gnome bars are displayed across both screens, and when I click maximize it maximizes to both displays :|

I'll see if I can fix that, but thanks a lot for the info Twizler!

Has anyone got a fix for this?

---

### Post by jptechnical on 2007-12-14
I just blew hours on this with an x800 card and dual 1280x1024 displays. The only thing I did get working is big desktop, which I hate... who wants every single message popping up in the center of the screen?

Anyway, is this still an issue? Can anyone tell me if you can have dualhead (independent displays and resolutions) without the one big desktop (bars accross both displays... i.e. the power button on the right screen)? I would like to make it work just like my matrox cards used to, I could extend it as another monitor. 

This seemed to work flawlessly with an nvidia card I was playing with in my demo before I tried this on my main machine. But I spent the day trying to get this simple thing working. If I can't get this working flawlessly tomorrow I am going back to XP on my desktop. 

This is making it my 7th failed attempt at moving my desktop to Linux. I have tried each time I reinstall my os for the last 7 years. I run vms and test boxes of every distro that has come out. Ubuntu has really hit the mark for me, before then there was no way I could have done it... anyone remember turbo linux that used to come with Belkin KVMs? At least the days of compiling/configuring cups are gone ;-)

Please help ;-)

---

### Post by gkasinath on 2007-12-31
> **aresazi said:**
> I followed your steps and it works perfectly for dual monitors on a X300, BUT ONLY THE FIRST TIME.

After a reboot (and subsequent login) I just get dumped at the login screen again.  Disabling XGL (touch ~/.config/xserver-xgl/disable) allows me to login with dual screens, but then Compiz is gone again.

What can I do or where can I find appropriate log files?

I have the exact same problem. I am now having to uninstall xserver-xgl and use the mesa drivers to have the dual head working. 
But in this case, I cannot adjust the resolution at all it gives : xserver does not support xrandr extension error. 
/var/log/Xorg.0.log does report that RANDR was enabled and initialized. 

What am I missing? 

Thanks and wish you all a very happy new year.

Cheers
Gautham Kasinath

---

### Post by gkasinath on 2007-12-31
> **jptechnical said:**
> I just blew hours on this with an x800 card and dual 1280x1024 displays. The only thing I did get working is big desktop, which I hate... who wants every single message popping up in the center of the screen?

Anyway, is this still an issue? Can anyone tell me if you can have dualhead (independent displays and resolutions) without the one big desktop (bars accross both displays... i.e. the power button on the right screen)? I would like to make it work just like my matrox cards used to, I could extend it as another monitor. 

This seemed to work flawlessly with an nvidia card I was playing with in my demo before I tried this on my main machine. But I spent the day trying to get this simple thing working. If I can't get this working flawlessly tomorrow I am going back to XP on my desktop. 

This is making it my 7th failed attempt at moving my desktop to Linux. I have tried each time I reinstall my os for the last 7 years. I run vms and test boxes of every distro that has come out. Ubuntu has really hit the mark for me, before then there was no way I could have done it... anyone remember turbo linux that used to come with Belkin KVMs? At least the days of compiling/configuring cups are gone ;-)

Please help ;-)

Hey mate, 
I havent gotten the compiz thingy working, but I do have the dual head working. I removed the xserver-xgl and here is my xorg.conf, if that is of any help to you. 
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
	Option		"XkbModel"	"pc101"
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

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"stylus"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"	"stylus"
#	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"eraser"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"	"eraser"
#	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"cursor"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"	"cursor"
#	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"0 ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	#	Driver		"radeon"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Option		"MergedFB"	"off"
	Screen	0
EndSection

Section "Device"
	Identifier	"1 ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	#	Driver		"radeon"
	#	Option          "VideoOverlay"      "on"
	#	Option          "OpenGLOverlay"     "off"
	Option		"MergedFB"	"off"
	Screen	1
EndSection

Section "Monitor"
	Identifier	"BENQ FP202W"
	Modelname	"BENQ FP202W"
	Option		"DPMS"
	Gamma	1.0
EndSection

Section "Monitor"
	Identifier	"DELL 1907FP"
	Modelname	"DELL 1907FP"
	Option		"DPMS"
	Option		"Enable"	"true"
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Main Screen"
	Device		"0 ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"BENQ FP202W"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Second Screen"
	Device		"1 ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor		"DELL 1907FP"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		#		Virtual 1280 1024
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Option		"Xinerama"	"true"
	Identifier	"Default Layout"
  screen 0 "Main Screen" 0 0
  screen 1 "Second Screen" rightof "Main Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Module"
	Load		"dri"
	Load		"v4l"
	Load		"vbe"
	Load		"i2c"
	Load		"int10"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	#	Load            "type1"
	Load		"GLcore"
EndSection

Section "Extensions"
	Option		"Composite"	"1"
	Option		"Composite"	"0"
EndSection

Section "DRI"
	Mode	0666
EndSection

#Section "device" # 
#	Identifier	"device1"
#	Boardname	"ATI Radeon (fglrx)"
#	Busid		"PCI:1:0:1"
#	Driver		"ati"
#	Screen	0
#	Vendorname	"ATI"
#	Option		"MergedFB"	"off"
#EndSection

#Section "screen" # 
#	Identifier	"screen1"
#	Device		"device1"
#	Defaultdepth	24
#	Monitor		"monitor1"
#EndSection

#Section "monitor" # 
#	Identifier	"monitor1"
#	Gamma	1.0
#EndSection

#Section "ServerFlags"
#EndSection

```

---

### Post by xVariable on 2008-01-02
Yeah, so I'm getting the same thing here: I keep getting booted back to the login screen w/2 Dell LCDs: a 24" and 20" 4:3.  Is this texture limit a function of the amount of video memory (my card is the x850 XT Platinum Edition w/256 MB), or is it a limitation of the driver or the hardware itself?

I even tried booting with 1 of each of the displays connected to bring the overall resolution below the 2048x2048 limit.  If I do an aticonfig --query-monitor it detects that only one display is connected. But if I select the terminal as the session from the login screen, the warning message still appears half off the edge of the display, as if the driver still thinks 2 monitors are connected!  But then, if I bring-up the Catalyst control centre from the terminal, IT only sees 1 display connected. :-?  I've tried doing an aticonfig --initial with one display connected, followed by a reboot, but it doesn't seem to make a difference.  Am I missing something?

Under the above circumstances - with 1 display connected - I no longer get booted back to the login screen.  It just sits there.  I've changed the cursor colour to black in my user account, and the loading of the desktop doesn't even get far enough to apply that custom setting. I have to do a sudo reboot.  I should point-out that I *did* install the latest driver version from ATI/AMD's site, so maybe there's some sort of compatibility issue?

If I want to test for a version incompatibility, would I be able to get rid of the driver I downloaded from ATI/AMD's site by first disabling the restricted driver, then uninstalling it using Synaptic, and then reinstalling with Synaptic?  I guess I'll give that a try and then start the process over again and see what happens?...

---

### Post by xVariable on 2008-01-02
Joy.  I removed the binary driver and rebooted, only to be told that my conf file was corrupted, and couldn't be fixed because get-edid wasn't installed. Unfortunately I couldn't reinstall it because my only network connection is wireless and I couldn't enable it from the command prompt.

So, I'm reinstalling now. It's faster than trying to recover anyway. The first thing I'll do at boot-up is to try following the instructions at the top if this thread and see if they work...

---

### Post by xVariable on 2008-01-03
Yay! It works! ACtually I've been drooling for a while here as I've played with it for an hour or so. I'm gonna give the dual display portion of the tut' a go tomorrow and will post back here with results.

I've also discovered a major bug but am too tired to post the details now. Tomorrow.

---

### Post by tgecho on 2008-01-03
This *almost* worked perfectly. I have a big desktop, I have compiz running.... everything works great. Except maximizing fills both screens. Since they're different resolutions, this is especially annoying.

This thread seemed to have an answer, but I couldn't get it to work:
[http://forum.compiz-fusion.org/showthread.php?t=4500](http://forum.compiz-fusion.org/showthread.php?t=4500)

I've tried turning off the effects while messing with things, but it doesn't seem to help.

---

### Post by xVariable on 2008-01-05
No I can't get both displays running with compiz. :( I can run either display w/compiz but not both w/compiz.  My setup is an ATI x850 XT Platinum Edition w/256 MB RAM, and a Dell  monitors: 24" @ 1920x1200, and a Dell 20" 4:3 @ 1600x1200.

Is this 2048x2048 limitation a question of the binary driver, the amount of video memory, or ATI's cards?

I thought about setting the total desktop size to 2880x1200 and *then* enabling the XGL server, but that res is not an option in the Screen Resolutions capplet, and I can't figure-out by looking at my xorg.conf file where to add a line for that res:

```
Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "DELL 2407WFP"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)]"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "TexturedVideoSync" "off"
	Option	    "Capabilities" "0x00000800"
	Option	    "FSAAEnable" "on"
	Option	    "FSAAScale" "6"
	Option	    "FSAADisableGamma" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc R480 [Radeon X850XT Platinum (PCIE)]"
	Monitor    "DELL 2407WFP"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1920x1200" "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection
```

BTW: the card's fan is running at full speed constantly and it's SOOO LOUD!  Is there any way to turn that off?  It's only supposed to run when heavily using the card. i.e.: when playing a game or something.  Under normal use in Windows it was never this loud...

---

### Post by gkasinath on 2008-01-07
uumm no joy yet with x300 Rv370.. :( Any help would be greatly appreciated. 

I am actually at my wits end on this now. Have tried almost everything I could read about the configuration. 

:( 

Gautham Kasinath

---

### Post by tbalzotti on 2008-02-06
Thank you! This made my dual ATI1300 on 2x1600x1200 Dell Monitors Dell Optiplex 745 work beautiful!

---

### Post by xr1c3x on 2008-04-09
hi i followed everything and i seem to get everything down to the point where i change the screen resolution but there isn't a big screen resolution. i have a samsung syncmaster 173s and im on a dell e1705 with an ati x1400 gfxcard
thanks for the help! great tutorial btw

---

### Post by robaldred on 2008-07-13
No compiz for me as my card x800pro only supports max 3d texture size of 2048 with dual head my desktop with is: 2560, but who cares using metacity, with the layout just as I want it :)

your a legend thanks!
Rob

---

