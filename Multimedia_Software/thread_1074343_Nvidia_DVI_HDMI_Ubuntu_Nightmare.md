---
title: "Nvidia DVI HDMI Ubuntu Nightmare"
date: 2009-02-19
forum: Multimedia Software
---

### Post by VastOne on 2009-02-19
For over 5 weeks now I have read and parsed a zillion threads and notes on the simple task of getting a correct DVI or HDMI resolution on my RCA 42 inch.

I have spent money to get the "right equipment" to change a simple resolution 

I have worn my fingers to bone and my eyes are now dead... Just to change a simple resolution....

I now know more about X than I ever thought possible and still cannot change a simple resolution....

It shows up in Nvidia X Server settings, but nay, it will not run....this simple resolution.....

As we advance to higher scale electronics, and purchase computers to match those electronics, it sure would be nice to change a simple resolution....

No help needed, I am chucking the attempt and glad to vent...

To hell with nVidia and X and a simple path to a simple resolution...

VastOne

---

### Post by xc3RnbFO8P on 2009-02-19
> It shows up in Nvidia X Server settings, but nay, it will not run....this simple resolution.....
Did you save it to xorg.conf?

---

### Post by VastOne on 2009-02-19
> **Ringi said:**
> Did you save it to xorg.conf?

Yes and manually entered it....

---

### Post by Alekth on 2009-02-19
Is the issue overscan?

That was my lost battle a few months ago, and from the amount of threads I read on it I don't think it's been solved software-wise.

But if you haven't tried yet, check if your TV has an option for 1:1 pixel mapping, seems to be the only thing that helps.

---

### Post by VastOne on 2009-02-19
> **Alekth said:**
> Is the issue overscan?

That was my lost battle a few months ago, and from the amount of threads I read on it I don't think it's been solved software-wise.

But if you haven't tried yet, check if your TV has an option for 1:1 pixel mapping, seems to be the only thing that helps.

Alekth,

It started as the overscan issue in pure 1920 * 1080 mode, but know is the 1360 * 768 setting in nVidia X that will not work or be recognized as a valid modeline

The only modline setting I can get to work at all is the 1920 * 1080 that is the same as the virtual mode X sees when it auto selects.

Just a simple process, you would think, to switch to the TV's native resolution

---

### Post by xc3RnbFO8P on 2009-02-19
Start with the orginal xorg.conf
**sudo nvida-settings**
Use separate screens, xinerama , choose your resolution on both screens (not auto) if have interlace TV choose 60i
save to X Configuration file.

---

### Post by VastOne on 2009-02-19
> **Ringi said:**
> Start with the orginal xorg.conf
**sudo nvida-settings**
Use separate screens, xinerama , choose your resolution on both screens (not auto) if have interlace TV choose 60i
save to X Configuration file.

Ringi,

Only using one screen, have done all the xrander commands and interlace..

Again, in nvidia-settings, I can choose and save 1360 * 768, but it will not display.  the virtual 1920* 1080 is the only display I can get to work but it is over scanned and so jumpy it kills the eyes.

---

### Post by xc3RnbFO8P on 2009-02-19
Did you try 1280x720 ?
> Only using one screen
sorry didn't see that.

---

### Post by VastOne on 2009-02-19
> **Ringi said:**
> Did you try 1280x720 ?

sorry didn't see that.

Ringi,

Yes.  From within nVidia-settings and it ballooned up to a level so large it was ridiculous

Appreciate your input!

---

### Post by xc3RnbFO8P on 2009-02-19
I had the same problem with my 720p 40" (Nvidia 6700XL) in Ubuntu and XP with DVI to HDMI,
now I have a 42" Full HD and Nvidia 9500GS with HDMI to HDMI.
Had  problem  in 8.04 and 8.10 so I installed 9.04 witch has Nvidia 180.29 driver
and it works fine.
What are your computer spec?

---

### Post by VastOne on 2009-02-19
> **Ringi said:**
> I had the same problem with my 720p 40" (Nvidia 6700XL) in Ubuntu and XP with DVI to HDMI,
now I have a 42" Full HD and Nvidia 9500GS with HDMI to HDMI.
Had  problem  in 8.04 and 8.10 so I installed 9.04 witch has Nvidia 180.29 driver
and it works fine.
What are your computer spec?

I am using the   180.29 as well with 8.10

Intel Core2 Quad Q6600 2,4 GHz

nVidia 8500 GS with 512

very very good HP system... this is my only issue ever with it...

FYI, I am now on an old emachine with a generic built in video on my 42 inch with just a VGA connection and get 1000 times better view and response...It is not HD or DVI, but at least I can use it...

I have fought this so long my apathy is overwhelming, but I really appreciate your help.

I may just go out and buy the 9500 to see if that is the difference...

VastOne

---

