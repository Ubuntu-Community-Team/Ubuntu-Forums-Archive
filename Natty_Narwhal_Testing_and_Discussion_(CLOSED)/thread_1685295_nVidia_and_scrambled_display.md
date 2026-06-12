---
title: "nVidia and scrambled display"
date: 2011-02-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by VMC on 2011-02-10
For the past week of zsync downloads. Whenever I try to use natty, I get the following scrambled display.

The only way I can see a display is to F6, and add nomodeset to the startup string. Then I have a workable display, albeit 800x600.

I have a NVIDIA GeForce 6150 SE intregrated graphics.

Here is what the display looks like:

Anyone else get this display error? I'm sure its related to new X, but I haven't seen any posting on this display error.

---

### Post by coffeecat on 2011-02-10
Yup. Got that with GeForce 7025 integrated graphics but not when I put a 8400GS PCIe card in.

---

### Post by rburkartjo on 2011-02-10
vmc i have getting that since alpha1. i had to at first also change too 800 x 600. finally reset monitor enough so i could get it back to 1200 x 900. even so i still get the scramble when first startup then it goes to useable monitor.

---

### Post by cariboo on 2011-02-10
I get a tiled desktop background when I first start it on my system using the nouveau drivers, but once the desktop is finished loading, everything is normal most of the time. There are a few artifacts very occasionally, but I attribute that more to the hard life, the old AGP 6600GT has had more than anything else. When I first acquired the system, the gpu fan was so clogged with dust it wouldn't turn, and temps were running in the low 90's.

---

### Post by VMC on 2011-02-10
> **rburkartjo said:**
> vmc i have getting that since alpha1. i had to at first also change too 800 x 600. finally reset monitor enough so i could get it back to 1200 x 900. even so i still get the scramble when first startup then it goes to useable monitor.

Interesting idea to reset the monitor. I'll try that.

 I've read all the nvidia errors on several topics but haven't seen anyone report the scrambled display problem before.

Edit: No, the reset monitor didn't work.

---

### Post by rburkartjo on 2011-02-11
vmc you have to be quick when you reset the monitor you only have a couple of seconds to set and confirm the display mode you want. took me a few times to do

---

### Post by dino99 on 2011-02-11
i dont have (had) this issue but compiz is not installed on my pc

---

### Post by VMC on 2011-02-11
> **rburkartjo said:**
> vmc you have to be quick when you reset the monitor you only have a couple of seconds to set and confirm the display mode you want. took me a few times to do

Your referring to the monitor auto reset itself and not something else from Ubuntu, correct?

---

### Post by eco2geek on 2011-02-12
> **VMC said:**
> Anyone else get this display error? I'm sure its related to new X, but I haven't seen any posting on this display error.

