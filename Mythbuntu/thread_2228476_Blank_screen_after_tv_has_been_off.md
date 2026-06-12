---
title: "Blank screen after tv has been off"
date: 2014-06-07
forum: Mythbuntu
---

### Post by itlarson2 on 2014-06-07
I have a problem with my system where anytime I turn the TV off. I get a blank screen when I turn it back on.  I can use ctrl+alt+F1 to get a terminal, then restart lightdm, and the system will be back to normal, at least until I turn the TV off again.

This seems to be more or less the same problem described in [this post]("http://ubuntuforums.org/showthread.php?t=2220583"), but the solution described doesn't work for me- probably because I don't understand it well enough.  The only change has been I now need to do "sudo lightdm stop" and "sudo lightdm start" instead of just "sudo lightdm restart".  Here are my files from my attempted fix: 

```
cat  /etc/udev/rules.d/hdmi.rules
KERNEL=="card0", SUBSYSTEM=="drm", ACTION=="change", RUN+="/home/itl/config/fix.sh"

$ cat  /home/itl/config/fix.sh
#!/bin/bash
export XAUTHORITY="/home/itl/.Xauthority"
export DISPLAY=":0.0"
xrandr --output HDMI-0 --mode "1280x720"

```

The xrandr line works properly when the system is functioning normally, but not when the problem is in effect. Then it gives a "Failed to use bus name" error.  I have also had similar results from  nvidia-settings when the system is in this state.  I wonder if it would be worth trying a LXDE install?  It seems like this is a bug in Xfce.

Here's some info on my graphics:

```
$ xrandr --verbose
Screen 0: minimum 8 x 8, current 1280 x 720, maximum 16384 x 16384
DVI-I-0 disconnected primary (normal left inverted right x axis y axis)
    Identifier: 0x27c
    Timestamp:  454764
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: VGA 
        supported: VGA
    ConnectorType: DVI-I 
    ConnectorNumber: 0 
    _ConnectorLocation: 0 
VGA-0 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x27d
    Timestamp:  454764
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: VGA 
        supported: VGA
    ConnectorType: VGA 
    ConnectorNumber: 2 
    _ConnectorLocation: 2 
DVI-I-1 disconnected (normal left inverted right x axis y axis)
    Identifier: 0x27e
    Timestamp:  454764
    Subpixel:   unknown
    Clones:    
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: TMDS 
        supported: TMDS
    ConnectorType: DVI-I 
    ConnectorNumber: 0 
    _ConnectorLocation: 0 
HDMI-0 connected 1280x720+0+0 (0x285) normal (normal left inverted right x axis y axis) 0mm x 0mm
    Identifier: 0x27f
    Timestamp:  454764
    Subpixel:   unknown
    Gamma:      1.0:1.0:1.0
    Brightness: 1.0
    Clones:    
    CRTC:       0
    CRTCs:      0 1
    Transform:  1.000000 0.000000 0.000000
                0.000000 1.000000 0.000000
                0.000000 0.000000 1.000000
               filter: 
    EDID: 
        00ffffffffffff003dcb610700000000
        00110103800000780adaffa3584aa229
        17494b00000001010101010101010101
        010101010101011d007251d01e206e28
        550098063200001e011d8018711c1620
        582c250098063200009e000000fc0054
        582d53523630350a20202020000000fd
        003b3d0f440f000a2020202020200142
        020334714e84050302070601100f0e0b
        0a242335097f070f7f071707503f06c0
        5706005f7e01675e00834f000066030c
        001100808c0ad08a20e02d10103e9600
        9806320000188c0ad08a20e02d10103e
        9600b206220000188c0aa01451f01600
        267c43009806320000988c0aa01451f0
        1600267c4300b206220000980000005d
    BorderDimensions: 4 
        supported: 4
    Border: 0 0 0 0 
        range: (0, 65535)
    SignalFormat: TMDS 
        supported: TMDS
    ConnectorType: HDMI 
    ConnectorNumber: 1 
    _ConnectorLocation: 1 
  1280x720 (0x280)   74.2MHz +HSync +VSync +preferred
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   60.0Hz
  1920x1080 (0x281)  148.3MHz +HSync +VSync
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   67.4KHz
        v: height 1080 start 1084 end 1089 total 1125           clock   59.9Hz
  1920x1080 (0x282)   74.2MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   33.8KHz
        v: height 1080 start 1084 end 1094 total 1124           clock   60.1Hz
  1920x1080 (0x283)   74.2MHz +HSync +VSync Interlace
        h: width  1920 start 2008 end 2052 total 2200 skew    0 clock   33.7KHz
        v: height 1080 start 1084 end 1094 total 1124           clock   60.0Hz
  1440x480 (0x284)   27.0MHz -HSync -VSync Interlace
        h: width  1440 start 1478 end 1602 total 1716 skew    0 clock   15.7KHz
        v: height  480 start  488 end  494 total  524           clock   60.1Hz
  1280x720 (0x285)   74.2MHz +HSync +VSync *current
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock   45.0KHz
        v: height  720 start  725 end  730 total  750           clock   59.9Hz
  720x480 (0x286)   27.0MHz -HSync -VSync
        h: width   720 start  736 end  798 total  858 skew    0 clock   31.5KHz
        v: height  480 start  489 end  495 total  525           clock   59.9Hz
  720x480 (0x287)   13.5MHz -HSync -VSync Interlace
        h: width   720 start  739 end  801 total  858 skew    0 clock   15.7KHz
        v: height  480 start  488 end  494 total  524           clock   60.1Hz
  640x480 (0x288)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  480x480 (0x289)   18.0MHz -HSync -VSync
        h: width   480 start  490 end  532 total  572 skew    0 clock   31.5KHz
        v: height  480 start  489 end  495 total  525           clock   59.9Hz
  411x480 (0x28a)   15.4MHz -HSync -VSync
        h: width   411 start  420 end  456 total  490 skew    0 clock   31.5KHz
        v: height  480 start  489 end  495 total  525           clock   60.0Hz
  3x480 (0x28b)    0.1MHz -HSync -VSync Interlace
        h: width     3 start    4 end    4 total    4 skew    0 clock   18.5KHz
        v: height  480 start  488 end  494 total  524           clock   70.6Hz

```

