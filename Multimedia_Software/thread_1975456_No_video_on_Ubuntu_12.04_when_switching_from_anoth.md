---
title: "No video on Ubuntu 12.04 when switching from another HDMI device"
date: 2012-05-07
forum: Multimedia Software
---

### Post by ekimseekem on 2012-05-07
I think I have a common video issue that I've seen before, can't remember how to fix it. Currently I have a few HDMI devices (PS3, 360) and a HTPC running Ubuntu. I have a Denon receiver doing the switching between all the devices. The issue I have is, whenever I switch from another device to the Ubuntu box or even turn the TV off/on, the screen is black with no video, with no way to get it back without hard rebooting. I currently have a NVIDIA GeForce GT 430 and the HTPC is connects via HDMI as well. I also have up-to-date drivers.

I see a lot of problems with HDMI audio, but very little on this kind of video issue.

Anyone had similar problems?

---

### Post by BicyclerBoy on 2012-05-07
Some of the better HT amps have EDID/ELD management that allows caching etc..

Failing that there are 2 option keywords for /etc/X11/xorg.conf file:

Option "UseDisplayDevice" "DFP-0"

or more heavy handed option (& probably required)

Option "ConnectedMonitor" "DFP"

Notes:
see appendix B. "X config Options" of the nVidia driver readme.
The /etc/X11/xorg.conf file is absent by default..
nvidia-xconfig can generate it.
Check your /var/log/Xorg.0.log for the exact display device port labels i.e. your HDMI TV could be "DFP-1"

---

### Post by ekimseekem on 2012-05-07
Writing out the xorg.conf file and adding the latter option didn't seem to work, here is my conf file:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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
    ModelName      "DENON, Ltd. DENON-AVAMP"
    HorizSync       31.0 - 82.0
    VertRefresh     57.0 - 63.0
    Option         "DPMS"
    Option         "ConnectedMonitor" "DFP-1"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 430"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "nvidia-auto-select +0+0; 1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

I can still shell into the box even though video is borked (post testing).  So it seems to me that its not picking up the monitor after switching.

---

### Post by ekimseekem on 2012-05-08
> **BicyclerBoy said:**
> Some of the better HT amps have EDID/ELD management that allows caching etc..

I don't think my amp has that feature... can't be sure, as the manual for it is crap.  Its a Denon AVR-790.

I should also add that this setup works on Windows 7, no issue with switching between HDMI devices.  I really want to switch to Linux, but so far I'm getting more disadvantages...

---

### Post by BicyclerBoy on 2012-05-08
The nVidia driver readme is very vague about the correct location of any options..It may parse the whole file anyway..

The options 
Option "ConnectedMonitor" "DFP"
Option "UseDisplayDevice" "DFP-1"
should probably be in "ServerFlags" or Device or screen section. 

I think I have these in screen section.

Check & post your /var/log/Xorg.0.log file (as attachment)..

I have a suspicion one or both these keywords are to be removed from the latest driver version 301..

---

### Post by ekimseekem on 2012-05-11
Well I ended up taking an easy road out and switched to Mythbuntu.  I was expecting the same issue to rear its head since it still relies on the same graphics drivers and Xorg config, but it works without issue, I didn't have to touch Nvidia settings either.

I'm going to hypothesize that it maybe due to an element that's new to Ubuntu 12.04 (or earlier) and that's Unity.  Is it possible that it may not be reloading the screen after the HDMI connection is detected again?

---

### Post by BicyclerBoy on 2012-05-11
That seems like a plausible root cause..

Something similar...
Unity/compiz does not automatically work with secondary X screens, & it needs to be forced to draw the desktop interface with something like this:
DISPLAY=:0.1 compiz
or
DISPLAY=:0.1 unity

Was your blank screen completely off or just blank ? Did the mouse cursor show up?

---

### Post by ekimseekem on 2012-05-11
> **BicyclerBoy said:**
> That seems like a plausible root cause..

Something similar...
Unity/compiz does not automatically work with secondary X screens, & it needs to be forced to draw the desktop interface with something like this:
DISPLAY=:0.1 compiz
or
DISPLAY=:0.1 unity

Was your blank screen completely off or just blank ? Did the mouse cursor show up?

No didn't see a cursor and it did look like the screen was completely off.

---

### Post by Du5t1n55 on 2012-05-14
I too have this issue.  However, i have found a work around of restarting Xorg every time I want to use my Media PC.  The only monitor that I have connected to this particular box is my HDTV.  I also have an NVIDIA 410 or something like that in it. 

sudo killall Xorg 

The interesting thing is that I also have a Denon Receiver.  I have not had time to do much research as of yet but if anyone does have an answer it would be greatly appreciated.

---

### Post by ekimseekem on 2012-05-15
> **Du5t1n55 said:**
> I too have this issue.  However, i have found a work around of restarting Xorg every time I want to use my Media PC.  The only monitor that I have connected to this particular box is my HDTV.  I also have an NVIDIA 410 or something like that in it. 

sudo killall Xorg 

The interesting thing is that I also have a Denon Receiver.  I have not had time to do much research as of yet but if anyone does have an answer it would be greatly appreciated.

I take it you just shelled into the machine from somewhere else and executed that command, or you had a hotkey setup for it...?

I should expand a bit on where I've seen this issue before.  Before the Nvidia card I have now, I used to have an ATI Radeon HD 5xxx card in the HTPC, during certain driver updates even for Windows, the screen would exhibit similar behavior (though at the time I attributed it to overheating as the card had a crappy heatsink/fan on it).  I switched to the Nvidia card as I was told the drivers are usually better, and they were correct, no issue at all from then on, until I tried Linux Mint 12, which had the same problems I've been seeing now.  I switched back to Windows and the issue went away.

