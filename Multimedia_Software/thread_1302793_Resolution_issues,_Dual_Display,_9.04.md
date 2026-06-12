---
title: "Resolution issues, Dual Display, 9.04"
date: 2009-10-27
forum: Multimedia Software
---

### Post by htt-thalan on 2009-10-27
Hi guys,

my first post on your extensive forum and immediately one with a problem.
Right off the bat: I'm a Linux noob. I figured I should be ashamed for being a 27-year old IT consultant/salesman and not knowing how to do basic stuff with Linux rather than a Microsoft OS, so over a month ago I wiped my Vista install and installed Ubuntu 9.04 x64. So far I've managed quite some stuff, working with the command line, playing some of my old Windows games, (WoW, Counterstrike, C&C3) and replaced all my other software (office, shoutcast stuff, etc) with Open Source alternatives. 

I've been keeping track of things through a topic on a dutch forum (tweakers) but ran into an issue which we haven't been able to solve yet.

Here it goes.

As the title allready says, I'm running 2 displays. Display #1 is an HP L2045w doing 1680*1050, display #2 an HP L1740 doing 1280*1024. On Vista, as many will know, this is easy-peasy, plug and play, even my granny could do it. You check the box 'extend' and all is well. With Ubuntu, things didn't go exactly as smooth as I wanted it to go, but hey, I was on a steep learning curve, and I managed to get it running. I can drag apps from left to right, they will maximize on the correct display, I even get the 'yelly pudding' effect when I forcibly pull an app 'from' fullscreen to un-maximize it.

And there is when things get ugly. Warcraft is not a problem: That runs 'windowed fullscreen' on 1680*1050 like it has always done for me on Windows. My native linux apps however, get pushed (i have no influence on that whatsoever) to a whopping 2920*1050 resolution. Thats funny, but far from practical. I ran Unreal tournament '99 native, for instance. The game options menu gives me all but one choice: The aforementioned resolution. I tried to override this via the unrealtourament.ini and user.ini but to no avail. I tried command line options - no result there either.

The problems arise with almost every native Linux app which I would like to run fullscreen: Wormux, OpenArena, you name them. I either have to run them windowed in a resolution lower than native, fullscreen stretched from left to right, or windowed on a native resolution which keeps the ubuntu menu bars active, effectively rendering a piece of my gaming area unreachable, because they 'hide' behind the menu bars.

Now, I noticed this problem before, at the office. We run linux-based thin clients (Athena) there, and some of us do have dual displays. They are completely useless because they have the same issue: 'fullscreen' means 'stretch' so they have to manually pull and push their windows (even while they are connected to a Windows 2008 terminal server/citrix session) to the right size to be able to use them effectively like a normal, local windows user would, just maximizing then on their display of choice.


Long story short: I'm out of options here. It seems to me dualscreen as I know (or knew) it, is just an impossibility on Linux. If you think otherwise, please give me some advice, lest my interesting Linux adventure not stop here.

---

### Post by markbuntu on 2009-10-27
There are many ways to get dual monitors working and some of them are quite easy but how to do it depends on the gpu and which driver it is using.

---

### Post by htt-thalan on 2009-10-27
Sorry, i forgot to mention that, yes. I'm using an Nvidia N9800GT 512mb with the supplied Ubuntu-built-in 'restricted' drivers. (i believe they are version 1.8x something).

---

### Post by htt-thalan on 2009-10-28
Anyone have any clue as to what I could try next?

---

### Post by markbuntu on 2009-10-28
I beleive you need to install nvidia-settings. There are a number of threads in this forum about setting up dual monitors with the nvidia driver. You should do a forum search.

---

### Post by htt-thalan on 2009-10-29
> **markbuntu said:**
> I beleive you need to install nvidia-settings. There are a number of threads in this forum about setting up dual monitors with the nvidia driver. You should do a forum search.

I don't wish to appear rude, but already I mentioned the fact that I'm using the drivers supplied by Ubuntu, which automatically come with the nvidia-settings window you say I should use. They give me the dualscreen setup I have now. 

The whole point is that Nvidia drivers are keeping the dualscreen config hidden from the X-Server. It appears to X as one big desktop doing 2920*1050. I need to find a way to make X understand he is dealing with 2 seperate screens, and stop it reporting this resolution to my games.

---

### Post by PokerJoker on 2009-10-31
> **htt-thalan said:**
> 
The whole point is that Nvidia drivers are keeping the dualscreen config hidden from the X-Server. It appears to X as one big desktop doing 2920*1050. I need to find a way to make X understand he is dealing with 2 seperate screens, and stop it reporting this resolution to my games.

First off, don't get why you wiped your vista install. It's so comfortable to have dual or even triple boot. Have xp/vista/ubu
as some apps in windows just need all the resources they can get and virtual just doesn't make sense. 

As to the dualheader problem. I've got an 8500GT and twinview worked like a charm prior to 9.04 on 2 1680 acers. 
For some reason, and i blame the prop nvidia drivers but can be wrong here, only the DVI connected monitor is recognized. 

Not much help for your problem i guess, just wanting to say that it CAN be done. 

9.10 beta's didn't even run on my machine, but i'm happy to see the upgrade to the 9.10 final is fine. 

Two more things. 
First: The nvidia-settings does make changes to the xorg.conf file. You need to run it as root, otherwise it can't write the changes to the file. There's another config file which is nvidia specific, it's in your user home dir called **.nvidia-settings-rc** (mind the . as part of the filename, meaning it's a hidden file, on cli type: ls -la to see those)

