---
title: "Twinview: Video tearing on second monitor"
date: 2008-08-29
forum: Multimedia Software
---

### Post by ReksZ on 2008-08-29
I've got an Nvidia 8500GT with a 19 inch CRT (on VGA) and a 22 inch LCD (on DVI) connected to it. When I fullscreen any video in mplayer, gmplayer, or vlc on my CRT monitor, everything is fine. But if I fullscreen on my 22 inch monitor, I have tearing/weird lines in my video. Some googling leads me to believe that I have to tell something somewhere to "sync" to my second monitor, but I'm kinda lost. Any help would be appreciated.

---

### Post by Ux64 on 2008-10-05
I can confirm that. I have trearing problem with both screens. It's just not perfect. Altough there seems to be "some syncing", because tearing often occures at the same point of screen and then slowly moves up or down. Meaning that there is "synchronization", it's just propably late from Vblank.

I haven't been able to solve that problem at all.

---

### Post by xreaper on 2008-10-05
I have an ATI radeon x300, and I only use one screen, and sometimes when opening video applications etc, it starts to tear. My best guess is that it has something to do with a restricted driver for a graphics card. probably a bug report about it somewhere.

---

### Post by Ux64 on 2008-10-29
> **xreaper said:**
> Probably a bug report about it somewhere.

That might be true. Because if I use windows with same hardware I don't have any problems. But with ubuntu tearing is issue. Anyway from Nvidia forums I got news that using window decorator like compiz might cause (additional / worse) tearing.

---

### Post by Phases on 2008-10-29
I've been trying to fix this for a week straight. Two different computers, one nvidia, one ATI, with or without compiz. Tried multiple driver versions/types, plenty of modules/options in xorg.conf. The similarity between the two computers is they are both dual screen setups. Although, one uses a Y cable off one card, and the other is running off two cards. I've made and read many a thread on here and have been unable to figure this out.

---

### Post by Ux64 on 2008-11-03
> **Phases said:**
> I've made and read many a thread on here and have been unable to figure this out.

So unfortunate. Like I said, I tried many things without success. Now when you have done the same job, we could conclude that it's simply NOT WORKING.

In my case it's like some kind of timing issue, with almost like an "offset" to screen bank. Because tearing point moves slowly up or downward. 

Maybe it's something to do with kernel not being able to handle time critical tasks or so. No idea.

---

### Post by Trifid on 2008-11-03
Similar problem when interacting with my second screen causing X server to crash. Maybe a bug with dual monitors running 2 X sessions?

---

### Post by Phases on 2008-11-03
First let me say, and I'm sorry for not mentioning this in my first post: But I'm not running Twinview. I'm using Xinerama + serverx-xgl. However I don't think it's limited to either, which is why I posted here. I'm seeing people post this problem in all different configurations, video drivers and cards. Maybe all I've seen reports on is dual monitor setups - but that's also part of the keywording I was searching with so.. 

> **Ux64 said:**
> So unfortunate. Like I said, I tried many things without success. Now when you have done the same job, we could conclude that it's simply NOT WORKING.

In my case it's like some kind of timing issue, with almost like an "offset" to screen bank. Because tearing point moves slowly up or downward. 

Maybe it's something to do with kernel not being able to handle time critical tasks or so. No idea.

For me, I get it when I slide windows horizontally, vertical is okay. The tearing doesn't move up or down, it's more sporatic. 

> **Trifid said:**
> Similar problem when interacting with my second screen causing X server to crash. Maybe a bug with dual monitors running 2 X sessions?

I suspect this may be the case. I haven't checked it with a single monitor though, as I don't want to rip out a card and modify my xorg.conf since it took so much work to get where I am, lol.. but it would probably benefit the cause for a single monitor config to be ruled out. 

But, I'm looking at three different dual monitor systems, ati and nvidia, all with the same problem. Have tried damn near everything.

---

### Post by Morientes on 2008-11-09
I also have this problem. I have tried with and without compiz and with and without twin view but the problem remains.

---

