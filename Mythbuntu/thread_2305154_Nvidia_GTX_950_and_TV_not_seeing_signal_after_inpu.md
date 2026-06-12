---
title: "Nvidia GTX 950 and TV not seeing signal after input change or power off/on"
date: 2015-12-03
forum: Mythbuntu
---

### Post by wpcprez on 2015-12-03
Hello All,
I am having the same issue I had before on my older GT240 card and the Option "UseHotplugEvents" "False" is properly set but it's not working on this card for some reason. Anyone with a GTX 950 / 960 with the same issue have a solution? I can't keep restarting lightdm via a laptop every time I want to turn on the TV. 

Here's the other thread for reference. Which did work on my GT240

[http://ubuntuforums.org/showthread.php?t=2257014&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=2257014&highlight=nvidia)

---

### Post by blm-ubunet on 2015-12-03
Your trusty GT240 is/was using the legacy driver. The shiny new GTX950 (HEVC 4K60p hdmi2.0) uses the latest..

FWIHR you can work-around by capturing the EDID (in nvidia-settings) & saving to file. Then reference this EDID.bin file in your /etc/X11/xorg.conf

Option "CustomEDID" "string"
[http://us.download.nvidia.com/XFree86/Linux-x86/358.16/README/xconfigoptions.html](http://us.download.nvidia.com/XFree86/Linux-x86/358.16/README/xconfigoptions.html)

This option could be better:-
Option "ConnectedMonitor" "string"
(Powered off HDMI displays can't be detected.)

Weaker option prob not work:
Option "UseDisplayDevice" "string"


Option "ModeValidation" "NoEdidHDMI2Check"
looks very useful for 4:4:4 output.

Option "AllowEmptyInitialConfiguration" "boolean"
Allow Xserver to start with no connected or powered off displays

DVI & VGA don't have this problem because their DDC I2C bus is powered from video card.

---

### Post by wpcprez on 2015-12-04
oh, so I wonder if I use a DVI > HDMI cable then I wouldn't have to change anything? Thanks for all that great info


also, how did you know I got a 4k@60p TV?

---

### Post by blm-ubunet on 2015-12-04
I do now! .. 
Because any HTPC user with GTX950 must have 4K & a need for HEVC.
And the only good TVs on the market now are 4K.

The DVI-HDMI cable is exactly same (electrically) as single link DVi or HDMI cable so makes no difference.

AFAIK The hdmi interface is designed to be dynamic hot-plugged/event driven. No need for EDID from devices powered off.

---

### Post by wpcprez on 2015-12-05
hmm, I can't seem to get this to work. Also, since this is HDMI 2.0 would the DVI cable work right? 

These are all the things in my xorg.conf

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "CustomEDID"    "DFP-1:/etc/X11/edid.bin"
        Option  "UseDisplayDevice"      "DFP-1"
        Option  "DPI"   "100x100"
        Option  "NoLogo"        "1"
        Option  "UseHotplugEvents"      "false"
        Option  "ModeValidation" "NoEdidHDMI2Check"
        Option  "AllowEmptyInitialConfiguration" "true"

but it still doesn't seem to wake up without restarting lightdm

---

### Post by blm-ubunet on 2015-12-05
It is possible the DVI port does not behave exactly stuff as hdmi port because of an intentional difference.

The contents of /var/log/Xorg.0.log might reveal stuff..
The tail end of "dmesg" output should have any hdmi events (HDA ELD etc)..

The driver is possibly ignoring your EDID or need to use "Connected Monitor"..


There are reports (mythtv mailing lists) that driver version 352 solves this problem without having to resorts to EDID or connected monitor hacks..

---

### Post by wpcprez on 2015-12-07
Hello,
I had to upgrade to 352.63 in order to use this card. It seems like the TV is trying to turn on and it's unable to. It says this 4 times in a row then the TV says no signal. Which makes me think it might be some sort of HDMI 2.0/HDCP thing 


[ 14744.811] (--) NVIDIA(GPU-0): LLL PRK65A65RQ (DFP-1): connected
[ 14744.813] (--) NVIDIA(GPU-0): LLL PRK65A65RQ (DFP-1): Internal TMDS
[ 14744.813] (--) NVIDIA(GPU-0): LLL PRK65A65RQ (DFP-1): 600.0 MHz maximum pixel clock
[ 14744.813] (--) NVIDIA(GPU-0):

. I have tried with/without connectedmonitor and usedisplaydevice and various combinations. None seem to work. For now I have power set to restart lightdm as a workaround.

---

### Post by wpcprez on 2016-01-02
fyi - this looks related to this if anyone else is having this issue.


[https://devtalk.nvidia.com/default/topic/776251/343-22-gtx-970-980-support-hdmi-2-0-/?offset=23](https://devtalk.nvidia.com/default/topic/776251/343-22-gtx-970-980-support-hdmi-2-0-/?offset=23)

something with HDCP and/or driver at 4k@60hz

---

### Post by one30nav on 2016-01-12
After upgrading my system with an ASUS GT 730 card with the latest Nvidia driver, I've had the same issue. What fixed it for me was revisiting the workaround that Mario Limonciello (superm1) originally recommended, particularly his script: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105)

fkervin did a really nice job running this to ground in this link:  [https://forum.xfce.org/viewtopic.php?id=9391](https://forum.xfce.org/viewtopic.php?id=9391)

So, fkervin's script looks like this and it works to reset my TV when you invoke manually via ssh or irexec.  Next step is to (hopefully) make this work in a udev:

> #!/bin/sh
#Fix TV state when HDMI link is lost.
#By Mario Limonciello <email address hidden>
sleep 10
OUTPUT="HDMI-0"
BAD_MODE="1280x720"
GOOD_MODE="1920x1080"

 for MODE in $BAD_MODE $GOOD_MODE; do
 DISPLAY=:0 xrandr --output $OUTPUT --mode $MODE
 sleep 2
done

---

### Post by one30nav on 2016-01-12
Oh, well. The script works, but no luck getting my udev to work. I may have to revert back to xfce-settings 4.11.0 and lock it.

---

### Post by wpcprez on 2016-01-12
> **one30nav said:**
> After upgrading my system with an ASUS GT 730 card with the latest Nvidia driver, I've had the same issue. What fixed it for me was revisiting the workaround that Mario Limonciello (superm1) originally recommended, particularly his script: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105)

fkervin did a really nice job running this to ground in this link:  [https://forum.xfce.org/viewtopic.php?id=9391](https://forum.xfce.org/viewtopic.php?id=9391)

So, fkervin's script looks like this and it works to reset my TV when you invoke manually via ssh or irexec.  Next step is to (hopefully) make this work in a udev:


thanks, that works as well as a restart of lightdm. That script changes resolution to something else then back to the good resolution. I still think this is some how tied into the nvidia driver. A udevadm monitor doesn't show any changes when the TV is turned on/off. fkervin does show udev things happening when he turns off his monitor. 

Do you show events happening when you turn on/off your monitor from "udevadm monitor"?

---

### Post by one30nav on 2016-01-13
Very frustrating. I agree that it's tied to the Nvidia driver. My Xorg.0.log file shows the monitor disconnecting. When I run udevadm monitor via ssh, it does not show a reconnect event when I plug the HDMI cable back into the TV.

---

### Post by wpcprez on 2016-01-13
That's the same issue I'm having. 

I was considering switching from XFCE but afraid it would cause issues being too far away from the base when we need to upgrade to the new release of mythtv 0.28. I believe it's scheduled to be out in 3 weeks.

---

### Post by one30nav on 2016-01-13
Makes sense and my thoughts exactly. To that point, I may just map a remote key via irexec to one of the various reset scripts and wait it out. I'll post here if I find another way or hopefully the forum will likewise?

---

### Post by wpcprez on 2016-01-13
that's what I do.


begin
    remote = mceusb
    prog = irexec
    button = KEY_POWER
    config = /usr/bin/fixhdmi.sh &
    repeat = 0
    delay = 0
end

---

### Post by one30nav on 2016-01-13
Perfect

---

### Post by one30nav on 2016-01-21
Fixed by downgrading xfce4-settings:  Greg Fordyce in post #104 in the following link, provided a quick way to revert back to xfce4-settings 4.11.0-1 (It's mentioned in other posts that 4.11.3 broke things):

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105)

I downloaded and installed the package via the link then locked it in both Synaptic and Apt.  Locking packages in Synaptic is straightforward. For Apt, I did:
 
```
sudo apt-mark hold xfce4-settings
```

Everything works fine now.

I use Mythbuntu 14.04 (Mythtv 0.27) / GeForce GT 730 / Nvidia 352.63 driver.

---

### Post by wpcprez on 2016-02-16
> **one30nav said:**
> Fixed by downgrading xfce4-settings:  Greg Fordyce in post #104 in the following link, provided a quick way to revert back to xfce4-settings 4.11.0-1 (It's mentioned in other posts that 4.11.3 broke things):

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1308105)

I downloaded and installed the package via the link then locked it in both Synaptic and Apt.  Locking packages in Synaptic is straightforward. For Apt, I did:
 
```
sudo apt-mark hold xfce4-settings
```

Everything works fine now.

I use Mythbuntu 14.04 (Mythtv 0.27) / GeForce GT 730 / Nvidia 352.63 driver.


I didn't see this for some reason. I'll try this tonight and see what happens.

---

### Post by wpcprez on 2016-02-17
> **wpcprez said:**
> I didn't see this for some reason. I'll try this tonight and see what happens.


nope this did not work for me. I still think this is some how related to the HDCP functions in the driver causing some wonkyness.

---

