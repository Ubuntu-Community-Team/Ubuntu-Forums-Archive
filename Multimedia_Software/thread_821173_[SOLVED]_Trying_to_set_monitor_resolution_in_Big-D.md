---
title: "[SOLVED] Trying to set monitor resolution in Big-Desktop (Ubuntu 8.04)"
date: 2008-06-06
forum: Multimedia Software
---

### Post by MaxMax on 2008-06-06
Hello,

I installed Ubuntu 8.04 on my Windows XP computer, hoping to switch to it if I can get it to work. I love it so far but I am stumbling on a major (for me) problem.

In both Ubuntu and XP, I am using two monitors. [Big-Desktop]("http://ubuntuforums.org/showthread.php?t=301941") works well in Ubuntu, but the maximum resolution I get is 2048x768, while on the same machine MS Windows gives me 2560x1024.

Having used that higher resolution for years, going down to 2048x768 is unusable. However, I can't seem to find a way to tell Ubuntu to go to 2560x1024.

My monitors are a Dell M783s and a NEC AccuSync 70. My video card is an ATI Radeon X300. When I do xrandr -q, I get the following:

```
~$ xrandr -q
Screen 0: minimum 320 x 200, current 2048 x 768, maximum 2048 x 768
default connected 2048x768+0+0 0mm x 0mm
   2048x768       60.0* 
   1024x768       60.0  
   1024x480       60.0  
   848x480        60.0  
   800x600        60.0     56.0     47.0  
   720x576        60.0  
   720x480        60.0  
   640x480        60.0  
   640x400        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        60.0  
   320x200        60.0  
```

Catalyst Control Center lists my two monitors as "Default Monitor" 1 and 2, with a maximum resolution of 1024x768 each. In Windows, I get 1280x1024 for each, and Windows can identify their brand names and models. 

Being new to Ubuntu, I need help. Can someone point me in the right direction so I can tell Ubuntu how to recognize those monitors properly and give me the higher resolution they can display?

Thanks -- Max

---

### Post by kharybdis on 2008-06-23
I am having this exact problem.

I am using a ATI All In Wonder 9600 and two identical Dell E17fp monitors.  


My xorg.conf:

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "1280x1024+1280x1024,0x0+0x0"
	Option	    "EnableMonitor" "crt1,crt2"
	Option	    "ForceMonitors" "crt1,crt2"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

---

### Post by ~humanity on 2008-07-06
Hi, I think I have the same problem as you. I'm using 2 Viewsonic VA905 monitors (19" 3:4 with ideal resolution of 1280*1024) on a Asus Radeon HD3450.

I managed to get the ATI drivers working with Big-Desktop, but I'm capped at 2048*768 which does not look good. 

My [xorg.conf]("http://docs.google.com/Doc?id=dccq4c29_75nz7tjrcs").

I don't know how well the hardware works in Windoze as it utterly refuses to work. (Finally got me to start using Linux).

Any help would be appreciated.

---

### Post by MaxMax on 2008-07-06
That problem is huge for me, because it is forcing me to go back to Windows XP on my personal computer. I still use Ubuntu on the laptop and I love it and it is painful to be forced back into Windows.

I hope the "Big-Desktop" team is reading this forum and working to find a solution to this. Or I wish someone in here is close to them and will forward this as a bug report. If any technical details are needed to help fix it, I'll happily provide them.

2048x768 on two monitors gives me barely more working space than a single monitor running at 1280x1024. I need twice as much to get some actual work done. 

HEEEEEEEEEEEELP ME!!!!! I DON'T WANT TO BE STUCK WITH WINDOWS!!!!! :-(

---

### Post by ~humanity on 2008-07-06
I can't even go back to Windows, I tried installing it 3 times on an independent hard drive and all three times is just bsods on me. Not that I'm complaining too loudly, people might start asking about the cd key.

---

### Post by pmaciver on 2008-07-08
Well like most people here I'm having trouble doing this BigDesktop thing properly.

My problem is that although I have Big Desktop working, I can't get each of the monitors to display at their correct resolution (1600x1200) when I try

sudo aticonfig --desktop-setup=horizontal --sync-vsync=on --add pairmode=1600x1200+1600x1200