Second: As an it-consultant where the h*ll do you find the time to play WoW/CC3 etc anyway?   :o ;)



EDIT:
Played around some more and now have my setup working, dual screens @ 1680x1050 in Twinview mode, meaning metamode is 3360x1050. 
In Twinview there's only 1 X-screen, but if i run my firefox in full-screen (F11) mode it doesn't get strechted over two monitors (great option btw in FF with a auto-hiding bar, never knew that :-) Haven't got Unreal linux version but love to try it native if i could only find the time...
I'll give Wormus a try and see what it does. 

EDIT2: Intalls a bit slow Wormus and OpenArena, but other games do fine when i go F11 on them, only stretching into 1 screen. I'll post my settings:

xorg.conf:
> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Acer"
    ModelName      "AL2016W"
    HorizSync       31.0 - 84.0
    VertRefresh     56.0 - 77.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT: 1680x1050_60 +0+0, DFP: nvidia-auto-select +1680+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


.nvidia-settings-rc:
> #
# /home/alex/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Sat Oct 31 14:58:44 2009
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

0/CursorShadow=0
0/CursorShadowAlpha=64
0/CursorShadowRed=0
0/CursorShadowGreen=0
0/CursorShadowBlue=0
0/CursorShadowXOffset=4
0/CursorShadowYOffset=2
0/SyncToVBlank=0
0/LogAniso=0
0/FSAA=0
0/TextureSharpen=0
0/AllowFlipping=1
0/FSAAAppControlled=1
0/LogAnisoAppControlled=1
0/OpenGLImageSettings=1
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
0/DigitalVibrance[CRT-1]=0
0/DigitalVibrance[DFP-0]=0
0/XVideoTextureBrightness=0
0/XVideoTextureContrast=0
0/XVideoTextureHue=0
0/XVideoTextureSaturation=0
0/XVideoTextureSyncToVBlank=1
0/XVideoSyncToDisplay=2


---

### Post by htt-thalan on 2009-10-31
Thanks for an extended and useful post. I'm upgrading to 9.10 as we speak.

The reason I wiped Vista was because I wanted to take away the 'safe' fallback in case things didn't work out they way I expected. I had to push on to make this work. 

The metamode you speak of - that is exactly the case. Firefox, nautilis, they all maximize they way they should: on one screen only, but games like openarena and wormux span on 2 screens. 

My main screen is attacked via DVI and the second one via VGA, there is no other way as my GPU does not have 2 DVI ports - my previous card did, but that broke down, i got this one as a replacement.

You mention some 'other games' - which ones would that be? 
I'm having this problem with almost every game. I got CSS running on screen one by using native windowed mode, but Half Life 2 doesn't work that way. I'm working around this problem by disabling my second display in my nvidia-settings prior to playing an affected game. 

Maybe 9.10 will bring me some progress.

On a side note - HL2 runs choppy with DX9 enabled - forcing it down to 8.1 make it run like a charm, even with everything on full for as far as DX8.1 goes.

---

### Post by PokerJoker on 2009-10-31
> **htt-thalan said:**
> 
The reason I wiped Vista was because I wanted to take away the 'safe' fallback in case things didn't work out they way I expected. I had to push on to make this work. 

Resp3ct

> 
The metamode you speak of - that is exactly the case. Firefox, nautilis, they all maximize they way they should: on one screen only, but games like openarena and wormux span on 2 screens. 

My main screen is attacked via DVI and the second one via VGA, there is no other way as my GPU does not have 2 DVI ports - my previous card did, but that broke down, i got this one as a replacement.

Same here, 1 VGA & 1 DVI. the VGA gave me some problems as it wasn't recognized anymore in 9.04, where it was identified perfectly before.

> 
You mention some 'other games' - which ones would that be? 
I'm having this problem with almost every game. I got CSS running on screen one by using native windowed mode, but Half Life 2 doesn't work that way. I'm working around this problem by disabling my second display in my nvidia-settings prior to playing an affected game. 


It seems a bit strange your problem as some apps behave like they should. I've tried some of the standard installed games in Full screen mode. Only thing i haven't tested yet is on which screen come to think of it, all were F11'ed on the DVI sceen, should give them a wirl on the VGA one too.

EDIT:
Well, OpenArena is a bit of a pain. It starts in fullscreen mode right away, stretched to 3360x1050. Can't change the resolution in the setup. 
I can however change it in the settings file. It's under the hidden dir in the file: 

**/home/<you>/.openarena/baseoa/q3config.cfg**
> seta r_fullscreen "0"
seta r_customwidth "1680"
seta r_customheight "1050"

That does make it run in the mode you put there, tried 1024x768 also. 

Problem is, i can't get focus to get out of the game once it's opened, so no way to move the window around.

Also it's weird that if you lower the resolution in the config file, setup will still see it as 3360x1050.
Hope this helps.

---

### Post by htt-thalan on 2009-11-03
Yes i figured that out already. UT Classic native should accept the given resolution from it's ini file as well but keeps defaulting to a 2-screen span. OpenArena runs on the given reso if you force it via the config file, but as i recall it will run windowed then.

Maybe I should consider switching to a 1920*1200 DVI screen, 24, and just be done with this whole 2-screen mess.

I am considering going Kubuntu now, to see what KDE is like. I'm getting the taste of this :)

---

