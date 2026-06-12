---
title: "How to add resolution for external monitor?"
date: 2009-01-11
forum: Multimedia Software
---

### Post by drwillis on 2009-01-11
Hi everyone! First of all I want to say that I'm a novice Ubuntu user but so far (1 week more ore less) I really like what Ubuntu has to offer.

To my problem.. When I connect my external tft monitor to my IBM Lenova thinkpad T60 laptop the resolution is the same as the laptop resolution (1400x1050 which is also max). But I want to have 1680x1050 widescreen for my external monitor and 1400x1050 for my laptop. As far as driver I use the FGLRX driver for my ATI Radeon Mobility X1300 graphic card. In ATI Catalyst Control Center it detects both my laptop screen and my external monitor which is an Samsung SyncMaster 2233DW 22'. And when I choose detect displays the laptop screen shows an 1 and the external monitor an 2, so it shows that they use different settings right? But I can't choose a resolution higher then 1400x1050 for my external monitor! Why is this? And how can I add a resolution to my external monitor?


**Q:How can I add 1680x1050 widescreen resolution for my Samsung SyncMaster 2233DW monitor?**

Thanks in advance!

Best Regards
Dr.Willis

---

### Post by drwillis on 2009-01-17
bump..doesn't anyone know?

---

### Post by samat on 2009-01-23
up!

Have the same question! :)
Help, please.

---

### Post by juveduke on 2009-01-24
Make sure you have your maximum total resolution in the virtual field of the screen section of your xorg.conf.

The "Screen" section of /etc/X11/xorg.conf should like something like this (for your stated resolutions):
```

Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
    SubSection "Display"
        Virtual 3080 1050
    EndSubSection
EndSection

```

Log out and log back in and hopefully your desired resolution will be available.  I'm running 1280x800 on my laptop and 1680x1050 on my external.  It seems like I always have to tinker with it a bit after rebooting, but after that it works fine.

---

### Post by bosworthy on 2009-01-24
I have the same problem, but don't see any xorg.conf as you've put it.

---

### Post by juveduke on 2009-01-24
> **bosworthy said:**
> I have the same problem, but don't see any xorg.conf as you've put it.

oops, should be /etc/X11/xorg.conf

fixed original post.

---