---

### Post by blm-ubunet on 2014-06-07
> export DISPLAY=":0.0" 
xrandr --output HDMI-0 --mode "1280x720"
Change that to:
```
xrandr -d :0.0 --output HDMI-0 --mode "1280x720"
```
or
```
DISPLAY=:0 xrandr --output HDMI-0 --mode "1280x720"
```
does that make any difference?

Have you disabled the start up of "xfsettingsd" ?

I fairly sure that nvidia-settings (called from cmd line) could also work-around the problem, but there is a high threshold to their verbose cmd line interface.

---

### Post by itlarson2 on 2014-06-07
Sory- no.  When the computer is in its borked state xrandr just gives the following output for either command:

```
xrandr: Configure crtc 0 failed
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  7 (RRSetScreenSize)
  Serial number of failed request:  31
  Current serial number in output stream:  32
```

and "xrandr --verbose" just says it can't open the display.  

This was after I manualy did the "export XAUTHORITY="/home/itl/.Xauthority"".  I'm assuming theres no point in setting this up in /etc/udev/rules.d if it won't work from the command line.

---

### Post by blm-ubunet on 2014-06-07
You could try/use this in /etc/X11/xorg.conf:
```
Option "ConnectedMonitor" "DFP-0"
```

You can use nvidia-settings or the /var/log/Xorg.0.log file to determine if "DFP-0" is the right port..
The xrandr names do not match the nvidia internal names.

---

### Post by itlarson2 on 2014-06-08
No, the xorg line didn't help.  You didn't specify the section, so, after some googling, I put it in the "Device" section.  

