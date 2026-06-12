---
title: "default driver for NVidia and xorg"
date: 2010-05-08
forum: Multimedia Software
---

### Post by oldsoundguy on 2010-05-08
Since, it appears, it is going to be a while until NVidia does something about their restricted driver problem in 10.04,  need to know how to get the line: Option  'RandRRotation" "true"  .. to work in the device section of xorg.conf so that the "display" option no longer has the rotation button disabled.
There was a time (previous versions of Ubuntu) when all that was required was to enter that line of code and I could rotate the monitor display.

Do I have to enter that line elsewhere?

---

### Post by oldsoundguy on 2010-05-09
What happened to all the "helpers" that are always telling you to "open terminal and put this in"?

I KNOW that is what has to be done .. but what is the "this" that I have to enter?

---

### Post by WinterRain on 2010-05-09
> **oldsoundguy said:**
> it is going to be a while until NVidia does something about their restricted driver problem in 10.04

What problem is that, and what model is your video card?

---

### Post by oldsoundguy on 2010-05-09
> **WinterRain said:**
> What problem is that, and what model is your video card?

The "problem" is that I want to be able to rotate my monitor to the portrait orientation.  

Initially, upon upgrading from 8.04 to 10.04, there was the option to do so in the NVida restricted driver. (not the generic).  For some reason that option just disappeared, along with the resolution settings required for my particular monitor!

So, I removed the restricted driver and went with the generic. (at least it has the resolution settings.) 
In the past, I could go into xorg.conf and enter the line:
Option "RandRRotation" "true"
in the device section, and the  rotate button on the generic "display"(now .. used to be "resolution") would be operable.  
NOT SO NOW

(card is NVidia FX 5500 .. system is home built with MSI board running Intel hyper 3.06 with 2 gb ram and a pair of nice large hard drives.)
Driving an HP LP2465 display.

This display problem and the fact that Skype no longer works, are the only two issues I have with 10.04.  Everything else .. including the BIG improvement in audio management, has me with a really big grin of satisfaction!

Would also point out, the upgrade on two other computers that use a STANDARD RATIO LCD, have NOT crashed the display (using the restricted driver).. they both rotate, and they both have the proper resolution for the attached NEC screens.

---

### Post by WinterRain on 2010-05-09
As you may know, upgrading can be hit or miss. I would try a clean install of lucid on that machine with the 173 nvidia drivers. Also, are you using nvidia-settings as superuser to try and make changes?

---

### Post by oldsoundguy on 2010-05-09
> **WinterRain said:**
> As you may know, upgrading can be hit or miss. I would try a clean install of lucid on that machine with the 173 nvidia drivers. Also, are you using nvidia-settings as superuser to try and make changes?

A clean install is totally out of the question.  This is the main machine and has been in operation for over 4 years and JUST UPGRADED.  Way too much in the way of tweaks and programs to wipe and start at point A.

The issue is .. the thing WORKED with the driver installed from the hardware drivers option.  But, had to re-boot for something else, and the monitor controls went south.
UNINSTALLED the restricted drivers and let it revert to the default drivers.
I am not into eye candy and games, so 3D is not needed .. but I DO need that rotation feature.  So, since the default drivers have better resolution, just modifying the xorg.conf file SHOULD solve the problem .. the issue is that entering the code and saving does NOTHING.  
Need to figure out why doing a standard sudo nano modification of xorg does NOT do anything!

---

### Post by oldsoundguy on 2010-05-10
same chorus, different day.

---

### Post by onecallednick on 2010-05-10
Woa, dude.  We aren't paid tech support.  We're linux users who like to help other linux users.  No one owes you a quick and helpful response.  If you don't like the answers you're getting here, you can pony up for Canonical tech support.  No need to get pissy, WinterRain was trying to do you a favor.

---

### Post by oldsoundguy on 2010-05-10
> **onecallednick said:**
> Woa, dude.  We aren't paid tech support.  We're linux users who like to help other linux users.  No one owes you a quick and helpful response.  If you don't like the answers you're getting here, you can pony up for Canonical tech support.  No need to get pissy, WinterRain was trying to do you a favor.


That is why I wait 24 hours to bump.

The problem seems to be more than ME as now there are more topics appearing on Google concerning the latest packages from NVidia and it's relationship with 10.04.
And the latest updates from the repositories were not the answer, either.

NONE of the purported fixes work thus far .. and the posters of them do not seem to have the answer to issues that come up mid fix as they do not respond to posts back.  Understandable, as they are just offering a fix that worked for them .. time for NVidia to do something.

