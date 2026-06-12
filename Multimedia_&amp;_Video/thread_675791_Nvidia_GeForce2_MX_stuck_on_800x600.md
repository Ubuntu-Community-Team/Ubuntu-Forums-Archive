---
title: "Nvidia GeForce2 MX stuck on 800x600"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by FaulkYou on 2008-01-23
Hello all,

I'm new to Linux. I recently installed Gutsy on my Dell Dimension 8200 in a dual-boot with WinXP. The computer has an Nvidia GeForce2 MX (AGP I think), and I use a ViewSonic VA520 LCD monitor instead of the Dell M991 that came with the box (it's huge and impractical for my desk).

When I installed Ubuntu 7.10 (from live CD), I had to hook up the old monitor because it defaulted to a high resolution (can't remember what) that is out of range of the LCD's optimal 1024x768 (I believe @60Hz). I set the resolution to 1024x768 after install, and it seemed happy on the smaller monitor, and looked beautiful. However, after the initial updates and enabling the recommended proprietary driver for the Nvidia card, the display resolution shrank to 800x600, which is now the only resolution available in the system menu (so is 50Hz).

I've played around with the driver and monitor settings to no end. I installed and ran Envy which gave me a nice Nvidia settings panel, but didn't help with my screen resolution problem. I've even gone in to xorg.conf at the suggestion of similar posts, but haven't worked out the problem. The funny thing is I've gotten my splash screens to display at 1024x768. I'm like "Come on graphics card, you can do this!"

At this point I really do want to kill my X server. If I could get back to 1024x768 I would be so happy.

Help is appreciated.

p.s. Envy did help iron out some bugs that also showed up in the enhanced visual effects after this all went down (like window bars disappearing when enabled), though there are still a few kinks here and there.

---

### Post by overdrank on 2008-01-24
> **FaulkYou said:**
> Hello all,

I'm new to Linux. I recently installed Gutsy on my Dell Dimension 8200 in a dual-boot with WinXP. The computer has an Nvidia GeForce2 MX (AGP I think), and I use a ViewSonic VA520 LCD monitor instead of the Dell M991 that came with the box (it's huge and impractical for my desk).