One experiment I tried did work, though- I plugged my TV directly into the computer, bypassing my A/V amplifier.  This fixes the problem, but isn't an ideal solution, since I have a PS3 that also uses the same screen.  I could use the TV to switch video inputs. The TV isn't near the other components, though, so it would require buying a second long HDMI cable, and stringing it through the basement.  It would also require extra fiddling with the remote to switch inputs, since the audio would still be switched by the amp.  

I tried generating a new xorg with nvidia-settings while the computer was pluged directly to the TV, then pluging back into the amp, but the two xorg files are pretty much identical.  the only difference is the old one says ModelName "ONKYO Corporation TX-SR605" and the new one says ModelName "PANASONIC-TV".  This had no effect on the problem.

---

### Post by blm-ubunet on 2014-06-08
Does your AV receiver have any EDID management options?
Some of the "better" ones have caching options for displays that are off or switched to other input..

DFP-0 could have been the wrong port name..have to check the logfile /var/log/Xorg.0.log.

---

### Post by itlarson2 on 2014-06-09
This problem seems to of mysteriously resolved.  When I tried to enter my amp's setup menus I was getting a flashing blue screen.  I moved the HDMI cable to my TV's second HDMI input, and both the flashing screen from the amp, and the blanking screen from the computer were fixed.  Both problems remained fixed even when  even when I switched back to the first input.  Is it possible the first HDMI input is failing, or was just badly plugged?  I will use the second input from now on to be safe.

I will mark this solved if it doesn't come back after a few days.  Thank you for all your help

---

### Post by dannyboy79 on 2014-06-10
adding these lines has always worked for me. of course adjust DFP to whatever you /var/log/Xorg.0.log shows
```
Option "ConnectedMonitor" "DFP" 
Option "UseDisplayDevice" "DFP-0" 
```

---

### Post by blm-ubunet on 2014-06-11
This problem seems to be centred on mythbuntu 14.04 & xfce desktop.

The most useful xorg.conf settings could be:
- caching TV EDID with nvidia-settings into a file "edid2.bin"

```
Option "UseHotplugEvents" "False"
Option "CustomEDID" "DFP-0:/tmp/edid2.bin"
```

check if /tmp/ is a permanent folder..else move file to /etc/X11/ or similar..

---

### Post by itlarson2 on 2014-06-11
This problem is persisting- although it doesn't take effect immediately anymore, only after the TV has been off for a while.  I will try  disabling dpms  with "xset -dpms"  and screen blanking with "xset -s off".  I had disabled the screen saver in xfce settings, but this will make sure that is not the issue.  

I would like to try the solution you sugest, but Mythtv is recording, so it will probably have to wait untill tomorrow.  Do you happen to know the command to get the TV EDID info out of nvidia-settings?  There's a button in the gui, but it's grayed out.  I will try rebooting when I can, since the same problem may be causing the button to be inactive.

---

### Post by itlarson2 on 2014-06-11
I was able to generate edid.bin after rebooting.  I tried adding the lines to "device"  but it just booted to a blank screen.  Same results with them placed in "screen".  Will look at this again when I can, tomorrow hopefully.

---

### Post by blm-ubunet on 2014-06-12
Can you please post your /var/log/Xorg.0.log file from a working login session.
We don't know if DFP-0 is the right port yet..

Most of the contents of xorg.conf can go anywhere.
AFAIK The whole file is parsed first, it is not executed by a cmd interpreter.

Are you sure your edid file name & path are exactly right in the xorg.conf file.
I believe you have to use the binary file format.

---

### Post by itlarson2 on 2014-06-15
Last night I finally found time to try this again, and have gotten the custom edid fix to work after with a few tweaks.  First, I ran nvidia-settings as root, and with the TV plugged directly into the computer to record the edid.  I noticed the second line you gave me was missing a quote right before "DFP" so I fixed that.  The /tmp directory seems to be cleared out after a reboot, so I moved the file to /etc.  I also ran "chmod 777" on the file to be sure there were no  permissions issues.  I have been using DFP-1 all along, since this is correct according to "/var/log/Xorg.0.log" which I probably should have mentioned.  So far the problem hasn't come back.  I'll give it a few days before I mark this "solved".  Thanks for all your help.