### Post by Ux64 on 2008-11-17
> **Trifid said:**
> Similar problem when interacting with my second screen causing X server to crash. Maybe a bug with dual monitors running 2 X sessions?

Dunno! After Ibex update everything works fine. And I can't transfer windows from session to session. But for some particual reason Nautilus windows opened from GNOME bars still open always to primary window. But if I open VLC or any other software it works ok. And there is no way to transfer windows back and forth. 

This is really really strange! ;)

And yet, tearing isn't gone. So it's still there!

---

### Post by radox1912 on 2008-12-17
i get this strange tear only, when i play movies and such.
horizontal line going up and down. really annoying
using ATI x2300
ill be watching this thread if anyone comes with solution.:popcorn:

---

### Post by themuddler on 2008-12-25
Same tearing here on intrepid using separate x-screens for laptop screen and hdtv (which is plugged in through dvi).  Using nvidia 173 (177 causes me resolution problems on second screen).  Also have the problem with nautilus opening on the wrong screen.

---

### Post by Ux64 on 2008-12-29
> **radox1912 said:**
> i get this strange tear only, when i play movies and such.
horizontal line going up and down. really annoying

We're clearly talking about same phenomenon. Do you also experience it more often at the bottom part of the screen, around are like 75% from top? It can be in upper part but it's very rare. And when ever it occures it moves "semislowly" up or downward. So it's position isn't totally random at all.

I think it's has something to do with low level task sheduling. For some reason the process updating the visible frame buffer is interrupted by some other task. I think it would be something that would cause phenomenon like what I decribed above. 

Yes, I have been programming low level display stuff over 10 years. And I have experienced similar issues. But those have been so low level systems that there hasn't been operating system with complex pre-emptive multitasing systems messing up my sheduling.

P.S. Are you using 32bit or 64bit version? I'm using 8.10 64bit right now.