I have two machines where this has not become a problem .. OLD machines with older hardware .. so can NOT figure this out.  

I am NOT a newbie to Linux (started with Mandrake 4) and have no fear of using terminal as I use it a lot.  But I am NOT a programmer/code writer .. I am a user.

The alternate fix (other than relying on NVidia) is to modify the xorg.conf file .. but the modifications that worked in previous builds do NOT work with Lucid .. so that is another issue.

---

### Post by oldsoundguy on 2010-05-13
Thought I would wait a couple of days to bump this so there is nobody to accuse me of being impatient.

So bumping.

---

### Post by Dilutu on 2010-05-14
Just out of curiosity, did you try the older "nv" driver? Its the only one  working decently with my geforce4 mx4000......

---

### Post by realzippy on 2010-05-14
*....the thing WORKED with the driver installed from the hardware drivers option*

...means you set up your portrait with *nvidia-settings* tool and settings have been gone after restart?

---

### Post by oldsoundguy on 2010-05-14
Answer to question about drivers used:
I have used every one in synaptic with the same results ..
So I use the default driver and it works BETTER (better resolution) but I still can NOT modify the xorg.conf file to allow screen rotation.  The code writes to the file and displays as there when re-checked, but the rotation button is not activated in the "monitors" screen.

Second question about procedure:
Yes, initially the restricted driver had the ability to set to portrait.  Upon rebooting (at that time), that option disappeared from the NVidia.Xconfig screen. Have NEVER been able to restore the option .. PLUS the restricted driver was just that .. restricted in resolution .. and would not give me the resolution I need for this cinema dispay.

---

### Post by realzippy on 2010-05-14
[I]that option disappeared from the NVidia.Xconfig screen
[/I]


..tested on my machine:

in nvidia-settings the "rotate" option only appears after editing xorg.conf..(and a X restart).Knowing you edited yours,but please post your current /etc/X11/xorg.conf (whole file)

---

### Post by oldsoundguy on 2010-05-14
> **realzippy said:**
> [I]that option disappeared from the NVidia.Xconfig screen
[/I]


..tested on my machine:

in nvidia-settings the "rotate" option only appears after editing xorg.conf..(and a X restart).Knowing you edited yours,but please post your current /etc/X11/xorg.conf (whole file)

Can't get the damn thing to copy and it is HUGE! I can get the first page to copy, but not the whole file! (must be a different trick to copy the whole file from terminal.)

---

### Post by realzippy on 2010-05-14
ehm,not talking about nvidia bugreport file; xorg.conf should not be more than 1 page...!?

with

```
gedit /etc/X11/xorg.conf
```

you should be able to open it and copy/paste the content here...

---

### Post by doughoist on 2010-05-14
Why does NVIDIA need to step up? The driver worked before, now in Lucid it doesn't. Sounds like Canonical needs to step up and fix their faulty implementation. Canonical is the one that changed things, the driver is still the same. Canonical broke its implementation of the driver and for no aparent reason other than to change from a working implementation to a faulty one.

---

### Post by realzippy on 2010-05-14
Nah,nvidia driver works fine (195.xx) with lucid.

---

### Post by oldsoundguy on 2010-05-14
DUUUHHHH!!  Was trying to copy from another editor!  Got it but it IS huge.

To answer:
Once again!
I have tried ALL of the NVida drivers in synaptic.
NONE of them has the rotate option line NVid xconfig screen ..... PLUS not of them has sufficient resolutions for my set up .. need 1920 x 1200 with 16x10 ratio for my cinema display. 
So I have the GENERIC CANONCAL written driver in use. It DOES have the resolution I need .. but it too, does NOT allow rotation (even after editing)

so here is the edit .. and sorry this will take up most of the page!

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Thu Jul 17 18:39:19 PDT 2008
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
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#    Identifier     "Generic Keyboard"
#    Driver         "kbd"
#    Option         "XkbRules" "xorg"
#    Option         "XkbModel" "pc105"
#    Option         "XkbLayout" "us"
#EndSection
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#    Identifier     "Configured Mouse"
#    Driver         "mouse"
#    Option         "CorePointer"
#EndSection