I have the same chipset as you, and am getting the same scrambled graphics using the "nouveau" driver on all Alpha2 versions of *buntu (Kubuntu, Xubuntu, etc.) running from the live CD (I don't have this alpha version installed, for obvious reasons.)

The only solution I've found so far (since installing "nvidia-current" takes out most of the xorg* packages) is to start with "nomodeset", install the xserver-xorg-video-nv package, and use a customised "xorg.conf".

---

### Post by VMC on 2011-02-12
> **eco2geek said:**
> I have the same chipset as you, and am getting the same scrambled graphics using the "nouveau" driver on all Alpha2 versions of *buntu (Kubuntu, Xubuntu, etc.) running from the live CD (I don't have this alpha version installed, for obvious reasons.)

The only solution I've found so far (since installing "nvidia-current" takes out most of the xorg* packages) is to start with "nomodeset", install the xserver-xorg-video-nv package, and use a customised "xorg.conf".

Does your "xorg.conf" include the "removeABI" section? If not, could you post your "xorg.conf"? Thanks.

Also are you running "xserver 1.10", or did you downgrade to "9". 

finally, what does "nvidia-current" do? I normally just install nvidia proprietary program, such as "NVIDIA-Linux-x86_64-270.18.run".

---

### Post by eco2geek on 2011-02-12
> **VMC said:**
> Does your "xorg.conf" include the "removeABI" section? If not, could you post your "xorg.conf"? Thanks.
I'm running from the live Alpha 2 CD here, and using the version of Xorg that comes with it. It comes with X server 1.9.99.901 (1.10.0 RC 1). Using the "nv" driver, my xorg.conf looks like this:
```
# xorg.conf

Section "Monitor"
  DisplaySize  340 270
  HorizSync    30-83
  Identifier   "Monitor[0]"
  ModelName    "EN7750"
  Option       "DPMS"
  VendorName   "EPI"
  VertRefresh  43-75
  UseModes     "Modes[0]"
EndSection

Section "Modes"
  Identifier   "Modes[0]"
  Modeline 	"1280x1024" 135 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Screen"
  DefaultDepth 24
  SubSection "Display"
    Depth      15
    Modes      "1280x1024" "1024x768" "800x600" 
  EndSubSection
  SubSection "Display"
    Depth      16
    Modes      "1280x1024" "1024x768" "800x600" 
  EndSubSection
  SubSection "Display"
    Depth      24
    Modes      "1280x1024" "1024x768" "800x600" 
  EndSubSection
  SubSection "Display"
    Depth      8
    Modes      "1280x1024" "1024x768" "800x600" 
  EndSubSection
  Device       "Device[0]"
  Identifier   "Screen[0]"
  Monitor      "Monitor[0]"
EndSection

Section "Device"
  BoardName    "GeForce 6200 A-LE"
  Driver       "nv"
  Identifier   "Device[0]"
  VendorName   "NVidia"
EndSection

Section "ServerLayout"
  Identifier   "Layout[all]"
  Screen       "Screen[0]"
EndSection

Section "DRI"
    Group      "video"
    Mode       0660
EndSection
```
As you can see, it's configured for my particular monitor. And the "nv" driver does not allow for 3D acceleration - i.e. no Unity. 

> what does "nvidia-current" do? I normally just install nvidia proprietary program, such as "NVIDIA-Linux-x86_64-270.18.run".
It's what you want to use if at all possible when running Ubuntu from your hard disk. "nvidia-current" is the package that installs the current NVIDIA driver and automagically keeps it up to date whenever the system installs a new kernel. (Whereas, if you manually install the driver after downloading it from NVIDIA, you have to manually reinstall it every time there's a kernel upgrade.)

At the moment, the latest Ubuntu "nvidia-current" package is incompatible with the current Xorg packages.

---

### Post by paglia96 on 2011-02-13
When i try the live cd of natty happen that:

This is with the daily build of today.

But if i use a build of 1 month ago it install but whun i upgrade the result is like the image i posted, without owners drivers for the nvidia geforce 7100.

---

### Post by coffeecat on 2011-02-13
> **paglia96 said:**
> This is with the daily build of today.

But if i use a build of 1 month ago it install but whun i upgrade the result is like the image i posted, without owners drivers for the nvidia geforce 7100.

There is already a thread about this issue:

[http://ubuntuforums.org/showthread.php?t=1685295](http://ubuntuforums.org/showthread.php?t=1685295)

---

### Post by howefield on 2011-02-13
Threads merged.

---

### Post by poonforce on 2011-02-22
> **VMC said:**
> For the past week of zsync downloads. Whenever I try to use natty, I get the following scrambled display.

The only way I can see a display is to F6, and add nomodeset to the startup string. Then I have a workable display, albeit 800x600.

I have a NVIDIA GeForce 6150 SE intregrated graphics.

Here is what the display looks like:

Anyone else get this display error? I'm sure its related to new X, but I haven't seen any posting on this display error.

yes it is the same.

---

### Post by koradji on 2011-02-28
Is there a particular launchpad issue that can be used to track this incompatibility ?

---

### Post by VMC on 2011-02-28
The scrambled display is now fixed using the latest ISO from daily-live current, timed at 11:04PM.

---

