---
title: "Proper resolution, but top of screen is flashing"
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by virtualcourtney on 2006-06-07
Hi all.  I'm new to linux (played with suse a few days before dapper LTS came out), and I've figured out a lot of my problems by browsing the forums, but I can't find anything to address this one.

I'm using an Nvidia GeForce FX Go5200 with driver version 1.0-8762, and I managed to get my custom resolution (1280x854 -- weird, I know).  The thing is, the top of my screen shifts up and down a pixel or two at a pretty frantic rate.  I have no clue what could be causing this--I've played with the vertical refresh value in xorg.conf to no avail.  I installed kubuntu-desktop to see if there was a difference there, but nothing.

Here's what I've got in xorg.conf related to the monitor and video card (the current values for "HorizSync" and "VertRefresh" are what I pulled from my XP partition using powerstrip):

```

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       52.007
    VertRefresh     60.054
    Option         "DPMS"
    Modeline       "1280x854@60" 90.93 1280 1312 1656 1688 854 871 880 897
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34M [GeForce FX Go5200]"
    Driver         "nvidia"
    Option         "DPI" "100x100"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34M [GeForce FX Go5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x854"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x854"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x854"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x854"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x854"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x854"
    EndSubSection
EndSection


```

I guess my questions are these: has anyone else run into this?  And what should I even start playing with to address the problem?  I mean, as long as I don't look at the top of my screen, this is a manageable problem.  But when I do look up there, I feel a little bit like I'm at a disco. :shock:

---