Section "Monitor"
	Identifier     "Configured Monitor"
	VendorName     "Hewlett-Packard"
	ModelName      "HP LP2065 Flat Panel Monitor"
	HorizSync       30.0 - 92.0
	VertRefresh     48.0 - 85.0
	Gamma           1
	ModeLine       "640x400@85" 31.5 640 672 736 832 400 401 404 445 -hsync +vsync
	ModeLine       "640x350@85" 31.5 640 672 736 832 350 382 385 445 +hsync -vsync
	ModeLine       "720x400@85" 35.5 720 756 828 936 400 401 404 446 -hsync +vsync
	ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
	ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
	ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
	ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine       "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
	ModeLine       "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
	ModeLine       "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
	ModeLine       "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	ModeLine       "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
	ModeLine       "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
	ModeLine       "1280x720@50" 60.47 1280 1328 1456 1632 720 721 724 741 -hsync +vsync
	ModeLine       "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	ModeLine       "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
	ModeLine       "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
	ModeLine       "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
	ModeLine       "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
	ModeLine       "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
	ModeLine       "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
EndSection

Section "Monitor"
	Identifier     "monitor1"
	Gamma           1
	#
EndSection

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "HP LP2465"
	HorizSync       30.0 - 94.0
	VertRefresh     48.0 - 85.0
EndSection

Section "Screen"
	Identifier     "Default Screen"
	Device         "Configured Video Device"
	Monitor        "Configured Monitor"
 	DefaultDepth    24
	Option         "RandRRotation" "true"
	SubSection "Display"
		Virtual     1920 1200
		Depth       24
		Modes      "1920x1200@60" "1680x1050@75" "1680x1050@60" "1600x1024@60" "1440x900@60" "1440x900@75" "1280x800@60" "1280x720@50" "1280x768@75" "1280x800@75" "1280x720@60" "1280x768@60" "1280x854" "1152x768@54" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "720x400@85" "640x350@85" "640x400@85"
	EndSubSection
EndSection

Section "Screen"
	Identifier     "screen1"
	Device         "device1"
	Monitor        "monitor1"
	DefaultDepth    24
EndSection
    
Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	DefaultDepth    24
	Option         "TwinView" "0"
	Option         "metamodes" "1600x1024_60 +0+0"
	# Removed Option "metamodes" "1440x900@60 +0+0; 1280x800@60 +0+0; 1280x720@60 +0+0; 1280x768@60 +0+0; 800x600@60 +0+0; 1600x1024 +0+0"
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Module"
	Load           "v4l"
	Load	"dri"
	Load	"GLcore"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "kbd"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
	# generated from default
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
	Option         "Xinerama" "0"
	# Keyboard settings are now read from /etc/default/console-setup
	#    InputDevice    "Generic Keyboard" "CoreKeyboard"
	# commented out by update-manager, HAL is now used and auto-detects devices
	# Keyboard settings are now read from /etc/default/console-setup
	#    InputDevice    "Configured Mouse"
	# commented out by update-manager, HAL is now used and auto-detects devices
EndSection

Section "Device"
	Identifier     "Configured Video Device"
	Driver         "nvidia"
        VendorName     "NVIDIA"
	BoardName      "NVIDIA GeForce4 (generic)"
	BusID          "PCI:1:0:0"
	Screen          0
EndSection

Section "Device"
	Identifier     "device1"
	Driver         "nv"
	VendorName     "NVIDIA"
	BoardName      "NVIDIA GeForce4 (generic)"
	BusID          "PCI:1:0:0"
	Screen          1
	#
EndSection

Section "Device"
	Identifier     "Device0"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce FX 5500"
        Option         "RandRRotation"  "true"
	Driver	"nv"
EndSection

NOTE .. the card in use is the 5500 .. and it worked just fine in 8.10 using EITHER driver.

---

### Post by realzippy on 2010-05-14
this file is completely....messed up.Or are you running more than 1 graphiccard?

---

### Post by oldsoundguy on 2010-05-14
Only one .. but there is an on board on the MB .. and I would SWEAR I went into bios a LONG time ago and disabled .. if your observation is correct .. may have to RE-DISABLE. (then comment out?)

---

### Post by modorf on 2010-05-14
hey,

can you provide the info about your video card.
which version of nvidia drivers are you trying to use?


depending on your graphics card, try installing the packages : nvidia-current, nvidia-settings, nvidia-common   and  run nvidia-xconfig to configure xorg.conf with nvidia driver.

```

sudo aptitude install nvidia-current nvidia-settings nvidia-common
sudo nvidia-xconfig

```

---

### Post by realzippy on 2010-05-14
> **oldsoundguy said:**
> Only one .. but there is an on board on the MB .. and I would SWEAR I went into bios a LONG time ago and disabled .. if your observation is correct .. may have to RE-DISABLE. (then comment out?)



No.Which driver are offered in restricted drivers?
173? current?

---

### Post by oldsoundguy on 2010-05-14
> **modorf said:**
> hey,

can you provide the info about your video card.
which version of nvidia drivers are you trying to use?


