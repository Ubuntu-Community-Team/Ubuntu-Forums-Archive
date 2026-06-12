---
title: "problem with playing videos in all players"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by vigener on 2007-10-20
Hi

I've been using Ubuntu 7.10 for two days and I can't find the source of 
the following problem: in all video players (totem, mplayer, vlc, xine)
when using xv instead of
desired effect I see bunch of multicoloured vertical lines on the whole width.
I have ati radeon x200m and xvinfo tells me that xv is turned on. When
I switch to x11, in mplayer for instance, everything is ok (except maybe the
fact that I can't switch to fullscreen mode).
Could someone tell me how to overcome this problem?

---

### Post by ceramicnuts on 2007-10-20
I have a similar problem with 7.10 and a Radeon Mobility X1400 vid card. I have a clean gutsy install and I enabled the proprietary fglrx driver.

mplayer will play movies but will result in tearing (a diagnoal streak is noticeable).
some movies the colors will be off. 

vlc appears to play them with proper colors but there is extreme stuttering of frames.

I installed all the codecs by going through totoem. I additionally installed the w32codecs from medibuntu.

---

### Post by Rstotland on 2007-10-20
Hey guys I seem to be having a related issue. Do not know why this is going on but in every player if I play .avi or other video files or .wma or .mp3 the video is screwed up. Even the visuals for th audio files do not come up. I have updated to 7.10 and have the latest driver for my nVidia card that was set up with xorg.

Here is a screen of what i get

[http://i233.photobucket.com/albums/ee214/rstotland/Screenshot-1.png]("http://i233.photobucket.com/albums/ee214/rstotland/Screenshot-1.png")

Everything was working fine in previous release.

Any ideas, anyone?

P.S. Sound works fine even when video is screwed up.

Thanks

---

### Post by thomas.hood on 2007-10-22
> **vigener said:**
> Hi

I've been using Ubuntu 7.10 for two days and I can't find the source of 
the following problem: in all video players (totem, mplayer, vlc, xine)
when using xv instead of
desired effect I see bunch of multicoloured vertical lines on the whole width.
I have ati radeon x200m and xvinfo tells me that xv is turned on. When
I switch to x11, in mplayer for instance, everything is ok (except maybe the
fact that I can't switch to fullscreen mode).
Could someone tell me how to overcome this problem?

I have the exact same card and problem...

Thomas Hood

---

### Post by raba1der on 2007-10-22
I have the same problem as seen on the screenshot linked above. However I got a Nvidia 7300SE card and I'm using the Restricted Nvidia drivers. Video works for a little while, then the screen blinks, and then video playback is garbled. It's then garbled in all players I've tested (totem and VLC) for the remainer of the X-session. If I Ctrl+Alt+Backspace to restart X it works again for a while. Anything from 2 minutes to working ok for a full length movie. (~2h)
This worked fine in Feisty. Upgraded to Gutsy ,got this issue, reinstalled, keeping the /home folder, got even worse, did a clean reinstall and issue is back as decribed above. Tried disabling/toggling between any effects-level in the System->Prefrences->Appearance->Visual effects. 

(I'm a linux-n00b, so please excuse me if any relevant info is missing. Please enlighten me and I'll try to provide anything that is needed)

My /etc/x11/xorg.conf file: 
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
    Option         "XkbLayout" "no"
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
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "S19-1"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "FUS S19-1"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:6:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 SE/7200 GS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "S19-1"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1280x1024_60 +1680+0, DFP: 1680x1050_60 +0+0; CRT: 1024x768 +1680+0, DFP: nvidia-auto-select +0+0; CRT: 832x624 +1680+0, DFP: nvidia-auto-select +0+0; CRT: 800x600 +1680+0, DFP: nvidia-auto-select +0+0; CRT: 640x480 +1680+0, DFP: nvidia-auto-select +0+0"
EndSection

---

### Post by coreyelledge on 2007-10-23
I encountered this problem today.  I changed the visual effects to none and video worked again in all players. The file was a .avi, and I also had green lines with audio still playing.  

I had visual effects set to custom using CCSM.  I would suggest turning them off and then adding them back one by one until you are back to your original settings.  Hope this helps.

---

### Post by victoitor on 2007-10-23
I have a dell laptop with a Radeon X1400 Mobility and the fglrx driver. If I play videos through totem, the colors are off. If I play them through vlc, the colors are ok but the video is very jumpy. I was playing .avi files.

---

### Post by audiored on 2007-10-23
I'm having the same problem.  In addition to the issues described above, I have to force quit the application.  This is the case with the movie player, Mplayer, VLC etc.  

I have the ATI Radeon X300 SE with the fglrx driver enabled.

---

### Post by DFreeze on 2007-10-23
Yup, same here (x200m ATI mobility). AVI files in totem show random colors, and with MPlayer or SMPlayer the video is too slow in fullscreen (MPlayer even crashes when I select Double Size or Fullscreen). In a smaller window the video can keep up...

I tried the "sudo aticonfig --overlay-type=Xv" fix in [some other thread]("http://ubuntuforums.org/showthread.php?t=513120&highlight=mplayer+fullscreen"), but now Compiz doesn't want to fire up. 

So two questions really: 
- how do I get videoplayback that's actually usable?
- how do I undo the command that caused Compiz to fail?

---

### Post by thomas.hood on 2007-10-23
There are multiple hardware/ software issues being conflated in this thread.

Re. the original post: it is a bug in the Xorg radeon sub-driver for xpress GPUs, confirmed by the driver's devloper, detailed here:[ https://bugs.freedesktop.org/show_bug.cgi?id=12744]("here: https://bugs.freedesktop.org/show_bug.cgi?id=12744")

People using the proprietary ATI fglrx driver/ nVidia cards have other issues.

Regards,

Thomas Hood

---

### Post by kernel1 on 2007-10-23
I have the same problem with ati radeon igp 300/330/350 (Compaq laptop)

I get black screen with sound with VLC Player when I open many videos that played with ubuntu 7.06

What I must do guys?

---

### Post by ragespot on 2007-10-23
> **coreyelledge said:**
> I encountered this problem today.  I changed the visual effects to none and video worked again in all players. The file was a .avi, and I also had green lines with audio still playing.  

I had visual effects set to custom using CCSM.  I would suggest turning them off and then adding them back one by one until you are back to your original settings.  Hope this helps.


with the special effects, you need to enable the GL video rendering, in totem, install gstreamer-gl package. in mplayer gui you can select it in the video output.  surely xine too

---

### Post by SwitchBlade on 2007-10-23
I've the same problem as described repeatedly.  IBM Z61m, with ATI Mobility Radeon x1400 using fglrx.

---

### Post by QwertyManiac on 2007-12-12
This happens for me on nvidia-glx-new (For an Nvidia GeForce 7600GT card). Weird no one else has nVidia and are experiencing this.

---

### Post by MaindotC on 2008-03-14
I'm experiencing a video problem which you can see in the attached picture.  The video plays off-centre, usually down a few inches from the top of the player (depending on the size of your screen).  If any humans are present, their skin is always blue ???

---

### Post by coskierken on 2008-03-14
For those with video playback problems.  I have experienced the same thing.  if you have XGL installed, it is no longer needed with the latest drivers.  I used Envy to install the latest ATI driver (next to latest) and things work smoother and faster.  The next problem is what was mentioned with the bug and special effects.  Just turn them off when playing videos.   A neat little program to run is called CompSwitch.  It lets you turn off the special effects by one click.  I got all my video problems to go away in all players by using Quickstart (look it up) and letting it install all the codecs needed and it uses Totem-Xine and not gstreamer.  My buddy and I figured it out one weekend and he wrote Quickstart which has an option to load all the files needed.  I hope this helps.

my systems has the ATI X1700 / Core 2 Duo T7200 Asus AJ8P laptop

---

### Post by kayel_justice on 2008-03-31
My problem is all video players crash. WHen I set CCSM to custom, they all crash. Is there a fix for this?  I have a vaio nr110-e with intel chip.

---

### Post by MaindotC on 2008-04-02
One thing I did to resolve my problem was in VLC, I modified some of the preferences.  Go to Edit -> Preferences -> Video -> Output Modules.  Click "Advanced Options".  Change Video Output Module to "X11 video output".  I can't really explain why this fixed it but I found it on another thread.

---