### Post by xc3RnbFO8P on 2009-02-20
> I may just go out and buy the 9500 to see if that is the difference...
Before you do that, try Jaunty Live Disk
[http://cdimage.ubuntu.com/releases/jaunty/alpha-4/]("http://cdimage.ubuntu.com/releases/jaunty/alpha-4/")

---

### Post by VastOne on 2009-02-20
> **Ringi said:**
> Before you do that, try Jaunty Live Disk
[http://cdimage.ubuntu.com/releases/jaunty/alpha-4/]("http://cdimage.ubuntu.com/releases/jaunty/alpha-4/")

I actually meant to post that as my first alternative before going out and getting a card...

Reading more and more posts, it does appear to be an X issue as even ATI cards are in the same boat

Thanks for the tip

---

### Post by VastOne on 2009-02-20
> **Ringi said:**
> Before you do that, try Jaunty Live Disk
[http://cdimage.ubuntu.com/releases/jaunty/alpha-4/]("http://cdimage.ubuntu.com/releases/jaunty/alpha-4/")

Thus the nightmare continues...

Installed Jaunty and was quite pleased with the install and the look and the new ext4 and auto grub detection and no issues...

Take the computer to the HD TV and was initially pleased at the login screen as it was 1920 * 1080 and not jumpy at all like it was with 8.10, in fact it is crystal clear.

First bad sign was logging in my fonts were at least 30 times what the rest of the screen was.  Get into Jaunty to see I am at a 640 resolution even tho nVidia X says I am at 1920 * 1080.  I try changing to 1360 * 768 and it lets me change, but I then go to a 400 resolution.

I ctrl alt F2 to a tty scren to have a look at the xorg.conf file (after stopping X) and to my chagrin, Jaunty will not let me open it with a generic message that it cannot be opened.  

Beating my head against a wall....I took two steps forward to go 10 back.....

---

### Post by xc3RnbFO8P on 2009-02-21
Read is:
[http://ubuntuforums.org/showthread.php?p=5569244#post5569244]("http://ubuntuforums.org/showthread.php?p=5569244#post5569244")

> Option         "ModeValidation" "NoDFPNativeResolutionCheck"
Option         "ExactModeTimingsDVI" "True"

---

### Post by Total Legend on 2009-02-25
> **Ringi said:**
> I had the same problem with my 720p 40" (Nvidia 6700XL) in Ubuntu and XP with DVI to HDMI,
now I have a 42" Full HD and Nvidia 9500GS with HDMI to HDMI.
Had  problem  in 8.04 and 8.10 so I installed 9.04 witch has Nvidia 180.29 driver
and it works fine.
What are your computer spec?

Did the HDMI to HDMI solve the problem? Or was it the 9.04 that solved it? Or both?

I'm having the same problem as VastOne. I have a 1080p HDTV. I have a GeForce 9600GT 512 (but it only has two DVI ports). I use a DVI to HDMI cable. I can return the 9600GT (got 3 days left) and get a 9500GS if it would fix this problem.

I only managed to get it to work by finding the proper modelines and I got at best 1202x692 after making the edits. Problem is that when I change the source on my TV (to Cable or the other HDMI with the Xbox on it) then when I go back to the HDMI2 port with Ubuntu on it, the right hand side gets cut off. The only way it'll go back to the resolution I want is if I reboot the entire ubuntu server. It's a pain that I've been dealing with for weeks now.

But if I can just change a card and do a HDMI - HDMI setup (not using DVI) and this fixes the problem, I'd totally hit it.

---

### Post by xc3RnbFO8P on 2009-02-28
I got it solved in 9.04 nvidia 180.29 with HDMI>HDMI (42" 1081i).
I didn't try DVI>HDMI.

---

### Post by VastOne on 2009-03-02
> **Ringi said:**
> I got it solved in 9.04 nvidia 180.29 with HDMI>HDMI (42" 1081i).
I didn't try DVI>HDMI.

Can you post your xorg.conf file please?

---

### Post by xc3RnbFO8P on 2009-03-02
> **VastOne said:**
> Can you post your xorg.conf file please?
Remember I got interlace TV! 
> Option         "metamodes" "DFP-1: 1920x1080_60[COLOR="Red"]**i**[/COLOR] +0+0"

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
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "0"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG W2452"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "OEM 42'' TFT-TV"
    HorizSync       15.0 - 46.0
    VertRefresh     49.0 - 61.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP-0: 1920x1200 +0+0, DFP-1: 1920x1080 +1920+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "DFP-0: 1920x1200 +0+0, DFP-1: 1920x1080 +1920+0; DFP-0: 1920x1200 +0+0, DFP-1: nvidia-auto-select +1920+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: 1920x1200 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP-1: 1920x1080 +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: 1920x1080_60[COLOR="Red"]**i**[/COLOR] +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by molder on 2009-04-24
Has anyone gotten HDMI sound to work on this card?

---