Trying out Ubuntu brought back the video issue and switching to Mythbuntu solved it (clean install mind you).  I have some minor issues with Mythbuntu, like not being able to use an external player* (smplayer or VLC) and having to deal with no audio normalization** when using the internal player, but it works good otherwise.

*I know how to set it up, but for some reason the external player will just open then quickly close when trying to play an AVI, but appears to work just fine when trying to play an mkv or something else.  I'd like to use the external player in order to have options for audio normalization

**I want audio normalization because I only have 2 speakers (L and R), as such, when playing 5.1 sound, music and sound effects are usually blaring and voice is very soft

---

### Post by jae18708 on 2012-05-15
I am having the same problem with the hdmi on my laptop. It works perfectly on the live cd and fresh install, but something gets updated and I lose the all video on my Sceptre LED TV. The screen is just blank, no cursor or anything. HDMI still works fine on TV downstair.

I'm wondering if its really emabled and sending the correct settings to the Sceptre TV.

---

### Post by SeanOB on 2012-05-20
Nothing to offer here.. just subscribing to the thread.
I have the same issue with a Denon 2809.
Its worked fine with my hardware setup for many many many ubuntu releases until today with 12.04.

---

### Post by derekcentrico on 2012-05-21
Same boat.  I have an Oknyo receiver.  If I plug the HDMI directly into my LCD I receive video and audio from Ubuntu.  If it is plugged into the AVR I only receive audio.

---

### Post by SeanOB on 2012-05-31
Problem is resolved by switching to mythbuntu.
And since this machine is a set-top-box that works for me.

And VDPAU video performance is better with mythbuntu now too -- no more tearing.

The downside?  No more slick unity interface..  but I'd rather have working video and be able to switch between my hdmi inputs than have a slick interface.

-SeanOB

---

### Post by ekimseekem on 2012-05-31
> **SeanOB said:**
> Problem is resolved by switching to mythbuntu.
And since this machine is a set-top-box that works for me.

And VDPAU video performance is better with mythbuntu now too -- no more tearing.

The downside?  No more slick unity interface..  but I'd rather have working video and be able to switch between my hdmi inputs than have a slick interface.

-SeanOB

Yea, I ended up switching to mythbuntu... worked very well and the video switching went away.

However, my machine has started overheating and I'm going to have to look for a new CPU cooler now... (already tried reseating the CPU heatsink with new thermal paste)

I like Ubuntu 12.04, seems to be a good improvement, I may switch to it in place of Linux Mint thats on my workstation currently.

---

### Post by robbyf on 2012-05-31
I'm having very similar problems
 
Ubuntu 12.04 LTS
Nvidia 460 GTX
 
HDMI out to Onkyo 609
 
I get bios screen, grub screen and then nothing. I can Ctrl+alt+F1 to console and get a display.
 
I can dual boot into windows 7 and get things to work fine, so it's clearly not a hardware problem.
 
I'm subscribing to this thread as well so if someone finds an answer please share, I've spent hours and hours googling.

---

### Post by ekimseekem on 2012-05-31
> **robbyf said:**
> I'm having very similar problems
 
Ubuntu 12.04 LTS
Nvidia 460 GTX
 
HDMI out to Onkyo 609
 
I get bios screen, grub screen and then nothing. I can Ctrl+alt+F1 to console and get a display.
 
I can dual boot into windows 7 and get things to work fine, so it's clearly not a hardware problem.
 
I'm subscribing to this thread as well so if someone finds an answer please share, I've spent hours and hours googling.

I was at the very least able to get to the desktop after a boot up... but as if it were a carnival only the first one was free, after switching from another HDMI device did it just give me a black screen, and no way to get to a console or anything short of ssh'ing into the machine.

I'm still thinking my issue was with Unity not redrawing the screen when switching back to the HTPC.  I think you're issue might be a missing or broken xorg.conf file?

---

### Post by robbyf on 2012-05-31
well I am making progress,
I booted an older kernel 2.6.XX and it booted into ubuntu 12.04 64 bit with graphics, how ever nvidia drivers are not running. So its a kernel issue or a driver issue my AVR is HDCP compliant as well.
Unity running
resolution was 800x600


going to test beta drivers 302.07 - there should be updated EDID

no such luck

---

### Post by loken1 on 2012-06-13
I have the same issue. The 302.07 beta fixed it, but then there is no sound on HDMI, as this thread describes:
[http://www.nvnews.net/vbulletin/showthread.php?t=180050](http://www.nvnews.net/vbulletin/showthread.php?t=180050)

Apparently 302.11 didn't have sound either, but nvidia is promising to fix it in next update.

I have rolled back to 295.49 while waiting for next nvidia update.. In the mean time, when I am switching HDMI back to HTPC, I connect with VNC from my laptop and logout. This brings back the picture on my TV. With a decent SSD this procedure takes just few seconds, but it's still a hassle..

---

### Post by loken1 on 2012-06-23
> **loken1 said:**
> I have the same issue. The 302.07 beta fixed it, but then there is no sound on HDMI, as this thread describes:
[http://www.nvnews.net/vbulletin/showthread.php?t=180050](http://www.nvnews.net/vbulletin/showthread.php?t=180050)

Apparently 302.11 didn't have sound either, but nvidia is promising to fix it in next update.

I have rolled back to 295.49 while waiting for next nvidia update.. In the mean time, when I am switching HDMI back to HTPC, I connect with VNC from my laptop and logout. This brings back the picture on my TV. With a decent SSD this procedure takes just few seconds, but it's still a hassle..

With driver version 302.17 everything works perfectly :p

---

