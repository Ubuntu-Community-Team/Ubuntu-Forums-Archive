---
title: "Nvidia Twinview - Window Maximizing Issue"
date: 2011-01-13
forum: Multimedia Software
---

### Post by awells527 on 2011-01-13
I am having a problem with TwinView on my dual card / 4-display setup.  I understand that TwinView will not work across different cards, and I'm OK with that.

The problem is that the desktop background, panels, and maximized windows span across both screens as if they were one giant one.  I have messed with various configuration settings for a couple days now and could not find a solution.

The weird thing is that if I only have one card enabled, it works just fine, but when I add the second card with identical settings, it does not work.  I have the two configurations below and ran a diff on both of them to show that the only difference was the addition of the sections for the second card.

Single Card Setup: [http://ubuntu.pastebin.com/FeSn7JVG](http://ubuntu.pastebin.com/FeSn7JVG)
Dual Card Setup: [http://ubuntu.pastebin.com/MWZAbnBe](http://ubuntu.pastebin.com/MWZAbnBe)
Difference: [http://ubuntu.pastebin.com/HPiVTmUE](http://ubuntu.pastebin.com/HPiVTmUE)

These are the cards that I have installed:

```
$ lspci | grep VGA
02:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GTS] (rev a1)
07:00.0 VGA compatible controller: nVidia Corporation Device 0dc4 (rev a1)

```

Any assistance would be appreciated.

---

### Post by TSJason on 2011-01-13
Hi,

You can define overrides in your twinview config that define the screen edges to your display manager. For instance, I have a triple-screen setup where each is 1280x1024. I use this in my "Screen" section to define them:


```

Option         "TwinviewXineramaInfo" "True"
Option         "TwinViewXineramaInfoOverride" "1280x1024+0+0, 1280x1024+1280+0, 1280x1024+2560+0"

```

HTH

---

### Post by awells527 on 2011-01-13
Hi TSJason - thanks for the response.  I added those lines to my xorg.conf file in the two sections and adjusted them to my resolutions.  The first time xorg threw a warning stating that I need MetaModes, so I added them, but my screens are still unfortunately not split up like they should.

Config File: [http://ubuntu.pastebin.com/aqGCUzUF](http://ubuntu.pastebin.com/aqGCUzUF)

Xorg Log: [http://ubuntu.pastebin.com/2bS9RmRB](http://ubuntu.pastebin.com/2bS9RmRB)

---

### Post by heldal on 2011-01-14
Which version of xserver-common and xserver-xorg-core do you use. I found that a recent upgrade (2:1.9.0-0ubuntu7.1) breaks twinview while the original supplied with 10.10 (2:1.9.0-0ubuntu7) works. Downgrading these packages (+ dev-packs if necessary) solved the problem for me. There is also an even newer version in the maverick-proposed repo, but I haven't tried that one yet.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/680811](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/680811)

---

### Post by heldal on 2011-01-14
Err... the problem I had seem to be fixed in the latest (2:1.9.0-0ubuntu7.3) xserver-packages in maverick-proposed, but 2:1.9.0-0ubuntu7.1 is definitely broken.

---

### Post by tjones00 on 2011-01-14
@ awells527 I have a dual nvidia card 4 monitor system.

> **awells527 said:**
> 
The problem is that the desktop background, panels, and maximized  windows span across both screens as if they were one giant one.  I have  messed with various configuration settings for a couple days now and  could not find a solution.



Isn't that what twinview is "suppose" to do? merge two monitors as they were one.

If you want a setup where you can drag applications across monitors and when you maximize applications they only maximize for the current display you need to enable separate x screens (not sessions) and turn twinview off.

Try this.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.original

sudo nvidia-xconfig --enable-all-gpus --xinerama --separate-x-screens --no-twinview
```

logout or reboot then use gksudo nvidia-settings to position displays.

1st option should activate both gpus

2nd option enables xinerama

3rd option enables 2 screens per gpu

4th ensures no twinview shenagigans.

From nvidia-xconfig -A

 >  -a, --enable-all-gpus
      Configure an X screen on every GPU in the system.

  --separate-x-screens, --no-separate-x-screens
      A GPU that supports multiple simultaneous display devices can either
      drive these display devices in TwinView, or as separate X screens.  When
      the '--separate-x-screens' option is specified, each GPU on which an X
      screen is currently configured will be updated to have two X screens
      configured.  The '--no-separate-x-screens' option will remove the second
      configured X screen on each GPU.  Please see the NVIDIA README
      description of "Separate X Screens on One GPU" for further details.

  --twinview, --no-twinview
      Enable or disable TwinView.

  --xinerama, --no-xinerama
      Enable or disable Xinerama.



Here's my xorg.conf

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@palmer)  Mon Oct  4 16:01:38 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1920 1024
    Screen      1  "Screen1" LeftOf "Screen0"
    Screen      2  "Screen2" Above "Screen1"
    Screen      3  "Screen3" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
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
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     50.0 - 63.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor2"
    VendorName     "Unknown"
    ModelName      "Mitsubishi RDT178S"
    HorizSync       31.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     50.0 - 63.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor3"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     50.0 - 63.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device3"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen3"
    Device         "Device3"
    Monitor        "Monitor3"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by awells527 on 2011-01-15
Thank you everyone for the advise.

@heldal I did downgrade the packages and then upgraded the packages to 7.3 with no luck.

@tjones00 I have tried Xinerama but compiz cannot be enabled and causes other issues with other applications like MythTV.

This is absolutely unbelievable how difficult something as simple as multi-display setups are.  I have spent a solid week on getting this to work and I have still been unsuccessful.  *sigh*

I really do appreciate the help though.

EDIT - more information...

I really think I'm dealing with a bug in Xorg or the nVidia driver.  If I enable one card at a time, TwinView works as expected.  It's only when both cards are active at once is when I see problems.

---

### Post by awells527 on 2011-01-15
To further drive the point...here is my simplest xorg.conf file that I have been working with: [http://ubuntu.pastebin.com/ayDTT9kB](http://ubuntu.pastebin.com/ayDTT9kB)

Running it as is will load my primary card, and it will load perfectly with the screen separated and windows move freely between the two.  Uncommenting line 4 will activate the second card, and that causes both pair of screens to turn on but fail to divide properly.  Both pairs operate as a single screen which is unusable.  Because I leave the rest of the configuration the same, it seems to be a different problem - probably with the driver.

---

### Post by BicyclerBoy on 2011-01-15
My suspicion is that it is confusing your monitor names across the 2 video cards.
Twinview makes 1 screen out of two monitors by using a metamode.

According to X11R6/Xorg docs..
I would think you still need 4 monitor sections.

Maybe you need 4 monitor sections & two monitors listed in each screen section.

Another way would be sli mosaic but the GPUs must be same.
Another possible way is dynamic twinview metamodes.

Need to study the X11R6/Xorg docs & nvidia release notes more..
[http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/README/installationandconfiguration.html](http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/README/installationandconfiguration.html)

---

### Post by BicyclerBoy on 2011-01-15
From a quick read of the X11R6/Xorg docs

Why do you have screen 0 listed in both device sections ? ( use (1) in one of them)

I think you need two (2)  server layout sections ( & not 2 monitors per screen).
Call them different names, have one screen in each for twinview. Use screen 0 & screen 1

4 monitor sections 0 - 3.

Screen1 is the "primary" monitor of 2nd GPU. monitor 2

Twinview may make the two meta screens from this.
Server layout0 == twinview-Screen 0 == [monitor 0 & 1]
twinview-Screen 1 == [monitor 2 & 3]


High hopes but not likely is it...

---

### Post by tjones00 on 2011-01-15
What type of Xinerama issues do you get for MythTV?

If you're running Mythtv on one of the displays wouldn't you want that display as a separate X session anyway? So you have better control over the frequency/picture quality/etc?

As for compiz yeah it breaks desktop effects but I can live without a spinny cube desktop jiggly windows and flaming text :o

---

### Post by awells527 on 2011-01-17
> **tjones00 said:**
> What type of Xinerama issues do you get for MythTV?

If you're running Mythtv on one of the displays wouldn't you want that display as a separate X session anyway? So you have better control over the frequency/picture quality/etc?

As for compiz yeah it breaks desktop effects but I can live without a spinny cube desktop jiggly windows and flaming text :o

Yes...ideally I wanted screens 1-3 joined and screen 4 (my TV) on a separate X session.  Once I learned I can't span desktops across two cards with TwinView, I decided to try to join 1-2 and have 3 & 4 separate.  I was going to use 1-2 for my main usage, #3 for my XP VM, and #4 for MythTV.  So, I would only want to move windows between 1 and 2.

With regards to compiz, maybe I *want* a spinny cube desktop jiggly windows and flaming text :).  I don't have my desktop setup like those Compiz demos out there, but I do use productive features like desktop zoom, window previews, and basically other things you see on Win7 by default.  I also had some gnome-panel issues with Xinerama running - the icons with transparency would show a white background.

> **BicyclerBoy said:**
> My suspicion is that it is confusing your monitor names across the 2 video cards.
Twinview makes 1 screen out of two monitors by using a metamode.

According to X11R6/Xorg docs..
I would think you still need 4 monitor sections.

Maybe you need 4 monitor sections & two monitors listed in each screen section.

Another way would be sli mosaic but the GPUs must be same.
Another possible way is dynamic twinview metamodes.

Need to study the X11R6/Xorg docs & nvidia release notes more..
[http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/README/installationandconfiguration.html](http://us.download.nvidia.com/XFree86/Linux-x86/260.19.29/README/installationandconfiguration.html)

If I have 4 monitor sections with TwinView, Xorg throws warnings stating that I need to have MetaModes defined.  Since MetaModes describes two screens, they have to go in the same screen section AFAIK.

> **BicyclerBoy said:**
> From a quick read of the X11R6/Xorg docs

Why do you have screen 0 listed in both device sections ? ( use (1) in one of them)

I think you need two (2)  server layout sections ( & not 2 monitors per screen).
Call them different names, have one screen in each for twinview. Use screen 0 & screen 1

4 monitor sections 0 - 3.

Screen1 is the "primary" monitor of 2nd GPU. monitor 2

Twinview may make the two meta screens from this.
Server layout0 == twinview-Screen 0 == [monitor 0 & 1]
twinview-Screen 1 == [monitor 2 & 3]


High hopes but not likely is it...

The Screen 0 line was a leftover from a previous Xorg.conf I was working on - it shouldn't have been there, but taking it out didn't change anything.

The xorg.conf man page does not indicate multiple server layouts at the same time.  Multiple can be specified, but only to quickly change from one to another by calling xorg with a --serverlayout flag.


I was thinking that maybe I may have better luck if I tried identical graphics cards.  For now, I am sticking with 4 separate X sessions - I need to actually get some work done this week :).  I will watch eBay for a used XFX GeForce 8600 GTS (the less expensive of my two cards), and see if that will change how they work together.

Any other suggestions in the meantime would be appreciated and a sincere thank you to everyone that has provided advice.

---

### Post by BicyclerBoy on 2011-01-17
Xorg docs are in a bygone era.

Nvidia, & I guess ATI, have added all sorts of tricks & work-arounds.

One server section agrees with Xorg.
Two screen sections each with one dual-screen meta-mode.
4 monitor sections.

Problem I see is that the nvidia driver release notes do not explain the display enumeration across two video cards.
It does not explain twinview across 2 video cards.

Each wired port has a fixed name like CRT-0 DVI-1 etc but the documentation does not explain or allow a GPU(device) hierarchal naming convention.
Would the 2nd card wired ports be CRT-3 & DVI-4 for example ?

From reading in the nv forums, the nouveau driver does this multi-monitor & hot plugging so much better.
Is the 3d Gallium driver usable ?

---

### Post by heldal on 2011-01-18
> **tjones00 said:**
> If you're running Mythtv on one of the displays wouldn't you want that display as a separate X session anyway? So you have better control over the frequency/picture quality/etc?

These settings should be adjustable for each screen individually (separate monitor configs in xorg.conf) regardless of the use of separate screens, xinerama or twinview. Mythfrontend works fine in such a config. XBMC otoh insists on treating twinview as one big display in its fullscreen mode.

---

### Post by awells527 on 2011-01-18
> **BicyclerBoy said:**
> 
From reading in the nv forums, the nouveau driver does this multi-monitor & hot plugging so much better.
Is the 3d Gallium driver usable ?

Yes, but the driver doesn't seem to be compatible with my GeForce GTS 450.

---

### Post by BicyclerBoy on 2011-01-21
Have you seen the nv forums threads about fake xinerama ?

---

### Post by awells527 on 2011-01-21
> **BicyclerBoy said:**
> Have you seen the nv forums threads about fake xinerama ?

I did experiment with it briefly, but it seems to function the same as regular Xinerama - disabling Compiz with no hardware acceleration.

Right not I have Xinerama enabled while I wait for a deal on matching one of my video cards so I can try two identical GPUs.

---

### Post by awells527 on 2011-01-25
Just for kicks, I tried two identical cards.  I removed my two original cards, and inserted two GeForce 6600 cards.  All the previous issues were repeatable, so the GPU mismatch didn't seem to be the problem.

---

### Post by your imaginary friend on 2011-01-26
I'm having the same problem with the same setup in ubuntu 10.10:

GPU0: geforce gts 450 driving two lcd monitors
GPU1: geforce 9800 GT driving a third monitor and my tv

each pair of displays is twinviewed, with each card running a separate xscreen.

twinview works fine with each card individually, but as noted by awells527, when both are active it doesn't respect the screen boundaries when maximizing (including fullscreen VMs), stretches wallpaper across both screens, and everything tends to open in the middle of the desktop, thereby spanning both monitors.

xinerama isn't an option because without compiz, avant window navigator (among other things) breaks/becomes so hideous to look at.

I too have been searching for a solution and have yet to come across one.  At this point it's just a frequent annoyance -- but it works automagically in windows so that makes me sad :(

---

### Post by awells527 on 2011-01-26
> **your imaginary friend said:**
> I'm having the same problem with the same setup in ubuntu 10.10:

GPU0: geforce gts 450 driving two lcd monitors
GPU1: geforce 9800 GT driving a third monitor and my tv

each pair of displays is twinviewed, with each card running a separate xscreen.

twinview works fine with each card individually, but as noted by awells527, when both are active it doesn't respect the screen boundaries when maximizing (including fullscreen VMs), stretches wallpaper across both screens, and everything tends to open in the middle of the desktop, thereby spanning both monitors.

xinerama isn't an option because without compiz, avant window navigator (among other things) breaks/becomes so hideous to look at.


At least I know I'm not crazy. :)  That's pretty much my exact setup.

---

### Post by your imaginary friend on 2011-05-07
Well...I installed natty and after multiple failed boot attempts after install, I managed to get in with no graphics.  I needed to update the nvidia driver and reboot and things were happy...ish.

Primary graphics card works fine with two monitors attached -- unity is happy except for the maximization issue mentioned in this thread.

However, desktop on the second graphics card doesn't have a menu bar (so all of the global menus from all programs and windows fail to load/appear).  In addition, keyboard input doesn't work on this desktop, nor do some mouse commands.  All in all, natty/unity is half-FAIL atm with two graphics cards.

---

### Post by shid007 on 2011-06-14
I had a similar problem... I found out that it was caused by RandR ... I had this problem on  really rusty version of RHEL, but I guess it doesn't matter 

In an ancient KRandR control panel, I've found one tab, that was about multiple monitors and it had one option that concerned about windows maximization ... at first it sounded like exact oposite, but I was really desperate so I tried it and ... voila ...:D IT WORKED:D

---

### Post by bcschmerker on 2011-06-16
Thanks for a heads up on a specific complication that may slow down a [project for which I am fielding recommendations](http://ubuntuforums.org/showthread.php?t=1776921) (none received as of 15 June 2011).  I am currently testing a recently-rebuilt [eMachines®/Acer® EL1210-09](http://www.emachines.com/) ([Advance Micro Devices® Athlon 64® LE-1620](http://www.amd.com/) (Socket AM2, 45*max*W), [nVIDIA® MCP78S chipset/GeForce® 8200 IGP](http://www.nvidia.com/)) under 10.04.2-LTS Lucid, AMD64 Edition, intending to set it up as a projector-ready rig for [Sun® OpenOffice.org](http://www.openoffice.org/) with independent video feeds from one or two GPU's.  A problem affecting nVIDIA® TwinView™ could potentially trip up my project, as well.

---

