---
title: "HDMI Display not enabled when booting with TV powered off"
date: 2015-01-22
forum: Mythbuntu
---

### Post by tylersontag on 2015-01-22
I recently switched from routing my HTPC to my TV via VGA to using an HDMI out and I've found an issue i'm not pleased with.

I store a large amount of my media on an external sata enclosure running a 3 drive RAID5 vdrive.  Occasionally, i'll see RAID failures and need to bounce the system.  Since I access this content remotely I occasionally need to bounce the server remotely.  I had a system in place where I could bounce and bring back up the whole system via a my phone and a VNC client, and this worked pretty well for emergencies.

However, since switching to using HDMI I've noticed an issue that breaks my process.  If my TV is powered down, as it would be if im not at home and bouncing the server remotely, when the server reboots, it won't recognize any active video out and it boots into some kind of non-graphical mode.   I can't VNC into the machine, when I return home and turn on the TV theres no output coming out of my video card's HDMI port and I end up having to SSH into the machine and reboot it.

Is there anyway to force my machine to always treat the HDMI port as though it were active, on reboot?

---

### Post by khPWXxF on 2015-01-22
Nvidia graphics?

See this:
[http://ubuntuforums.org/showthread.php?t=2257014](http://ubuntuforums.org/showthread.php?t=2257014)

Once fixed, make sure you make /etc/X11/xorg.conf immutable.
hth
Phil

---

### Post by tylersontag on 2015-01-23
Thanks for the advice!  I'd seen that thread but didn't really know if my issue was the same (the OP described the screen going off having once been working, when turning off the screen.  Whereas, I can power down my TV provided the system was already up and running, my only issue is when trying to reboot with the TV off)

I followed the instructions on that thread anyway and updated my Device section to look like the following 

```
Section "Device"
  Identifier "Device0"
  Driver "NVidia"
  VendorName "NVIDIA Corporation"
  BoardName "Geforce GT 430"
**  Option "UseHotplugEvents" "False"**
EndSection
```

After doing so, I rebooted my machine with the screen off and got the same behavior :-/

---

### Post by Lester_Burnham on 2015-01-23
Hi,

I'm not sure if you can still do this with Nvidia but, you used to be able to save the edid.bin from nvidia-settings to a location and use that file to set the resolution.
I was using it on an old Samsung TV 5+ years ago

If you run this command below or go to nvidia settings you will see which device to use. Mine is DFP-1. If you click on it in the left pane, you will also see aquire EDID in the bottom right corner. I saved this to /etc/X11/edid.bin (you can use a more descriptive name)
```
cat /var/log/Xorg.0.log | grep DFP
```

> Done building ModePool for TOSHIBA-TV (DFP-1)
Mine shows up as DFP-1

My old xorg.conf looked like this
```
Section "Device"

  # Option         "UseEDID" "False"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
    Option         "ConnectedMonitor" "DFP-1"
    Option         "CustomEDID" "DFP-1:/etc/X11/edid.bin"
EndSection
```

There are other xorg.conf options to try first before arriving here though. Like maybe not using the EDID, that you can see is commented out above and instead, setting the resolution in nvidia settings and saving it to xorg.conf
UseHotplugEvents as Phil mentioned earlier.
Don't forget to back up your xorg.conf each time if required.

You might even find some pointers here [http://wiki.openelec.tv/index.php?title=Config_EDID_nvidia](http://wiki.openelec.tv/index.php?title=Config_EDID_nvidia)

Lester

---

### Post by khPWXxF on 2015-01-24
That's right - the problem is that TV gives blank screen if switched on after your myth box.

Is it fixed if you try UseHotPlugEvents not UseHotplugEvents  (upper case P) and false not False (lower case f).

Phil

---

### Post by Lester_Burnham on 2015-01-24
Hi Phil,

What section does this option (UseHotplugEvents) go in?
The last post I read, said in the monitor section. Does it matter?
Referring to this post below (he said it worked!)
[http://ubuntuforums.org/showthread.php?t=2136911](http://ubuntuforums.org/showthread.php?t=2136911)

This looks to be correct
Option "UseHotplugEvents" "False"

Lester

---

### Post by khPWXxF on 2015-01-25
Hi Lester,

I put it in the devices section.  My whole xorg.conf is shown below, but you’ll have seen from other postings that I’m no expert.  I just repeat the words of others!
 
As an aside, I’ve been wondering whether we need a general wiki page about picture problems.  Xfce bar at top, screen resolution, legacy nvidia graphics, this issue etc. Views?
 
Phil
 
> # xorg.conf is immutable and is protected from deletion by 'sudo chattr +i xorg.conf'
#  use 'sudo chattr -i xorg.conf' if you need to edit or remove it
#  use 'sudo lsattr xorg.conf' to list attributes


# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 304.117  (buildmeister@swio-display-x86-rhel47-01)  Tue Nov 26 22:29:40 PST 2013

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option         "UseHotPlugEvents"   "false"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by Lester_Burnham on 2015-01-25
> **khPWXxF said:**
> Hi Lester,

I put it in the devices section.  My whole xorg.conf is shown below, but you&#8217;ll have seen from other postings that I&#8217;m no expert.  I just repeat the words of others!

LOL... I'm no different. Read, trial, error, read again.
I've learnt from you also...
 
> **khPWXxF said:**
> 
As an aside, I&#8217;ve been wondering whether we need a general wiki page about picture problems.  Xfce bar at top, screen resolution, legacy nvidia graphics, this issue etc. Views?
 
It would be a good idea in logical steps. I've tried using the screen wizard in mythbuntu, but have never had an acceptable picture afterwards. Panning starts to rear it's head in XBMC etc. I know TGM and co put a lot of work into these things for us, but its been just a bandaid fix for me really. You just can't beat HDMI without overscan, but it can be hard on older TVs to get there. New technology should help.

I used to dread dealing with Mr Xorg, but these days I'm more comfortable, as things have come a long way in a few years.

Lester

Finally found the list of Nvidia options [http://us.download.nvidia.com/XFree86/Linux-x86/310.44/README/xconfigoptions.html](http://us.download.nvidia.com/XFree86/Linux-x86/310.44/README/xconfigoptions.html)

---

### Post by khPWXxF on 2015-01-25
[COLOR=#000000]Quite right - this does look to be correct[/COLOR]
[COLOR=#000000]Option "UseHotplugEvents" "False"

That's an interesting xorg parameters page - not seen it before - thanks.
Phil

[/COLOR]

---

### Post by tylersontag on 2015-02-28
my display is managed by lighdm, not Xorg, so i had trouble generating an EDID (Kept saying zero found)

I've tried upper and lower case on the UseHotPlugEvents and get the same behavior.   This issue is still ongoing :?

---

### Post by khPWXxF on 2015-03-23
Anything helpful here?
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105)
Phil

---

### Post by mathog on 2015-04-06
Look down at the bottom of this thread:

[http://www.nvnews.net/vbulletin/archive/index.php/t-129966.html](http://www.nvnews.net/vbulletin/archive/index.php/t-129966.html)

I had a similar issue getting the myth box to come up with output on
when any combination of the two output devices might not be attached
at boot time.  

That was over 6 years ago, so don't be surprised if the needed syntax in xorg.conf has changed.

---

