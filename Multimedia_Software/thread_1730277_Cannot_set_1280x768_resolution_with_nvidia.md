---
title: "Cannot set 1280x768 resolution with nvidia"
date: 2011-04-15
forum: Multimedia Software
---

### Post by parthamage on 2011-04-15
All,

I am running Ubuntu 10.10 on an Asus 1201N eeePC.  Nvidia driver version 260.19.06.  I am attempting to run Dual monitors using a Dell W1700 with a native resolution of 1280x768.  No matter what I try, or which forum thread I look at, I cannot get this thing to offer me a choice of 1280x768.  I have gone through several evolutions of my xorg.conf; current one is attached.  I have also attached my nvidia bug report file.  I have tried creating a new resolution in xrandr using a very specific thread, and I keep getting syntax errors.  The really aggravating thing is that this thing works with no problems under Windows 7 (gag), and I refuse to let Windows win.  The native resolution on the Asus is 1366x768, so you would think that getting the second screen to run 1280x768 would be easy.  You'd be wrong.  I can currently choose between 1024 and 1360, but not 1280.  Please advise.

---

### Post by wolfen69 on 2011-04-15
Did you try **nvidia-settings**?

---

### Post by parthamage on 2011-04-15
That's where I started.  By messing around in the xorg.conf, I have gotten a few different combinations of resolutions to show up in the nvidia-settings, but never 1280x768.  If it had been that simple, I wouldn't be here.

---

