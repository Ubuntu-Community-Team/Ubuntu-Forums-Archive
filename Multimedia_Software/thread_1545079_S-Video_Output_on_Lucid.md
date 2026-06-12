---
title: "S-Video Output on Lucid"
date: 2010-08-03
forum: Multimedia Software
---

### Post by Andysan on 2010-08-03
Hi folks,

I have a NVidia Geforce Go 6150 that I would like to output video via the S-Video port to hook upto my TV via composite/SCART.  One way that I know of doing this is via xrandr, but this produces an error in Lucid:

```
andy@ubuntu:~$ xrandr --output S-video --set load_detection 1
warning: output S-video not found; ignoring
X Error of failed request:  BadRROutput (invalid Output parameter)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  15 (RRGetOutputProperty)
  Serial number of failed request:  26
  Current serial number in output stream:  26
```


I have also tried the Nvidia corporate drivers and a custom xorg.conf file but the output doesnt seem to be initialised via either of these methods.  I'm running a completely fresh Kubuntu install.  Thanks.

---

### Post by wrench 36 on 2010-08-03
first do u have onboard video driver (another vga port)?
 if so u will need to disable in bios settings
next dose ur card support what u want to do?
then try 
 alt+f2 or any terminal

gksudo nvidia-settings

it sets u up as a semi root user so u can SAVE ur settings, same gui but with root privileges

ok that is still not going to work though and u will probably need to manually edit the xorg.conf file 
i have found two ways of doing the same thing, the first is in the nvidia-settings gui, when u hit the tab to save config u can manualy edit the settings, also pay attention to the (merg with file, box: to check or un check)
or the old fashind way
 
gksudo gedit /etc/X11/xorg.conf

but before u change anything run 
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
FIRST to save a backup of a known working file 


here r a few links to help u edit the file try the firs and so on in that order

  [http://en.wikibooks.org/wiki/NVidia/TV-OUT](http://en.wikibooks.org/wiki/NVidia/TV-OUT)
what worked 4 me 
find the "A complete device-section"

 
Section "Device" 
 Identifier  "Card_tv"
 Driver      "nvidia"
 BusID       "PCI:1:0:0"  # May differ (not needed unless you have two or more cards)
 Option      "TVOutFormat" "COMPOSITE"  # Or "SVIDEO"
 Option      "TVStandard" "NTSC-M"
 Option      "ConnectedMonitor" "TV"
EndSection

 
and under the option list leave only the one u want in "italics"
ie
Section "Device" 
 Identifier  "Card_tv"
 Driver      "nvidia"
 BusID       "PCI:1:0:0"  # May differ (not needed unless you have two or more cards)
 Option      "TVOutFormat" "SVIDEO"
 Option      "TVStandard"  "NTSC-M"
 Option      "ConnectedMonitor" "TV"
EndSection
 
see how only svideo in "" is there
there r quite a few other things but that is where i would start.

 [http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html)
way more technical 

or posibly this 1
 [https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)
i even rember 1 4 beginners and the svideo in ubuntu

hope this helps im fresh with this i just did an upgrade from 9.04 to 10.04

---