I get the message

FGLRX_AddPairMode failed when try to add mode : 1600x1200+1600x1200

Just like many others.

My graphics card is a Radeon HD 2600 Series

And my xorg.config look as follows
* by the way both my monitors are exactly the same make model and resolution.


Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "gb"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Monitor"
Identifier "aticonfig-Monitor[0]-0"
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
Option "DPMS" "true"
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Device"
Identifier "aticonfig-Device[0]-0"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "DesktopSetup" "horizontal"
Option "Capabilities" "0x00000800"
Option "PairModes" "1024x768+1024x768"
BusID "PCI:1:0:0"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
EndSection

Section "Screen"
Identifier "aticonfig-Screen[0]-0"
Device "aticonfig-Device[0]-0"
Monitor "aticonfig-Monitor[0]-0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
EndSubSection
EndSection

Also I know that the

Option "PairModes" "1024x768+1024x768"

is not set correctly, but even when I change this by hand it still doesn't work, and when I run

sudo aticonfig --desktop-setup=horizontal --sync-vsync=on --add pairmode=1600x1200+1600x1200

it sets that line back to what you see now.

I have been trying to get this working for 2 days now, and feel like throwing one of the monitors out the window because it is so frustrating.

Oh and I am using the drivers that I found on the ati website here

[http://ati.amd.com/support/drivers/l...ux-radeon.html](http://ati.amd.com/support/drivers/l...ux-radeon.html)

and this driver

[https://a248.e.akamai.net/f/674/9206...x86.x86_64.run](https://a248.e.akamai.net/f/674/9206...x86.x86_64.run)

I hope someone can help me out with this or at lease point me in the right direction.

Thanks in advance.

---

### Post by Chachee on 2008-07-08
Same problem as everyone else.  I have 2 24in Dell's and the best resolution I can get out of them now is 2048x768.  I want to run 1680x1050.  

I have a ATI 9600XT with the restricted drivers from the distro installed.

Using the aticonfig command I get:

```
sudo aticonfig --add-pairmode=1680x1050+1680x1050
FGLRX_AddPairMode failed when try to add mode : 1680x1050+1680x1050 
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-12

```

And it switches the .conf to:
```
Option	    "PairModes" "0x0+0x0,1024x768+1024x768"
```

Manually editing by hand does no good either.

I'll keep researching, but if someone knows please clue us in.

JT

---

### Post by Chachee on 2008-07-08
All right,
  I give up.  I'll take my 2 mirrored displays back.  But now I can't even get that high resolution back.  Current .conf
```

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
	Screen         "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "EnableMonitor" "crt1,tmds1"
	Option	    "DesktopSetup" "mirror"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "1680x1050"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

```

I couldn't find my back up.. I was stuipd and did a 'mv' instead of a 'cp' the las time I used it.  So I tried the ```
sudo dpkg-reconfigure -phigh xserver-xorg
```   

I still have big desktop!

I tried ```
aticonfig --dtop=mirror
```

I can't get my original resolutions back!  I've spent about 2 hrs on this now.  I'd rather not reload if I don't have to.

Thanks.

JT

---

### Post by pmaciver on 2008-07-09
Hey, I just solved my problem, you can read about it here 

[http://ubuntuforums.org/showthread.php?p=5349139&posted=1#post5349139](http://ubuntuforums.org/showthread.php?p=5349139&posted=1#post5349139)

---

### Post by MaxMax on 2008-07-27
Based on pmaciver's solution mentioned above, here are the exact steps I followed to solve my own similar problem (described in the first message of this thread):

[LIST=1]
[*] Re-install Ubuntu 8.04 from the CD, overwriting the previous version *(annyoing but worth it, since it worked)*.
[*] Login to user account, and ignore *(for now)* all update notifications
[*] Click on the main menu "**Applications** / **Add/Remove...**"
[*] Get **ATI binary X.Org driver** and also get **ATI Catalyst Control Center**
[*] Once they are installed, close "Add/Remove..." *(I might have been asked to reboot at this point, if so I did and re-logged in)*
[*] Click on the main menu "**Applications** / **Other** / **ATI Catalyst Control Center**"
[*] Click on the **Display Manager** *(on the left side of the window)*
[*] Click on the **Display Modes** tab *(near the middle of that window)*
[*] Select **Big Desktop** from the dropdown list
[*] At this point, the two monitors remain cloned and they jump into a incorrect resolution... I click accept anyway and I reboot
[*] After I re-login, I have a Big-Desktop spread correctly over my two monitors, and the resolution is 2560x1024 *(magically)*
[*] At this point, I click on the Update Notification icon and let it update everything.
[/LIST]
Why didn't it work like that the first time??

When I first installed Ubuntu, I remember reading a strong warning when I was about to install the ATI binary driver. Being a newbie, it sounded risky and I decided to go for the open source ATI driver instead. Turns out those open source drivers where the ones I should have been warned about!!!!!. From that point on, it took weeks just to get the Big-Desktop working and a subsequent installation of the ATI binary driver never worked correctly. I hate being a newbie, but I really wanted to give Ubuntu a try, so thanks to **[COLOR="Red"]pmaciver[/COLOR]** for finding the solution! Ubuntu looks great on two monitors, and now I can get some actual work done with it! Hopefully I will pleasantly move away from XP and never have to sink into Vista -- MaxMax

---

### Post by Phlogiston on 2008-08-30
Please post the xorg.conf used when its working! Thanks a lot!

---

### Post by MaxMax on 2008-08-31
Hello Phlogiston,

You'll see my xorg.conf at the end of this message. You'll see it's just the standard one, because the way to make this work is by getting the **ATI binary X.Org driver** and also getting the **ATI Catalyst Control Center** and then doing the Big-Desktop configuration from that last one (as described in my previous message to this thread). It doesn't use the xorg.conf, as you can see below:

```
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

Hope this helps!

---

### Post by twisted_steel on 2008-09-10
> **Chachee said:**
> Same problem as everyone else.  I have 2 24in Dell's and the best resolution I can get out of them now is 2048x768.  I want to run 1680x1050.  

I have a ATI 9600XT with the restricted drivers from the distro installed.


I also have a 9600XT in my desktop with two 1680x1050 monitors.  I had the restricted drivers working up to the same place where you got stuck.  I tried to reset everything back to defaults and cross my fingers and then reenable BigDesktop, but I failed.

I then decided to just see if the open source "ati" driver would do the trick after reading pmaciver's post.  I completely removed the restricted drivers and after a little configuring, I got it to work.  The only problem I had was Ubuntu/GNOME made my right (VGA) monitor my 'main' screen and made my left (DVI) monitor the extra desktop.  I got around that by dragging all of the panels over to my left monitor.

Here is the output from "xrandr -q" which displayed a max of 1680x1200 before I added in the Virtual line to my xorg.conf:

```
user@hostname:~$ xrandr -q
Screen 0: minimum 320 x 200, current 3360 x 1050, maximum 3360 x 1050
VGA-0 connected 1680x1050+1680+0 (normal left inverted right x axis y axis) 434mm x 270mm
   1680x1050      59.9*+   60.0  
   1280x1024      59.9  
   1440x900       59.9  
   1280x960       59.9  
   1152x864       75.0     74.8  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3     56.2  
   640x480        75.0     60.0  
   720x400        70.1  
DVI-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 434mm x 270mm
   1680x1050      59.9*+   60.0  
   1280x1024      59.9  
   1440x900       59.9  
   1280x960       59.9  
   1152x864       75.0     74.8  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3     56.2  
   640x480        75.0     60.0  
   720x400        70.1  
S-video disconnected (normal left inverted right x axis y axis)

```Here is my xorg.conf.  I have no idea if the right/left is correct because I just kept messing around without any changes.  I think one might make the mouse movement incorrect (e.g. I could only move right on my right monitor to get to the left).

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "vmmouse"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "USB"   "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "USB"   "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "USB"   "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "pad"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "pad"
        Option          "ButtonsOnly"   "on"
        Option          "USB"   "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "pad"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "pad"
        Option          "ButtonsOnly"   "on"
        Option          "USB"   "on"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
        Option          "Monitor-DVI-0" "DVI-0"
        Option          "Monitor-VGA-0" "VGA-0"
EndSection

Section "Monitor"
        Identifier      "DVI-0"
        Horizsync       30-70
        Vertrefresh     50-160
EndSection

Section "Monitor"
        Identifier      "VGA-0"
        Horizsync       30-70
        Vertrefresh     50-160
        Option          "RightOf"       "DVI-0"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
        SubSection      "Display"
                Virtual 3360 1050 # 1680 x 2 = 3360
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
        Inputdevice     "pad"
EndSection
Section "Module"
        Load            "glx"
EndSection

```

---

### Post by 73ckn797 on 2008-09-21
> **MaxMax said:**
> Based on pmaciver's solution mentioned above, here are the exact steps I followed to solve my own similar problem (described in the first message of this thread):

[LIST=1]
[*] Re-install Ubuntu 8.04 from the CD, overwriting the previous version *(annyoing but worth it, since it worked)*.
[*] Login to user account, and ignore *(for now)* all update notifications
[*] Click on the main menu "**Applications** / **Add/Remove...**"
[*] Get **ATI binary X.Org driver** and also get **ATI Catalyst Control Center**
[*] Once they are installed, close "Add/Remove..." *(I might have been asked to reboot at this point, if so I did and re-logged in)*
[*] Click on the main menu "**Applications** / **Other** / **ATI Catalyst Control Center**"
[*] Click on the **Display Manager** *(on the left side of the window)*
[*] Click on the **Display Modes** tab *(near the middle of that window)*
[*] Select **Big Desktop** from the dropdown list
[*] At this point, the two monitors remain cloned and they jump into a incorrect resolution... I click accept anyway and I reboot
[*] After I re-login, I have a Big-Desktop spread correctly over my two monitors, and the resolution is 2560x1024 *(magically)*
[*] At this point, I click on the Update Notification icon and let it update everything.
[/LIST]
Do you think this will work with the ATI Radeon HD 3450 on one monitor? Dumb question (Yes?) but I actually assume that to be true.
The Catalyst Center may be the way to be able to set things up. I have had multiple failures trying to make the video card work properly. Catalyst has not been installed before. When I reboot the system will not boot past a little blue message saying "Out of Range". I would have to reboot and let system reconfigure first. 

I have earlier posts regarding this whole issue but have either not received response or no follow-up was given to what I submitted for review.

---

### Post by 73ckn797 on 2008-09-21
> **MaxMax said:**
> Based on pmaciver's solution mentioned above, here are the exact steps I followed to solve my own similar problem (described in the first message of this thread):

[LIST=1]
[*] Re-install Ubuntu 8.04 from the CD, overwriting the previous version *(annyoing but worth it, since it worked)*.
[*] Login to user account, and ignore *(for now)* all update notifications
[*] Click on the main menu "**Applications** / **Add/Remove...**"
[*] Get **ATI binary X.Org driver** and also get **ATI Catalyst Control Center**
[*] Once they are installed, close "Add/Remove..." *(I might have been asked to reboot at this point, if so I did and re-logged in)*
[*] Click on the main menu "**Applications** / **Other** / **ATI Catalyst Control Center**"
[*] Click on the **Display Manager** *(on the left side of the window)*
[*] Click on the **Display Modes** tab *(near the middle of that window)*
[*] Select **Big Desktop** from the dropdown list
[*] At this point, the two monitors remain cloned and they jump into a incorrect resolution... I click accept anyway and I reboot
[*] After I re-login, I have a Big-Desktop spread correctly over my two monitors, and the resolution is 2560x1024 *(magically)*
[*] At this point, I click on the Update Notification icon and let it update everything.
[/LIST]
 Thanks for this information. I have been searching for a solution for the ATI Radeon HD 3450 and your procedure worked. I did have to add one more step in the process which I will insert as step 6. I still had to install the ATI restricted driver before Catalyst would work because it found no ATI video driver. I did not follow any of the previous steps that MaxMax stated  were followed, only these steps.

I will paste your solution with my added step in the proper forum to pass along for others to benefit from. I will mention your user name with full credit.

Thanks again.

---

### Post by MaxMax on 2008-09-21
I'm happy this worked for you too! Enjoy Ubuntu!!

---

