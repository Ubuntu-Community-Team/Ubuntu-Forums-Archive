---
title: "Still Can't Change the Resolution"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by dagr8tim on 2006-06-11
I've been lurking the forums/web articles/IRC channel for the past few days and I still cannot change my resolution from 640x480.  When I was running 5.10, I know I had a large resolution, so I'm wondering what changed in the realm of video between the two versions.

Below is the section of my xorg.conf that deals with the monitor.  From what I've read it *should* allow me to choose another resolution. 

```
Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Matrox Graphics, Inc. MGA 2064W [Millennium]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

Does anyone have any other suggestions?  I'm at a loss.  :confused: :confused: :confused:

---

### Post by Jason_25 on 2006-06-11
Post your full xorg.conf, and optionally, your Xorg.0.log.  You don't happen to have a tv connector plugged in do you?

---

### Post by dagr8tim on 2006-06-11
This is a old PII400 with no frills.  Currently I am booted from a 5.10 live CD.  This gives me the ability to have more than 640x480.  I'll try and post that whole file later when I am booted from 6.06.

Below is that same section of the xorg.conf from my 5.10 live CD session.
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Matrox Graphics, Inc. MGA 2064W [Millennium]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```

---

### Post by samandiriel on 2006-06-11
I was tearing my hair out with similar probs.  For whatever reason, it won't run with a color depth of 24 (tho it will in WinXP?).  I switched it to 16 just to giggles, and voila! I had a decent resolution.  Along with some EXTREMELY strange ones that appeard from nowhere - things like 832x624 and the like.  Weird, but whatever.  Now to get BOTH my video cards to work and have both monitors up again...

Tyler 
tyler (dot) style 
AT
gmail

---

### Post by BaffledMollusc on 2006-06-11
[QUOTE=Jason_25]Post your full xorg.conf, and optionally, your Xorg.0.log.  You don't happen to have a tv connector plugged in do you?[/QUOTE]
I was also stuck at 640x480, and the only way I got out of it was to install the proprietory ATI fglrx driver (which has its own problems, the original poster doesn't have an ATI card anyway).

I do have a (PCI) TV card plugged into my computer, however. It never occurred to me that this might be causing the problem... Can you explain whether this might screw around with the resolution?

---

### Post by Jason_25 on 2006-06-12
[QUOTE=BaffledMollusc]I was also stuck at 640x480, and the only way I got out of it was to install the proprietory ATI fglrx driver (which has its own problems, the original poster doesn't have an ATI card anyway).

I do have a (PCI) TV card plugged into my computer, however. It never occurred to me that this might be causing the problem... Can you explain whether this might screw around with the resolution?[/QUOTE]
That wouldn't cause a problem.  But sometimes having tv-out plugged in on the video card itself will cause x to choose a low resolution.

---

### Post by n00bWillingToLearn on 2006-07-16
> **dagr8tim said:**
> This is a old PII400 with no frills.  Currently I am booted from a 5.10 live CD.  This gives me the ability to have more than 640x480.  I'll try and post that whole file later when I am booted from 6.06.

Below is that same section of the xorg.conf from my 5.10 live CD session.
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Matrox Graphics, Inc. MGA 2064W [Millennium]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```
It's a little late for a reply but the section monitor is actaully the important one and if you copy that into your dapper xorg.conf you should be able to get any supported resolution WITH 24 bit color.

---