depending on your graphics card, try installing: nvidia-current, nvidia-settings, nvidia-common

```
sudo aptitude install nvidia-current nvidia-settings nvidia-common
```

Been there, done that .. more than once.
As the xorg shows TWO cards .. I am using the FX 5500 and have been on this box for a long time.

EMPHASIZING AGAIN .. I do NOT need the restricted driver(s) so that I can install a boatload of .. what is to me .. useless desktop manipulators.  I never see my desktop except when I download something or bring something in from another computer on my net. (and the current crop does not seem to have my monitor set up)

I DO, however, need the rotation option to work for it is a lot easier on some of my programs to use it in portrait orientation vs landscape .. a lot less scrolling.

---

### Post by oldsoundguy on 2010-05-14
Synaptic offers 96, 173, 180, 185 and CURRENT
The hardware drivers shows CURRENT is the package. It also says "activated but not currently in use"

I also got this thing in the works (I am Dave)
[http://www.sucka.net/2010/04/how-to-install-nvidia-video-driver-in-10-04-lucid-lynx/#comment-1809](http://www.sucka.net/2010/04/how-to-install-nvidia-video-driver-in-10-04-lucid-lynx/#comment-1809)

---

### Post by realzippy on 2010-05-14
> **oldsoundguy said:**
> Been there, done that .. more than once.
As the xorg shows TWO cards .. I am using the FX 5500 and have been on this box for a long time.

EMPHASIZING AGAIN .. I do NOT need the restricted driver(s) so that I can install a boatload of .. what is to me .. useless desktop manipulators.  I never see my desktop except when I download something or bring something in from another computer on my net. (and the current crop does not seem to have my monitor set up)

I DO, however, need the rotation option to work for it is a lot easier on some of my programs to use it in portrait orientation vs landscape .. a lot less scrolling.

Yes.But it is a difference to set up the "portrait" mode with the *restricted driver* the *nv* driver or the *nouveau* driver.
If we do not know which driver,we cannot help....

---

### Post by bywhatnow on 2010-05-14
Don't have a reply, but do have a question. I downloaded and burned the 10.4 release, put it on my machine and the second time I booted up ....no go..the lights on my keyboard just flashed and it was locked in some kind of loop. I tried to reinstall but for whatever reason it can not repair an installation,and could only do another install. I tried to do a low level format on the hard drive (using troubleshooter) and was unable to do so. I assumed I had a bad hard drive. I reinstalled (dual boot with my Windows XP) and all seemed to be well until it told me I needed to update my Nvidia video driver. I told it to do it, it did told me to restart the machine, and here I am at that same will not boot to the desktop, keyboard lights flashing and the machine locked again.....is there a way to get this to work or have I just lost another hard drive??

---

### Post by realzippy on 2010-05-14
> **oldsoundguy said:**
> Synaptic offers 96, 173, 180, 185 and CURRENT
The hardware drivers shows CURRENT is the package. It also says "activated but not currently in use"

I also got this thing in the works (I am Dave)
[http://www.sucka.net/2010/04/how-to-install-nvidia-video-driver-in-10-04-lucid-lynx/#comment-1809](http://www.sucka.net/2010/04/how-to-install-nvidia-video-driver-in-10-04-lucid-lynx/#comment-1809)

So do this;

```
sudo rm /etc/X11/xorg.conf
```

that kills your messed up old xorg.conf,no need to backup.Then restart
and check hardware drivers if "current" is in use.

---

### Post by oldsoundguy on 2010-05-14
lshw shows the card as unclaimed but the monitor is plugged INTO the card and it is working.

---

### Post by oldsoundguy on 2010-05-14
> **realzippy said:**
> So do this;

```
sudo rm /etc/X11/xorg.conf
```

that kills your messed up old xorg.conf,no need to backup.Then restart
and check if "current" is in use.

Will give it a shot.  Hope it does not crash this thing as it is my MAIN computer in the place and 98% of what I do goes through it!

---

### Post by Fenris_rising on 2010-05-14
> **oldsoundguy said:**
> Will give it a shot.  Hope it does not crash this thing as it is my MAIN computer in the place and 98% of what I do goes through it!

Back up your data at least if you haven't already.

---

### Post by bywhatnow on 2010-05-14
Only one graphic card a Gforce6800GT 256MB AGP card. The default drive worked,but when I tried to change my video resolution I was told ,by the OS that I needed to upgrade/update my video driver. I said yes(I'm completely stupid when it comes to Linux,but I'm trying) this is twice this has happened, the first time it cost me a 120 GB Hard drive that I can no longer format...Now if I could get this thing to boot to the desktop I may be able to fix some of it....BUT, the machine locks up and the lights on my keyboard flash and the boot sound is like a broken record......please,anyone, please help

---

### Post by realzippy on 2010-05-14
That file is junk.Karmic/lucid runs without xorg.conf....

---

### Post by realzippy on 2010-05-14
> **bywhatnow said:**
> Only one graphic card a Gforce6800GT 256MB AGP card. The default drive worked,but when I tried to change my video resolution I was told ,by the OS that I needed to upgrade/update my video driver. I said yes(I'm completely stupid when it comes to Linux,but I'm trying) this is twice this has happened, the first time it cost me a 120 GB Hard drive that I can no longer format...Now if I could get this thing to boot to the desktop I may be able to fix some of it....BUT, the machine locks up and the lights on my keyboard flash and the boot sound is like a broken record......please,anyone, please help

Welcome!!
But...please do not jump in threads with your problem.It is called....
Please open a new thread!

---

### Post by oldsoundguy on 2010-05-14
REALZIPPY .. THANKS .. that got the thing fixed and using the generic Ubuntu NVida driver!!

MUCHLY APPRECIATED as I have been fighting this thing since I upgraded!


(now if only I can get Skype to work .... hmmmmm ... later for that one!)

---

### Post by bywhatnow on 2010-05-14
Please forgive me......I'm tooo stupid to open a new thread....looked for over 30 min to post a question. guess I'm just not geek enough to leave Windows.....sorry I bothered you

---

### Post by oldsoundguy on 2010-05-14
> **Fenris_rising said:**
> Back up your data at least if you haven't already.


ALWAYS have the thumb drive already loaded before I do any serious tweaking!!  Been doing this too long to make that dumb move!! LOL

---

### Post by realzippy on 2010-05-14
> **bywhatnow said:**
> Please forgive me......I'm tooo stupid to open a new thread....looked for over 30 min to post a question. guess I'm just not geek enough to leave Windows.....sorry I bothered you

Yes,the button "new thread" is nearly invisible.It can be seen
on the left if you open a forum/subforum,e.g.:

[http://art.ubuntuforums.org/forumdisplay.php?f=331](http://art.ubuntuforums.org/forumdisplay.php?f=331)

Btw,you are welcome.No need for geeks here...

---

### Post by oldsoundguy on 2010-05-14
buywhatnow .. not stupid .. takes time to learn the ropes .. but find your topic, IF you can't find an answer with a search (best search is GOOGLE .. not the one furnished by the site) .. at the bottom of the topic page is a "start a new thread". .. then to track WHAT you have done .. do a search option and plug your user name into the appropriate box.  Real easy way to keep track of what you are doing.

AND mark your thread as SOLVED if it is solved.  Saves hassle for others.

You don't have to be a geek to use Ubuntu .. but you do have to exercise a bit of patience and not display gamers anxiety and want it NOW!

---

### Post by oldsoundguy on 2010-05-14
God, I love it!! .. NO MORE useless motion to scroll a page when the whole damn thing is right in front of my eyes!!

I DO love Lucid .. think it is, without a doubt, the best thing Ubuntu has done YET!!

---

### Post by bywhatnow on 2010-05-14
> **oldsoundguy said:**
> buywhatnow .. not stupid .. takes time to learn the ropes .. but find your topic, IF you can't find an answer with a search (best search is GOOGLE .. not the one furnished by the site) .. at the bottom of the topic page is a "start a new thread". .. then to track WHAT you have done .. do a search option and plug your user name into the appropriate box.  Real easy way to keep track of what you are doing.

AND mark your thread as SOLVED if it is solved.  Saves hassle for others.

You don't have to be a geek to use Ubuntu .. but you do have to exercise a bit of patience and not display gamers anxiety and want it NOW!
Thanks for telling me I'm not stupid.....but still do not see ANY link to post a new thread.....also not a gamer and NO, I don't want it now!!!!!!!!!!!!!! I thought I was just asking a question...just can't seem to find a link to allow me to ask the question in the proper form.....Please note; since I can't boot into Ubutu I am on my windows portion of my hard drive...maybe things show up differently in ubuntu than they do in Windows.........I think I may just forget trying to learn Linux since all I can get is told off and that I "must be a gamer" since I didn't follow your rules....I'm sorry to have bothered you, .....hope you have a good day and a nice life as I have just given up two hard drives and now they seem to be worthless......what you took as my impatience was just fustration......again ...sorry I bothered you without first learning your rules and regulations on asking a question

---

### Post by oldsoundguy on 2010-05-14
your skin is a tad thin .. we tried to help.

---

