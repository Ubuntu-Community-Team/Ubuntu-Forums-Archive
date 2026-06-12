---
title: "Ubuntu 7.10 Screen Resolution wrong Dell s2409w 1920x1080 @ 60Hz"
date: 2008-08-18
forum: Multimedia Software
---

### Post by HiFiJive on 2008-08-18
I have an issue regarding my new Dell s2409w 24" widescreen monitor. I have tried adding custom `gtf 1920 1080 60` modelines in my xorg.conf. I have tried using `nvidia-settings`... not tried so many things im not sure where to go next. Any help would be GREATLY appreciated.

---

### Post by DjMojoRisin69 on 2008-09-29
Hi,

I am having the same issue with my Dell S2409W monitor as well.
Any help would be appreciated.

Thanks!

---

### Post by cariboo on 2008-09-30
Have you tried in a terminal displayconfig-gtk, this should detect your display properly and set up the correct modlines in /etc/X11/xorg.conf. in a terminal type:

```
displayconfig-gtk
```

I didn't notice you weren't running hardy so this probably won't work.

Jim

---

### Post by wolfen69 on 2008-09-30
try
```
sudo dpkg-reconfigure -phigh xserver-xorg
```then restart x or reboot.

---

### Post by DjMojoRisin69 on 2008-09-30
Hi,

Wolfen69:
I tried what you suggested, but it converted my resolution to 800x600 and it also disabled my nvidia video card driver.

Cariboo907:
I am actually running Hardy, and when I run that command I get a selection of screens to pick from, should I just pick the Generic type for my screen, and see if the correct mod lines are put in?

Thanks!

Any other suggestions?

---

### Post by bufsabre666 on 2008-09-30
have you tried running nvidia-settings as root? that worked for me when my laptop didnt want to display at 1280 x 800

---

### Post by DjMojoRisin69 on 2008-09-30
Yes. I have tried running nvdia-settings as root, and it will only let me max my resolution out at 1280x1024.

The max that the monitor supports is 1920x1080, and I tried this out and I get that resolution in Windows.

Thanks!

---

### Post by cariboo on 2008-09-30
When you run displayconfig-gtk, if you monitor isn't listed use the generic choice. I would suggest you backup your /etc/X11/xorg.conf file before making any changes, just in case you don't get the expected results.

Jim

---

### Post by DjMojoRisin69 on 2008-10-01
So I have tried out these methods, and I am still not able to get the max resolution set on my monitor. The highest resolution I can get is 1280x1024. I have also tried getting the latest NVidia drivers and re-installing them, and that did not help either.

I also looked at adding modelines to the xorg.conf with no luck.

I am starting to think that there is something wrong with the way the Nvidia driver is being installed? Or that the Monitor is not supported correctly w/ the drivers yet?

Any ideas anyone?

Thanks!

---

### Post by dancavs on 2008-10-01
hi i just did a new install of 8.04 last night and managed to get native res (1920x1080) for a dell 2408wfp ultrasharp.

the how to i followed is: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

cheers

---

### Post by DjMojoRisin69 on 2008-10-02
No Luck :(  Do you think that it might have to do with the fact that I upgraded from Fiesty to Hardy? 

A fresh install of Hardy might do the trick?

---

### Post by dancavs on 2008-10-02
hi what is the model of your nvidia graphics card? need to work out first if youve installed the correct driver.

have you tried editing manually your /etc/X11/xorg.conf file? nvidia cards apparently have a torrid time determining a displays native resolution. 

the info you need is the horizontal and vertical refresh rates of your display, and the different resolutions that it is capable of displaying in. your display's documentation should have this info. 

editing the xorg.conf file is covered in: 

[https://help.ubuntu.com/community/Fi...esolutionHowto](https://help.ubuntu.com/community/Fi...esolutionHowto)

unsure whether your upgrade could have caused this ... did you have your native resolution ok in feisty? apparently if you manually install your nvidia driver a kernel upgrade can cause problems. if this is so you may need to reinstall your graphics card driver.

cheers m8

---

### Post by DjMojoRisin69 on 2008-10-06
So, I was finally able to resolve this issue. It seems that something got messed up when I upgrade from Fiesty to Hardy, so when I did a fresh install of Hardy I was able to get the max resolution(1920x1080) on my screen by default :)
All off the default screen resolutions are now  availible in the Screen Resolution menu in Gnome.

Thanks for all your help everyone!

---

### Post by Crick on 2008-10-10
I got this to work last night. Not sure how exactly, because when I booted it up this morning it worked. Note that I am running an old nvidia geforce4 MX 420 card. I found the latest legacy drivers and installed those, but I think it was due to me fiddling around with xorg.conf after googling for 1080p s2409w and reading forum posts.

Note also that running nvidia-settings didn't help because it only listed 1920x1200.

Relevant part of my xorg.conf is as follows:
```
Section "Monitor"
    Identifier "monitor1"
    VendorName "Dell"
    ModelName "s2409w"
    HorizSync 15.0 - 65.0
    VertRefresh 50.0 - 75.0
    Option "DPMS"
EndSection

Section "Device"
    Identifier "device1"
    VendorName "nVidia Corp."
    BoardName "NVIDIA GeForce4 (generic)"
    Driver "nvidia"
    Option "DPMS" "false"
EndSection

Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 16
    Option "AddARGBGLXVisuals"
Option "ModeValidation" "NoMaxPClkCheck, AllowNon60HzDFPModes, NoVesaModes, NoXServerModes, NoPredefinedModes"
Option "ModeValidation" "NoEdidDFPMaxSizeCheck"
Option "ModeValidation" "NoDFPNativeResolutionCheck
#    Option "UseEdidFreqs" "false"
    Subsection "Display"
        Depth 16
        Modes "1920x1080"
    EndSubsection
EndSection

```

---