Link to nvnews for those looking to solve this issue: 
[http://www.nvnews.net/vbulletin/showthread.php?t=125378](http://www.nvnews.net/vbulletin/showthread.php?t=125378)
I'll be reporting here too if the issue gets solved.

---

### Post by radox1912 on 2009-01-01
> **Ux64 said:**
> We're clearly talking about same phenomenon. Do you also experience it more often at the bottom part of the screen, around are like 75% from top? It can be in upper part but it's very rare. And when ever it occures it moves "semislowly" up or downward. So it's position isn't totally random at all.

I think it's has something to do with low level task sheduling. For some reason the process updating the visible frame buffer is interrupted by some other task. I think it would be something that would cause phenomenon like what I decribed above. 

Yes, I have been programming low level display stuff over 10 years. And I have experienced similar issues. But those have been so low level systems that there hasn't been operating system with complex pre-emptive multitasing systems messing up my sheduling.

P.S. Are you using 32bit or 64bit version? I'm using 8.10 64bit right now.

Link to nvnews for those looking to solve this issue: 
[http://www.nvnews.net/vbulletin/showthread.php?t=125378](http://www.nvnews.net/vbulletin/showthread.php?t=125378)
I'll be reporting here too if the issue gets solved.

yeah i have clearly the problem you described, the line ,,starts,, top and then goes down , but is there always, and forever :(
im ubuntu 8.10 32 bit, by the way
and everything i tried, failed: like installing driver from ubuntu repos, then from ati.amd.com, hopeless editing xorg.conf, nothing. i think theres no solution yet,also beacuse it seems to be very rare problem, or is everyone overlooking this?
by the way, also tried endless list of players(vlc, totem, xine,...), also tried different video outputs: like xv, x11 opengl..
appareantly, it happens on mobility radeon only?, especially on x-cards like mine x2300 mobility radeon.
and by the way on Windoze everything seems to be fine.

ill be checking your thread, thx, hopefully is there still hope for us, mobility owners:(

---

### Post by Ux64 on 2009-01-02
One huge difference is that I'm using Nvidia 8500GT, not ATI or laptop mobility adapter.

So, it clearly tells me that the issue is deeper in system. Maybe kernel timing issue or something like that. (even this is still just poorly educated guess)

I also can confirm that there is no problem what so evern when using Windows Vista. So it's not a hardware issue.

---

### Post by radox1912 on 2009-01-02
but i remember, that once this problem didnt occure. but it was few months ago, with older kernel of course.
i had some trouble (obviusly i was setting my graphic), so i booted ubuntu in safe mode, and played some video. i was amazed there was nothing wrong with the video.

conclusion: there must be something that disturbs fullscreen video playback.

by the way, are you experiencing this problem in non-fullscreen mode? im not, just fullscreen makes me mad...

---

### Post by The_Rebel52 on 2009-01-03
I have the exact same issue and i have tried almost everything to resolve it.. only thing i can thing of.. maybe the kernel needs tweaking to handle 2 displays at once?

Could someone with an Nvidia chipset try twinview with the open source driver? (or does it even support twinview?)

I bet matrox cards work perfectly..

---

### Post by Ux64 on 2009-01-07
> **radox1912 said:**
> by the way, are you experiencing this problem in non-fullscreen mode? im not, just fullscreen makes me mad...

Interesting suggestion/question, I'll have to check this out. I'll edit this message as soon as I know.

Confirmed, tearing appears in windowed & full screen modes. No difference what so ever. And on both screens.

---

### Post by powdermaniaDE on 2009-01-08
I also have the tearing problem with twin view on my think pad T61 (1680x1050) and an additional samsung syncMaster 19" (1600x1200). Im using NVIDIA X Server Settings. 

My System: Ubuntu 8.10 (2.6.27-11-generic) (Linux-x86_64)
NVIDIA Driver Version 177.82

The effect of the tearing is gone if I, e.g. switch back and forth between browser tabs. On scrolling down the tearing reappears. As far as I know the tearing does not happen on single screen.

---

### Post by element_G on 2009-01-08
Am also having this problem for quite a while on my home machine (see specs in sig) with various nvidia drivers and kernels (now using latest intrepid and nvidia 180.06) 

Found this on nvnews, looks like you have to turn on vsync in every setting dialog you can find it. Haven't tried it as I'm not at home now but will update when I can

[http://www.nvnews.net/vbulletin/showthread.php?p=1894576](http://www.nvnews.net/vbulletin/showthread.php?p=1894576)

---

### Post by Ux64 on 2009-01-09
> **element_G said:**
> Am also having this problem for quite a while on my home machine (see specs in sig) with various nvidia drivers and kernels (now using latest intrepid and nvidia 180.06) 

Found this on nvnews, looks like you have to turn on vsync in every setting dialog you can find it. Haven't tried it as I'm not at home now but will update when I can

[http://www.nvnews.net/vbulletin/showthread.php?p=1894576](http://www.nvnews.net/vbulletin/showthread.php?p=1894576)

It's not about that. VSync is mostly working, it's not 100% tearing all the time, which happens if I disable vsync. Sometimes everything go fine for a quite long while before it appears again. And when it appears it's often more like slightly chainging offset for VSync so it'll slide down or up. 

I did check that vsync is enabled everywhere and it is. 

But yeah, it's better to check that compiz is disabled and all vsyncs are enabled. But it's not the solution for this problem right now.

---

### Post by radox1912 on 2009-01-09
hm, how can i check , if i have vsync on ?

---

### Post by radox1912 on 2009-02-12
i finally figured it out !! but i dont think it will work on nvidia too..  

[http://ubuntuforums.org/showthread.php?p=6715096#post6715096](http://ubuntuforums.org/showthread.php?p=6715096#post6715096)

---

### Post by The_Rebel52 on 2009-02-12
> **radox1912 said:**
> i finally figured it out !! but i dont think it will work on nvidia too..  

[http://ubuntuforums.org/showthread.php?p=6715096#post6715096](http://ubuntuforums.org/showthread.php?p=6715096#post6715096)

LOL, you have no clue about what problems we have.

No matter how many applications you set vertical refresh to it'll still fail to do so on the second display.

This is something Nvidia needs to fix, not us.

---

### Post by Ux64 on 2009-02-24
I might have a clue what might be affecting it. It's the primary screens sync / graphics.

I had iGoogle with "technology" page open. It showed some flash star system and satellite tracking. It caused huge frame skipping / tearing issue on secondary screen.

I have to investigate more.

Next I'll try disabling first screen sync, and see if it is the solution.

Like I said problem is strange, and actually it could be result of interference between first and second screen syncs.

---

### Post by RomD on 2009-02-26
The problem with Twinview is that both screens are handled like one big surface. Twinview has to sync to one of the monitors, which causes tearing on the other. You should be able to set the target sync screen in nvidia-settings, but I couldn't manage to do so on my machine. I decided to use separated X screens to circumvent this problem.

See this thread: [http://forum.compiz-fusion.org/showthread.php?t=7405](http://forum.compiz-fusion.org/showthread.php?t=7405)

---

### Post by Ux64 on 2009-03-09
I'm not using twinview anymore. Because it didn't allow me to set screen contrast correctly.

[http://www.nvnews.net/vbulletin/showthread.php?t=117936](http://www.nvnews.net/vbulletin/showthread.php?t=117936)

Now I have two separate screens, but I still get this same tearing issue even if I got vblank sync enabled for both screens separately.

---

### Post by Ux64 on 2009-04-04
> **ReksZ said:**
> I've got an Nvidia 8500GT with a 19 inch CRT (on VGA) and a 22 inch LCD (on DVI) connected to it. When I fullscreen any video in mplayer, gmplayer, or vlc on my CRT monitor, everything is fine. But if I fullscreen on my 22 inch monitor, I have tearing/weird lines in my video. Some googling leads me to believe that I have to tell something somewhere to "sync" to my second monitor, but I'm kinda lost. Any help would be appreciated.

I wrote again about this topic to NVnews, hoping that someone would really take a look and get it fixed.

 - Thank you!

[http://www.nvnews.net/vbulletin/showthread.php?p=1975302#post1975302](http://www.nvnews.net/vbulletin/showthread.php?p=1975302#post1975302)

---

### Post by ubu-for on 2009-04-04
> **RomD said:**
> The problem with Twinview is that both screens are handled like one big surface. Twinview has to sync to one of the monitors, which causes tearing on the other.
You could try "Separate X Screen" instead.

[http://ubuntuforums.org/showthread.php?t=23628](http://ubuntuforums.org/showthread.php?t=23628)
[http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456)

---

### Post by Ux64 on 2009-04-04
> **ubu-for said:**
> You could try "Separate X Screen" instead.

[http://ubuntuforums.org/showthread.php?t=23628](http://ubuntuforums.org/showthread.php?t=23628)
[http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456)

Yes, I'm currently using Separete X Screens, due the fact that using single screen didn't allow me to set contrast for screens separately. Which is unacceptable for home theather use.

[http://ubuntuforums.org/showthread.php?t=887762](http://ubuntuforums.org/showthread.php?t=887762)

And other people are also using different configurations, but nobody has been this far able to get rid of tearing.

Yes, I have used nvidia config to enable sync for both screens etc and my current X.org:
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Thu Jun  5 09:27:12 UTC 2008

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
#    Identifier     "Configured Mouse"
#    Driver         "mouse"
#    Option         "CorePointer"
#    Option         "Device" "/dev/input/mice"
#    Option         "Protocol" "ExplorerPS/2"
##     Option         "Protocol" "ImPS/2"
#    Option         "Buttons" "10"
#    Option         "ZAxisMapping" "4 5"
#    Option         "ButtonMapping" "1 2 3 6 7"
#    Option         "Emulate3Buttons" "true"
#EndSection

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 1600 0
# commented out by update-manager, HAL is now used
#    InputDevice    "Generic Keyboard"
# commented out by update-manager, HAL is now used
#    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
# Removed Option "Xinerama" "1"
    Option         "Xinerama" "0"
EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    Identifier     "Generic Keyboard"
#    Driver         "kbd"
#    Option         "CoreKeyboard"
#    Option         "XkbRules" "xorg"
#    Option         "XkbModel" "pc105"
#    Option         "XkbLayout" "fi"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    Identifier     "Configured Mouse"
#    Driver         "mouse"
#    Option         "CorePointer"
#    Option         "Device" "/dev/input/mice"
#    Option         "Protocol" "ExplorerPS/2"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    Identifier     "stylus"
#    Driver         "wacom"
#    Option         "Device" "/dev/input/wacom"
#    Option         "Type" "stylus"
#    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    Identifier     "eraser"
#    Driver         "wacom"
#    Option         "Device" "/dev/input/wacom"
#    Option         "Type" "eraser"
#    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#    Identifier     "cursor"
#    Driver         "wacom"
#    Option         "Device" "/dev/input/wacom"
#    Option         "Type" "cursor"
#    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
#EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    VendorName     "Generic CRT Display"
    ModelName      "Monitor 1600x1200"
    HorizSync       31.5 - 107.5
    VertRefresh     50.0 - 85.0
    Gamma           1
    ModeLine       "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    Option         "DPMS"
    Option         "OffTime" "5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "FUS P20-2"
    HorizSync       30.0 - 82.0
    VertRefresh     51.0 - 75.0
    Option         "DPMS"
    Option         "OffTime" "5"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       30.0 - 82.0
    VertRefresh     51.0 - 75.0
    Option         "DPMS"
    Option         "OffTime" "5"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8500 GT]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          0
    Option         "UseEvents" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:1:0:0"
    Screen          0
    Option         "UseEvents" "True"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:1:0:0"
    Screen          1
    Option         "UseEvents" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8500 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     3520 1200
        Depth       24
        Modes      "1600x1200@75"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "TwinView" "1"
# Removed Option "metamodes" "TV: 1920x1080 +1600+0, DFP: 1600x1200 +0+0"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TVStandard" "HD1080i"
    Option         "TVOutFormat" "COMPONENT"
    Option         "UseDisplayDevice" "TV"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 1920x1080 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: 1600x1200 +0+0"
EndSection


```

And my Nvidia-config-rc

```

#
# /home/sl/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Sun Feb  1 19:14:15 2009
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes
Timer = Thermal_Monitor_(GPU_0),Yes,1000
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000

# Attributes:

0/DigitalVibrance[DFP-0]=0
0/SyncToVBlank=1
0/AllowFlipping=1
0/LogAniso=0
0/FSAA=0
0/TextureSharpen=0
0/CursorShadow=1
0/CursorShadowXOffset=4
0/CursorShadowYOffset=2
0/CursorShadowAlpha=64
0/CursorShadowRed=0
0/CursorShadowGreen=0
0/CursorShadowBlue=0
0/FSAAAppControlled=1
0/LogAnisoAppControlled=1
0/GPUScaling[DFP-0]=131073
0/FSAAAppEnhanced=0
0/RedBrightness=0.000000
0/GreenBrightness=0.000000
0/BlueBrightness=0.000000
0/RedContrast=0.000000
0/GreenContrast=0.000000
0/BlueContrast=0.000000
0/RedGamma=1.000000
0/GreenGamma=1.000000
0/BlueGamma=1.000000
0/OpenGLImageSettings=1
0/XVideoTextureBrightness=-8
0/XVideoTextureContrast=4096
0/XVideoTextureHue=0
0/XVideoTextureSaturation=4096
0/XVideoTextureSyncToVBlank=1
0/XVideoSyncToDisplay=65536
1/DigitalVibrance[TV-0]=0
1/SyncToVBlank=1
1/AllowFlipping=1
1/LogAniso=0
1/FSAA=0
1/TextureSharpen=0
1/CursorShadow=0
1/CursorShadowXOffset=4
1/CursorShadowYOffset=2
1/CursorShadowAlpha=64
1/CursorShadowRed=0
1/CursorShadowGreen=0
1/CursorShadowBlue=0
1/FSAAAppControlled=1
1/LogAnisoAppControlled=1
1/FSAAAppEnhanced=0
1/RedBrightness=0.000000
1/GreenBrightness=0.000000
1/BlueBrightness=0.000000
1/RedContrast=-0.200000
1/GreenContrast=-0.200000
1/BlueContrast=-0.200000
1/RedGamma=1.000000
1/GreenGamma=1.000000
1/BlueGamma=1.000000
1/OpenGLImageSettings=1
1/XVideoTextureBrightness=0
1/XVideoTextureContrast=4096
1/XVideoTextureHue=0
1/XVideoTextureSaturation=4096
1/XVideoTextureSyncToVBlank=1
1/XVideoSyncToDisplay=256

```

---

### Post by ubu-for on 2009-04-04
> **Ux64 said:**
> Yes, I'm currently using Separete X Screens, due the fact that using single screen didn't allow me to set contrast for screens separately.
But you already know that in your xorg.conf are still some Twinview options? I don't know, if you should "comment them out" (#) but I don't think they are necessary.

Here is my xorg.conf but I can't find out why VLC and Totem open up only on my PC monitor and not on my TV like Ogle.

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Simple Layout" #"Default Layout" (Jaunty default)
    Screen 0	   "Screen0" #"Screen0" 0 0          (Jaunty default)
    Screen 1	   "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

#Section "ServerFlags"			(Jaunty default)
#    Option         "Xinerama" "0"	(Jaunty default)
#EndSection				(Jaunty default)

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "ImPS/2" #"auto" (Jaunty default)
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "true" #"no" (Jaunty default)
    Option         "ZAxisMapping" "4 5"
EndSection

#Section "Monitor"
#    Identifier     "Configured Monitor"
#EndSection

Section "Monitor"
    Identifier     "MD30219PH"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

# NEU
Section "Monitor" 
	Identifier	"TV" 
	HorizSync	15-45 # 31.47 # 60
	VertRefresh	50-60 # 59.94 # 56-76 
EndSection
# NEU ENDE

#Section "Device"				(Jaunty default)
#    Identifier     "Configured Video Device"	(Jaunty default)
#    Driver         "nvidia"			(Jaunty default)
#    Option         "NoLogo" "True"		(Jaunty default)
#EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7950 GT"
    # NEU
    Screen 0
    Option         "ConnectedMonitor" "MD30219PH"
    # NEU ENDE

EndSection

# NEU
Section "Device" 
   	Driver          "nvidia" 
   	Identifier      "Device1" 
   	Screen 1 
	Option          "TVOutFormat" "COMPOSITE" #or "S-VIDEO" etc 
   	Option          "TVStandard" "HD576p" #"PAL-G" or NTSC, PAL-B etc 
   	Option          "ConnectedMonitor" "TV" 
   	#BusID           "PCI:5:0:0" # adjust using 'lspci' or cat /proc/pci # "PCI:1:0:0"
EndSection
# NEU ENDE

#Section "Screen"				(Jaunty default)
#    Identifier     "Default Screen"		(Jaunty default)
#    Device         "Configured Video Device"	(Jaunty default)
#    Monitor        "Configured Monitor"	(Jaunty default)
#    DefaultDepth    24				(Jaunty default)
#EndSection					(Jaunty default)

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "MD30219PH"
    DefaultDepth    24
    #Option         "TwinView" "1"								(Jaunty default)
    #Option         "metamodes" "TV: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0"	(Jaunty default)
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

# NEU
Section "Screen" 
	Device		"Device1" 
	Identifier	"Screen1" 
	Monitor		"TV" 
	DefaultDepth	24 
	SubSection "Display" 
		Depth 24 
		Modes "576p" "720x576" #"852x480" 
	EndSubSection
EndSection
# NEU ENDE
```

---

### Post by shinew on 2009-04-06
I'm experimenting with "Separated X screen" too because I cannot set seprate color profiles for NVidia Geforce 9500GT Dual DVI card. Is there a way to move the window from one screen to another?(I don't need the ability to actually "drag it").

For tearing, i have it too but "metacity --replace" fixes it for me. So when i watch movie, I use metacity and change it back when I'm done.

---

### Post by Ux64 on 2009-04-06
> **shinew said:**
> For tearing, i have it too but "metacity --replace" fixes it for me. So when i watch movie, I use metacity and change it back when I'm done.

I'm using metacity all the time. Because Compiz caused funny (and not so fun) problems.

But that didn't fix it for me. Is there any special VLC settings that might help? 

I would like to have screens as totally different sessions or I would like to have them as separate desktops. But it seems that either of options seem to be working. Those would be most logic options, after forming one big screen. Then I could use normal move to desktop 1,2,3,4 etc options to move windows from desktop to another.

X seems to be pretty buggy and not so useful. Also yet another problem is that if I launc programs from secondary screen, screens often open on first screen. Nautilus seems to be doing that all the time. So many bugs... So I'm not really suppriced that complicated issues like sync isn't working, when system is barely working in general.

---

### Post by Ux64 on 2009-05-01
Just reporting that I updated to Jaunty and VLC 0.9.4 and Nvidia 180.44 driver. Yet, no change. Tearing is still an issue.

Ok, people get used to tearing, so it's not serious issue. But it still before you'll learn how to ignore it. Some times vertical scrolling looks horrible.

---

### Post by The_Rebel52 on 2009-05-01
> **Ux64 said:**
> Just reporting that I updated to Jaunty and VLC 0.9.4 and Nvidia 180.44 driver. Yet, no change. Tearing is still an issue.

Ok, people get used to tearing, so it's not serious issue. But it still before you'll learn how to ignore it. Some times vertical scrolling looks horrible.

That's the Linux spirit - ignore the problems and keeping forking away.

---

### Post by Ux64 on 2009-05-03
> **The_Rebel52 said:**
> That's the Linux spirit - ignore the problems and keeping forking away.

Hey! I did attack this problem once more. And I did get it to work. Because in Nvidia support forums they told me that there is no problem what so ever. I did believe them. I don't often believe random forum stuff, but that was authorative enough.

So I did rebuild xorg.conf totally, did delete all nvidia related settings. Did uninstall and reinstall driver and updated VLC to 1.0 pre and deleted all configuration and rebuild it's config. And guess what, now it's working.

It might be that I had some "legacy payload" from way old Ubuntu versions. I also tried with and without success many X configurations and had to fight with full screen mode working at all on secondary screen. So there might have been multiple overlapping reasons why it didn't work out.

But now it's working.

So if you're suffering from same problem with VLC I can tell you that it's working with 8500gt after all.

Also full hd x264 1080p stuff is running nicely on both screens simultaneously.

Offtopic: I'm not too eager anymore to fight with problems. I'm bit too old. I have already waster 20 years of my life fighting different kind of software and hardware problems almost 24/7 (when ever I'm not sleeping). I think it's time to try do something different. (???)

---

### Post by The_Rebel52 on 2009-05-03
> **Ux64 said:**
> Hey! I did attack this problem once more. And I did get it to work. Because in Nvidia support forums they told me that there is no problem what so ever. I did believe them. I don't often believe random forum stuff, but that was authorative enough.

So I did rebuild xorg.conf totally, did delete all nvidia related settings. Did uninstall and reinstall driver and updated VLC to 1.0 pre and deleted all configuration and rebuild it's config. And guess what, now it's working.

It might be that I had some "legacy payload" from way old Ubuntu versions. I also tried with and without success many X configurations and had to fight with full screen mode working at all on secondary screen. So there might have been multiple overlapping reasons why it didn't work out.

But now it's working.

So if you're suffering from same problem with VLC I can tell you that it's working with 8500gt after all.

Also full hd x264 1080p stuff is running nicely on both screens simultaneously.

Offtopic: I'm not too eager anymore to fight with problems. I'm bit too old. I have already waster 20 years of my life fighting different kind of software and hardware problems almost 24/7 (when ever I'm not sleeping). I think it's time to try do something different. (???)

Interesting.. I'll have to try again with Jaunty (I'm currently using Windows 7 and it goes above and beyond anything out there)

---

### Post by ScottDeagan on 2012-06-24
It's 2012, I'm using Ubuntu 12.04 with a GTX460. TwinView still results in tearing on secondary monitor.

---