When I installed Ubuntu 7.10 (from live CD), I had to hook up the old monitor because it defaulted to a high resolution (can't remember what) that is out of range of the LCD's optimal 1024x768 (I believe @60Hz). I set the resolution to 1024x768 after install, and it seemed happy on the smaller monitor, and looked beautiful. However, after the initial updates and enabling the recommended proprietary driver for the Nvidia card, the display resolution shrank to 800x600, which is now the only resolution available in the system menu (so is 50Hz).

I've played around with the driver and monitor settings to no end. I installed and ran Envy which gave me a nice Nvidia settings panel, but didn't help with my screen resolution problem. I've even gone in to xorg.conf at the suggestion of similar posts, but haven't worked out the problem. The funny thing is I've gotten my splash screens to display at 1024x768. I'm like "Come on graphics card, you can do this!"

At this point I really do want to kill my X server. If I could get back to 1024x768 I would be so happy.

Help is appreciated.

p.s. Envy did help iron out some bugs that also showed up in the enhanced visual effects after this all went down (like window bars disappearing when enabled), though there are still a few kinks here and there.

HI and welcome, when using the nvidia-settings to set your resolution have you used this command ```
gksudo nvidia-settings
``` this will allow your settings to be saved.

---

### Post by FaulkYou on 2008-01-25
Greetings overdrank, thanks for the welcome,

I have indeed used that command (though I still don't know what "gksudo" actually means). It gives me the Nvidia X Server Settings panel/application that came with the new driver that Envy installed. However, in the section of the panel that shows my monitor settings, the "resolution" field of my primary monitor doesn't show any specific resolutions - only "auto" and a grayed-out "off"..

---

### Post by overdrank on 2008-01-26
> **FaulkYou said:**
> Greetings overdrank, thanks for the welcome,

I have indeed used that command (though I still don't know what "gksudo" actually means). It gives me the Nvidia X Server Settings panel/application that came with the new driver that Envy installed. However, in the section of the panel that shows my monitor settings, the "resolution" field of my primary monitor doesn't show any specific resolutions - only "auto" and a grayed-out "off"..

HI and sorry for the delay, can you post the output of this command ```
cat /etc/X11/xorg.conf
``` and also have you tried to configure your xorg with the command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` this may allow you to add your resolution. If not use the command without the  **_-phigh_** tag.

---

### Post by bkelly on 2008-01-26
I am quite new to Linux, but I just went through some problems with nvidia and gutsy.  Look at this post and see if that process helps you any:

[http://ubuntuforums.org/showthread.php?p=4207051#post4207051](http://ubuntuforums.org/showthread.php?p=4207051#post4207051)

I checked the FAQs and did not see any special code to surround the URL with.  Using brackets with code and slash code did not seem to make any difference.

---

### Post by Waldo2020 on 2008-01-28
I have the very same problem. "nvidia" is broken. The only 
way I could get 1280x1024 was to startx as root. using
the verbose set to 5, and looking at the logs, I found
that the nvidia driver was rejecting all resolutions except
640x480. I was able to get 800x600 by telling the driver
to ignore the EDID and luckily that help some. The issue
is that the  nvidia driver no longer reads the monitor EDID
(and hence all the valid settings/modelines etc). Everything
worked fine at full resolution with the VESA driver, so I know
nvidia is at fault.

---

### Post by FaulkYou on 2008-01-30
Sorry for the delayed response,

So here's the breakdown of my situation from what I found out since my last post:

Since my graphics card is based on the GeForce2 chipset, it is not one of the 'new' boards. It is considered legacy hardware. The restricted driver that Gutsy says you have to install and enable to get the full hardware acceleration features (those that allow the advanced visual effects in Gnome) is actually the nvidia-glx driver package.

There are three tiers of nvidia proprietary drivers:
1) **nvidia-glx-new** which is for the newest cards
2) **nvidia-glx** which, among others, is for GeForce4 and up
3) **nvidia-glx-legacy** which is for the 'older' Nvidia cards

In the new version of Envy (for Gutsy), it lists these drivers by their version numbers instead of their names. If you select the "Install Nvidia drivers manually" radio button, you will see the three drivers listed by version number. If I have Envy automatically install the Nvidia driver while using my old Geforce2 (:mad:), or enable the Restricted driver that Gutsy plugs, they both install the nvidia-glx driver. I think Envy also runs a configuration script or two on your behalf.

The regular glx driver allowed my card to serviceably render the enhanced visual effects (with glitches), but since it's not made specifically for the card, it won't allow for resolutions that my card is capable of, and stuck me at 800x600. After a bit of fiddling, I installed the nvidia-glx-legacy driver and voila! Resolutions galore.

The drawback is that the legacy driver does not support the accelerated hardware features, so while OpenGL works, I can't get enhanced visual effects in Gnome. If I try to enable them, Ubuntu says "you have to enable the restricted driver that we told you about in order to do that" which basically translates to "click this button to reinstall the wrong driver. What also sucks is I don't think Nvidia is going to be coming out with any updates to this driver.

I've also now come upon this darned problem that I've seen discussed in a few threads where when I hit Ctrl+Alt+F(1-6) in Gnome, I get a blank screen with a blinking cursor instead of a login terminal, which is needless to say frustrating. I'm pretty sure this has to do with the Nvidia driver and the framebuffer.

If I enable the frambuffer by going into /etc/modules and add fbcon and vga16fb and then  run the command
```
sudo update-initramfs -u -k `uname -r`
```
and reboot, I get the login prompts back (in a nice font), but my shutdown splash screen turns dark and muddy. This is a whole other issue, not along the topic of this thread, but I thought it was worth mentioning.

Anyway, I'm not inclined to mark this thread solved, as I'm not exactly happy with this explanation, but it's what I've got at the moment. I appreciate the posts and help guys. I wondered if I should have posted this in the beginners section. I would welcome any more input on the issue.

overdrank, I have yet to play with the xserver reconfiguration but I'll check it out. Also, here is the output from my cat xorg.conf command as it stands now, whether or not it still matters - thanks for the input.

```
Section "Files"
EndSection

Section "Module"
        Load            "glx"
        Load            "v4l"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "vesa"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  0
        Option          "NoLogo"        "true"
EndSection

Section "Monitor"
        Identifier      "Failsafe Monitor"
        Vendorname      "ViewSonic"
        Modelname       "ViewSonic VA520"
        Horizsync       30-62
        Vertrefresh     50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1024x768@60"   "1280x960@60"   "1024x768@70"  "1024x768@75"    "832x624@75"    "800x600@60"    "800x600@75"    "800x600@72"   "800x600@56"     "640x480@75"    "640x480@72"    "640x480@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
EndSection
Section "device" #           
        Identifier      "device1"
        Boardname       "vesa"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  1
EndSection
Section "screen" #           
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
EndSection
Section "monitor" #           
        Identifier      "monitor1"
        Gamma   1.0
EndSection
Section "ServerFlags"
EndSection
Section "Extensions"
        Option          "Composite"     "Disable"
EndSection

```

---

### Post by rodent69 on 2008-03-10
Thanks for the modelines, v&h sync for the va520.  Wouldn't work correctly with my radeon 7500 pci with Xorg either.  This card/monitor combo is def not a good thing.

---