---

### Post by khPWXxF on 2014-06-23
Would anyone with this problem please check that you still have the file /etc/X11/Xorg.conf?
 
I had this ‘dead tv’ problem and fixed it with advice found here:

[http://www.gossamer-threads.com/lists/mythtv/users/570769](http://www.gossamer-threads.com/lists/mythtv/users/570769)

I noted that /etc/X11/Xorg.conf was missing so created one with [I]nvidia-xconfig.
[/I]I then edited it to add to the "Device" section: 
[I][I]
Option "UseHotplugEvents" "false"[/I] [/I]

That worked fine last week and the 'dead tv' problem was fixed. However, I find that the vital configuration file /etc/X11/Xorg.conf keeps vanishing so the fault keeps coming back. The file gets renamed with the date appended eg tonight at 20:38 it was renamed: /etc/X11/Xorg.conf.06232014.   


I cannot establish the pattern of when it happens.  There are NO entries with a timestamp of 20:38 tonight in syslog, frontend or backend logs.
 
Any ideas?
 
Phil

---

### Post by khPWXxF on 2014-06-23
Would anyone with this problem please check that you still have the file /etc/X11/Xorg.conf?

I had this ‘dead tv’ problem and fixed it with advice found here:
[http://www.gossamer-threads.com/lists/mythtv/users/570769](http://www.gossamer-threads.com/lists/mythtv/users/570769)

There was no config file /etc/X11/Xorg.conf so I created one with* nvidia-xconfig.*
I then edited it and added to the "Device" section: 
```
*Option "UseHotplugEvents" "false"*
``` 
That worked fine last week. However, I find that the vital configuration file /etc/X11/Xorg.conf keeps vanishing so the fault keeps coming back. The file gets copied and renamed with the date appended.  eg tonight at 20:38 it was renamed: /etc/X11/Xorg.conf.06232014.   

I cannot establish a pattern of how it happens.  There are NO entries with a timestamp of 20:38 tonight in syslog, frontend or backend logs.
 
Any ideas?
 
Phil

---

### Post by blm-ubunet on 2014-06-24
We discussed that option keyword in this thread as well..

The file is named:
```
/etc/X11/xorg.conf
```
note the upper & lower case "x"; maybe that's the problem
The current session log file is named:
```
/var/log/Xorg.0.log
```

You can create this file with Xorg, nvidia-xconfig or nvidia-settings or by hand.

---

### Post by khPWXxF on 2014-06-24
Apologies - that was a typo.  You are correct - the file is 
> /etc/X11/xorg.conf
and it is that which was vanishing.  I'm removing write permissions in the hope that it will linger longer or that something will complain!
Phil

---

### Post by khPWXxF on 2014-06-24
After further googling I think I have the mechanism by which xorg.conf is renamed:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1307546](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1307546)

If file > [COLOR=#333333][FONT=monospace]/var/lib/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]ubuntu-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]drivers-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]common/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]last_gfx_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]boot[/FONT][/COLOR][COLOR=#333333][FONT=monospace] is missing then it assumes we are doing an upgrade from a previous version so it does the rename.  That trigger file exists on my system - creation time of last reboot.

I had a suspicion of upgrades to 0.27.1 causing it - I could have inadvertently fooled it by upgrading with
```
sudo apt-get install mythtv
``` 
  rather than
```
sudo apt-get upgrade
```

Thanks for listening!

Phil

[/FONT][/COLOR]

---

### Post by blm-ubunet on 2014-06-24
Good debugging. 
Forgot about the distro releases upgrades move this file out of the way.

sudo apt-get distupgrade ?
This does **not do** a upgrade between distro releases but point updates inside of a release.

---