### Post by oklokl on 2011-04-15
[COLOR=#666666][FONT=Arial]synaptic install
nvidia[COLOR=#FF0000]-185-kernel-source

[/COLOR][/FONT][/COLOR][COLOR=#666666][FONT=Arial]root c:# sudo nvidia-xconfig[/FONT][/COLOR]
booting..

[http://ubuntuforums.org/showthread.php?t=993652](http://ubuntuforums.org/showthread.php?t=993652)

[http://ubuntuforums.org/showthread.php?t=1725801](http://ubuntuforums.org/showthread.php?t=1725801)

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by parthamage on 2011-04-15
The 185 install just set both at 800x600, and then fracked up my mouse to the point I was about to throw it through the window.  I have my screens back to where I was, but still no choice of 1280x768 in nvidia-settings.  

Next contestant?

---

### Post by BicyclerBoy on 2011-04-15
I don't know the nvidia bug report format & there are multiple Xorg.0.log files contained in it & I'm not opening a .doc file.

Looking at your /var/log/Xorg.0.log file.. you are causing the problem with your use of horizontal & vertical freq limits..e**dit maybe**

The placement of these is affecting both displays.
The value of these is causing video modes to be in-validated..
AFAIK The video mode 1366x768 is not a recognised internal defined mode..1360x768 is ..
So there is no definition of 1366x768 for the meta mode (twinview) so the driver rejects them

Your telling the X server to use EDIDFreqs but the monitor EDID is not valid/readable on wired port CRT-0

Your telling X server you have CRT-0 & DVI/DFP-0 connected but you don't... You have LVDS & CRT-0..**edit**;
[B]your DFP-0 is LVDS..this is okay
[/B] 
You should backup/delete your xorg.conf, reboot, run nvidia-xconfig..
Then repost your
/var/log/Xorg.0.log file    as .txt attachment.

To use 1366x768 mode you may need to make a custom modeline or modes section in xorg.conf.

The version of nvidia driver was not very good...best to use 260.19.36 or later..
Couple of ppa
Ubuntu nvidia x-swat team  (they have link to more recent ppa)

---

### Post by parthamage on 2011-04-16
So, all the other posts I've read tell me I have to have H&V freqs, and you're telling me they are part of the problem.  If that's the case, where should I remove them?

I know it's not reading EDID; don't know how to tell it to look somewhere else, and then specify there what I want.  Can help there?

I have no idea where I'm "telling X server you have CRT-0 & DVI/DFP-0 connected".  Again, if you can show me where to fix it, I'm all ears.

I deleted xorg.conf; rebooted, ran nvidia-xconfig, and guess what?  I got the same, exact, wrong resolutions.

Where are you finding a driver numbered 260.19.36?  Both the driver tool itself and synaptic are telling me that this is the most up to date version there is; I don't have a way of getting anything more current.  There is a 185.18.36, but the only 260 version I see is the one I'm running.

Thanks for the effort; I appreciate it, even if it doesn't sound like it.  This is just kind of frustrating.  Everybody wants to take me a different direction down the rabbit hole, and so far, they are all leading me to the same wrong place.  And this really should be easier than it is.  There is no excuse for not having something as basic as screen resolution aced by now.

---

### Post by BicyclerBoy on 2011-04-16
Please check the edited bits in the previous post..

If you get the same result with no xorg.conf (& you do) then your xorg.conf entries are not making it fail (1366).

The heart of the problem is the corrupt/unreadable EDID..
So then you need to have H & V freqs listed, for monitors without EDID, so the driver can validate the video modes.
I did say the limits ...try
    HorizSync       24.0 - 80.0
    VertRefresh     49.0 - 75.0
This covers the wide selection video modes VGA to HD1080.

You can use keywords in the approp. screen section
    Option         "UseEDID" "FALSE"
    Option         "UseDisplayDevice" "CRT-0"

The EDID problem could be caused by monitor/cable/videocard/driver/kernel bugs..
There was a big jump in EDID problems several months ago.
The driver version you are using has not proven to be that good.
So the suggestion was to use later 260 or 270 from another ppa.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=maverick]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates?field.series_filter=maverick")

**But your video mode problem** seems to be the video mode 1366x768 is not recognised. Maybe the new driver does not support it..try
1360x768  or 1368x768     (all multiples of eight (8.))

If these work then you can try a custom modeline for 1366x768..but..
(modeline calc CVT rejects this mode for 1368x768..

I have a vague idea the ION chipset has some video mode/vdpau restrictions...


Can you try disable twinview & then see if the internal panel can be set to 1366x768 automatically ?
What do you get on internal panel ?

---

### Post by parthamage on 2011-04-16
1366x768 is not a problem; I'm getting that on the laptop just fine.  The problem is getting 1280x768 on the Dell external (which is its native res).

---

### Post by parthamage on 2011-04-16
Updated driver from ppa you suggested.  Re-booted, and it works like a charm.  Many thanks!:KS

---

### Post by BicyclerBoy on 2011-04-16
Mental  isn't it...no wonder everyone has grief..

I was just making you a new xorg.conf  file...
You don't need it but this is how I think it should be arranged. (best guess)

---

### Post by parthamage on 2011-04-17
Thanks, BicyclerBoy; have downloaded the xorg.conf in case I need it in the future.  I guess this is the trade-off we make when we choose freedom from MS/Apple.  Glad these forums are here!

---

### Post by parthamage on 2011-04-17
And the problem is back, even though I have the new drivers loaded.  (Sigh).  Loaded your xorg.conf; no help.

---

### Post by BicyclerBoy on 2011-04-18
Can you post your
/var/log/Xorg.0.log   file as an attachment with .txt extension..

Maybe the nvidia driver is not loading after reboot cycle..

Your error report seems to suggest 64bit..
How have you got x86_64 kernel running on a 32bit only atom 330 CPU ??

To clarify
From wikipedia the N2xx and Z5xx series only can not run 64 bit..so desktop 270 & 330 are x86_64 capable.

---

### Post by parthamage on 2011-04-23
Here is the log file.

Have been running the 64 bit, as the 1201N is able to take up to 8 gigs of RAM, it never occurred to me that it might be limited to 32-bit.

Thanks for the help!

---

### Post by parthamage on 2011-04-29
UPDATE:

I updated my OS to 11.04.  First reboot, the system detected the second monitor correctly and worked perfectly.  After shutdown and restart, it lost the correct resolution again.  That is the second time that the second reboot after an update has broken a fix.  WTF?

---

