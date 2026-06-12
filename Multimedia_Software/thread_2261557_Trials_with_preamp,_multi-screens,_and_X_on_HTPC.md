---
title: "Trials with preamp, multi-screens, and X on HTPC"
date: 2015-01-19
forum: Multimedia Software
---

### Post by milesnorth on 2015-01-19
Problem with preamp on both Kubuntu and Netrunner HTPC.  Currently trying Netrunner 14 with nvidia-331-updates driver.  No xorg.conf is currently in use.  

Occationally used to be able to switch preamp sound on/off with tv and/or projector on/off and stay at 1080p 60hz.  Usually, though, turning preamp on switched refresh rate down to 30 hz and had to manually reset to 60hz.  Now turning preamp on defoults to 480p 30hz and tv and/or projector goes to a blue screen.  Then have to restart x and relogon to account.

Desired use is DVI monitor always off, use tv as main monitor with pream off or on, turn projector on for large screen events, usually with preamp on, and keep the settings at 1080p 60hz.  Also a happy wife who can watch tv without lessons in restarting X.

Any ideas on how to get a stable default configuation or a stable xorg.conf would be appreciated.

Hardware map:
HTPC -> NVIDIA -> DVI   -> iZ3D
                       ---------------------------                     -> HDMI -> UMC-200 -> splitter -> SEIKI TV
                                                                    ----------------------------------------------------------------                                                                  -> EPSON projector
                  
iZ3D (used for boot only, almost always off)
UMC-200 (preamp with video pass through when off - music stereo dac & tv/movies 5.1 sound)
SEIKI TV (used as main monitor/tv, mirrors UMC-200)
EPSON PJ (used as tv/movie display)

The devices are listed below:

    Driver             "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 650 Ti BOOST"

    ModelName      "Kontron UMC-200"
    HorizSync         14.0 - 68.0
    VertRefresh       48.0 - 62.0

    ModelName      "Chi Mei Optoelectronics corp. iZ3D Back"
    HorizSync         30.0 - 82.0
    VertRefresh       56.0 - 76.0

    ModelName      "SEK LC-46G68"
    HorizSync         14.0 - 68.0
    VertRefresh       48.0 - 62.0

    ModelName      "Seiko/Epson EPSON PJ"
    HorizSync         15.0 - 92.0
    VertRefresh       24.0 - 85.0

---

### Post by milesnorth on 2015-01-25
Lets shorten the question to - why does turning on the preamp send the system to a blue screen with a 480p 30hz signal that neither the tv nor projector can process?  It doesn't matter what's in settings - display, or settings - other - display configuration (kscreen?), or xorg.conf or no xorg.conf.  When the preamp goes on, all the screens go blue and I have to restart X.

What controls the display/screen manager, how do you configure it, how do you override it?  I'm clueless.  Is this an Àlex Fiestas or Dan Vrátil with ksreen development question?

---

