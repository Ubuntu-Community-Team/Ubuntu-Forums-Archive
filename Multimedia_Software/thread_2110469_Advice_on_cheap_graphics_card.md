---
title: "Advice on cheap graphics card"
date: 2013-01-30
forum: Multimedia Software
---

### Post by Acharn on 2013-01-30
Not sure if this is the right forum to be asking this question on, or if it would be better over at the Absolute Beginners forum.

I'm currently running Ubuntu 12.04 on an Acer Aspire M-1610 desktop machine which has 1GB RAM, a dual core Intel CPU running at 1.8GHz, and an AMD Radeon x1550 graphics card. I have a 19" Acer monitor and use a resolution of 1440x900. I do know that the graphics card slot is PCI Express compatible. I got some troubling error messages one day from compiz, the program that basically runs the Unity desktop, and was planning to upgrade to 12.10, when I discovered AMD has dropped support for the Linux version of this driver, the open source driver (which is what I've been using) won't support higher resolutions under 12.10 (because of a new release from X.Org) and things are likely to get worse in the near future. I was finally able to boot from a live USB stick and the display is usable but not very nice. I think I would get eye-strain pretty quickly. Buying a newer computer is at least a year and a half away (this one is five years old, can't help it), but I could afford a new graphics card in the $100-110 price range. Next month, after I get my income tax refund.

I've found a helpful list at Tom's Hardware, and the AMD HD6670 looks like just what I need, but who knows how long AMD will support this card. For Nvidia a flyer from a local computer shop lists a GT440 2GB and a GT8450 w/1GB at a slightly higher price. From remarks I've read, I think the Nvidia is more likely to work well with Linux, but there may be a reason Acer chose the AMD card with this motherboard. I'm not into gaming much, certainly not new graphics-intensive games. Anybody have any recommendations?

---

### Post by Yellow Pasque on 2013-01-30
> the open source driver (which is what I've been using) won't support higher resolutions under 12.10 (because of a new release from X.Org)

That doesn't sound right. Source/Citation?

---

### Post by Mark Phelps on 2013-01-30
I'm using the open source Radeon driver under 12.10 and have the same high resolutions as I did under 12.04.  But, I'm not using the same video chipset -- and that could be the limitation.

I would boot using a 12.10 version, use the LiveCD (or LiveUSB) mode and see what resolutions the open-source driver offers.

---

### Post by oldfred on 2013-01-30
I like the Tom's list to compared video cards.

But if system is older, you need to check on power supply. Almost all new video cards need lots of power and most older systems especially the pre-built one's had limited power available.

---

### Post by Acharn on 2013-01-31
> [quote]
the open source driver (which is what I've been using) won't support higher resolutions under 12.10 (because of a new release from X.Org)

That doesn't sound right. Source/Citation?
[/quote]

The thread at [http://ubuntuforums.org/showpost.php?p=12361480&postcount=13](http://ubuntuforums.org/showpost.php?p=12361480&postcount=13)

I seem to remember a slightly longer statement to the same effect, giving a list of the AMD chipsets which will no longer work with the new version of the X Server, but can't find it in my browsing history.

---

### Post by Acharn on 2013-01-31
> **Mark Phelps said:**
> I'm using the open source Radeon driver under 12.10 and have the same high resolutions as I did under 12.04.  But, I'm not using the same video chipset -- and that could be the limitation.

I would boot using a 12.10 version, use the LiveCD (or LiveUSB) mode and see what resolutions the open-source driver offers.

Yes, the problem is with older AMD graphics chipsets. Newer ones are supposed to be OK. I thought I saw a post which listed all the chipsets which are not supported at higher resolutions any more, but I haven't been able to find it again. There were a lot of chips involved. The author pointed out that the guys who maintain the open source drivers are handicapped because the proprietary drivers are closed source and ATI/AMD has not been helpful over the years. That's one reason I would kind of like to switch to Nvidia, but am not sure if there might be motherboard compatibility issues. By the way, this is caused by X.Org upgrading their X Server, it's not a reflection on the Ubuntu team. The same problem is going to hit every Linux distro.

I was able to boot from a live USB stick and the graphics options were very limited, I believe three, including 640x400. the best was, IIRC, 1024x768. None of them had quite the right aspect ratio and the only display was identified as LAPTOP. In 12.04 I use 1440x900 but have many possibilities.

---

### Post by Acharn on 2013-01-31
> **oldfred said:**
> I like the Tom's list to compared video cards.

But if system is older, you need to check on power supply. Almost all new video cards need lots of power and most older systems especially the pre-built one's had limited power available.

Oh, thanks for the heads up. I hadn't even thought of that, but I'm pretty sure the power supply is adequate. Let's see, where did I put those spec sheets...?

---

### Post by Yellow Pasque on 2013-01-31
That post you linked to only applies to proprietary drivers and is irrelevant here (unless you tried to install the proprietary driver and borked your system). Post your /var/log/Xorg.0.log

---

### Post by Acharn on 2013-01-31
> **Temüjin said:**
> That post you linked to only applies to proprietary drivers and is irrelevant here (unless you tried to install the proprietary driver and borked your system). Post your /var/log/Xorg.0.log

Well, here's the result of 'cat /var/log/Xorg.0.log', pretty long:
```

[    15.859] (II) This device may have been added with another device file.
[    15.860] (II) config/udev: Adding input device HDA SIS966 Line (/dev/input/event4)
[    15.860] (II) No input driver specified, ignoring this device.
[    15.860] (II) This device may have been added with another device file.
[    15.860] (II) config/udev: Adding input device HDA SIS966 Front Mic (/dev/input/event5)
[    15.860] (II) No input driver specified, ignoring this device.
[    15.860] (II) This device may have been added with another device file.
[    15.861] (II) config/udev: Adding input device HDA SIS966 Rear Mic (/dev/input/event6)
[    15.861] (II) No input driver specified, ignoring this device.
[    15.861] (II) This device may have been added with another device file.
[    15.861] (II) config/udev: Adding input device HDA SIS966 Front Headphone (/dev/input/event7)
[    15.861] (II) No input driver specified, ignoring this device.
[    15.862] (II) This device may have been added with another device file.
[    15.862] (II) config/udev: Adding input device HDA SIS966 Line Out Side (/dev/input/event8)
[    15.862] (II) No input driver specified, ignoring this device.
[    15.862] (II) This device may have been added with another device file.
[    15.862] (II) config/udev: Adding input device HDA SIS966 Line Out CLFE (/dev/input/event9)
[    15.862] (II) No input driver specified, ignoring this device.
[    15.862] (II) This device may have been added with another device file.
[    15.863] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event12)
[    15.863] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    15.863] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    15.863] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    15.863] (**) evdev: ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event12"
[    15.863] (--) evdev: ImPS/2 Generic Wheel Mouse: Vendor 0x2 Product 0x5
[    15.863] (--) evdev: ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    15.863] (--) evdev: ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    15.863] (--) evdev: ImPS/2 Generic Wheel Mouse: Found relative axes
[    15.863] (--) evdev: ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    15.863] (II) evdev: ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    15.863] (II) evdev: ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    15.863] (**) evdev: ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    15.863] (**) evdev: ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.863] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input12/event12"
[    15.863] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE, id 10)
[    15.863] (II) evdev: ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    15.863] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    15.863] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    15.863] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    15.863] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    15.864] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    15.864] (II) No input driver specified, ignoring this device.
[    15.864] (II) This device may have been added with another device file.
[    16.638] (II) RADEON(0): EDID vendor "ACR", prod id 44416
[    16.638] (II) RADEON(0): Using hsync ranges from config file
[    16.638] (II) RADEON(0): Using vrefresh ranges from config file
[    16.638] (II) RADEON(0): Printing DDC gathered Modelines:
[    16.638] (II) RADEON(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz e)
[    16.638] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    16.638] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    16.638] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    16.638] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    16.638] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    16.638] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    16.638] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    16.638] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    16.638] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    16.638] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    16.638] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    16.638] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    16.638] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    16.638] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    16.638] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    16.638] (II) RADEON(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[    16.638] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    16.638] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    16.638] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    16.638] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[    16.638] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    16.638] (II) RADEON(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz e)
[    19.533] (II) RADEON(0): EDID vendor "ACR", prod id 44416
[    19.533] (II) RADEON(0): Using hsync ranges from config file
[    19.533] (II) RADEON(0): Using vrefresh ranges from config file
[    19.533] (II) RADEON(0): Printing DDC gathered Modelines:
[    19.533] (II) RADEON(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz e)
[    19.533] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    19.533] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    19.533] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    19.533] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    19.533] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    19.533] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    19.533] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    19.533] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    19.533] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    19.533] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    19.533] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    19.533] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    19.533] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    19.533] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    19.533] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    19.533] (II) RADEON(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[    19.533] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    19.533] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    19.533] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    19.533] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[    19.533] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    19.533] (II) RADEON(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz e)
[    41.067] (II) RADEON(0): EDID vendor "ACR", prod id 44416
[    41.067] (II) RADEON(0): Using hsync ranges from config file
[    41.067] (II) RADEON(0): Using vrefresh ranges from config file
[    41.067] (II) RADEON(0): Printing DDC gathered Modelines:
[    41.067] (II) RADEON(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz e)
[    41.067] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    41.067] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    41.067] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    41.067] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    41.067] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    41.067] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    41.067] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    41.067] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    41.067] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    41.067] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    41.067] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    41.067] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    41.067] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    41.067] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    41.067] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    41.067] (II) RADEON(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[    41.067] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    41.067] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    41.067] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    41.068] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[    41.068] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    41.068] (II) RADEON(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz e)
[    42.815] (II) RADEON(0): EDID vendor "ACR", prod id 44416
[    42.815] (II) RADEON(0): Using hsync ranges from config file
[    42.815] (II) RADEON(0): Using vrefresh ranges from config file
[    42.815] (II) RADEON(0): Printing DDC gathered Modelines:
[    42.815] (II) RADEON(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz e)
[    42.815] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    42.815] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    42.815] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    42.815] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    42.815] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    42.815] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    42.815] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    42.815] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    42.815] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    42.815] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    42.815] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    42.815] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    42.815] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    42.815] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    42.815] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    42.815] (II) RADEON(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[    42.815] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    42.815] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    42.815] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    42.815] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[    42.815] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    42.815] (II) RADEON(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz e)
[    44.836] (II) RADEON(0): EDID vendor "ACR", prod id 44416
[    44.836] (II) RADEON(0): Using hsync ranges from config file
[    44.836] (II) RADEON(0): Using vrefresh ranges from config file
[    44.836] (II) RADEON(0): Printing DDC gathered Modelines:
[    44.836] (II) RADEON(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz e)
[    44.836] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    44.836] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    44.836] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    44.836] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    44.836] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    44.836] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    44.836] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    44.836] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    44.836] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    44.836] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    44.836] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    44.836] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    44.836] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    44.836] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    44.836] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    44.836] (II) RADEON(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[    44.836] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    44.836] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    44.836] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    44.836] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[    44.836] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    44.836] (II) RADEON(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz e)
[    65.187] (II) RADEON(0): EDID vendor "ACR", prod id 44416
[    65.187] (II) RADEON(0): Using hsync ranges from config file
[    65.187] (II) RADEON(0): Using vrefresh ranges from config file
[    65.187] (II) RADEON(0): Printing DDC gathered Modelines:
[    65.187] (II) RADEON(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz e)
[    65.187] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    65.187] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    65.187] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    65.187] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    65.187] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    65.187] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    65.187] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    65.187] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    65.187] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    65.187] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    65.187] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    65.187] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    65.187] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    65.187] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    65.187] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    65.187] (II) RADEON(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[    65.187] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    65.187] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    65.187] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    65.187] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[    65.187] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    65.187] (II) RADEON(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz e)
[    74.909] (II) XKB: reuse xkmfile /var/lib/xkb/server-518754FAB1FA320CD11E67E5F27005732682D4B3.xkm
[  8871.456] (II) RADEON(0): EDID vendor "ACR", prod id 44416
[  8871.517] (II) RADEON(0): Using hsync ranges from config file
[  8871.517] (II) RADEON(0): Using vrefresh ranges from config file
[  8871.517] (II) RADEON(0): Printing DDC gathered Modelines:
[  8871.517] (II) RADEON(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz e)
[  8871.517] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  8871.517] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  8871.517] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  8871.517] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  8871.517] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  8871.517] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  8871.517] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  8871.517] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  8871.517] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  8871.517] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  8871.517] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  8871.517] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  8871.517] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  8871.517] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  8871.517] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  8871.517] (II) RADEON(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[  8871.517] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[  8871.517] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  8871.517] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  8871.517] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[  8871.517] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[  8871.517] (II) RADEON(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz e)
[ 27060.208] (II) RADEON(0): EDID vendor "ACR", prod id 44416
[ 27060.294] (II) RADEON(0): Using hsync ranges from config file
[ 27060.294] (II) RADEON(0): Using vrefresh ranges from config file
[ 27060.294] (II) RADEON(0): Printing DDC gathered Modelines:
[ 27060.294] (II) RADEON(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz e)
[ 27060.294] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 27060.294] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[ 27060.294] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 27060.294] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[ 27060.294] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[ 27060.294] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 27060.294] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 27060.294] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 27060.294] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 27060.294] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[ 27060.294] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 27060.294] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[ 27060.294] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 27060.294] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[ 27060.295] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 27060.295] (II) RADEON(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[ 27060.295] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[ 27060.295] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 27060.295] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[ 27060.295] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[ 27060.295] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[ 27060.295] (II) RADEON(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz e)
[ 29254.174] (II) RADEON(0): EDID vendor "ACR", prod id 44416
[ 29254.191] (II) RADEON(0): Using hsync ranges from config file
[ 29254.191] (II) RADEON(0): Using vrefresh ranges from config file
[ 29254.191] (II) RADEON(0): Printing DDC gathered Modelines:
[ 29254.191] (II) RADEON(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 29254.191] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[ 29254.192] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[ 29254.192] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[ 29254.192] (II) RADEON(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz e)

```
It overflowed my terminal's buffer. I think it's probably more than you wanted, but I didn't know where to cut it. I'll try searching some more for the thread which discussed losing support for ATI/AMD chipsets.

---

### Post by Yellow Pasque on 2013-01-31
Actually, I was looking for the whole log. Open it in a text editor instead of using 'cat'.

---

### Post by kurt18947 on 2013-01-31
If you choose to go with a new video card, I have a low end Nvidia -8400GS and SWMBO has a a GT210 (or something like that) both running on AMD Gigabyte MoBo s with integrated ATI/AMD graphics.  I just disabled onboard video and set the PCIe slot as preferred.  Installed the video card, booted, loaded the Nvidia drivers (though the open source drivers aren't bad) and we were both up & running.  No issues though 12.10 Gnome remix seems to prefer the open source driver at times for stability.

---

### Post by Yellow Pasque on 2013-01-31
8400GS is a bit old now. It's still a good card for video playback (have one in the living room PC), but I wouldn't buy one new when I could get a GT440 like OP.

---

### Post by kurt18947 on 2013-01-31
> **Temüjin said:**
> 8400GS is a bit old now. It's still a good card for video playback (have one in the living room PC), but I wouldn't buy one new when I could get a GT440 like OP.

It is, I doubt you can even buy one through normal retail channels.  It still works fine for office-type stuff.  The point I was trying to make is the fact that a board has built-in AMD/ATI video doesn't mean that an Nvidia board won't work.

---

### Post by darkager on 2013-02-01
> **kurt18947 said:**
> It is, I doubt you can even buy one through normal retail channels.  It still works fine for office-type stuff.  The point I was trying to make is the fact that a board has built-in AMD/ATI video doesn't mean that an Nvidia board won't work.

True. The whole purpose of the external graphics processor is to be independent of the motherboard (and its integrated graphics).  Just promptly disable the integrated graphics in the bios.

---

### Post by Acharn on 2013-02-01
> **Temüjin said:**
> Actually, I was looking for the whole log. Open it in a text editor instead of using 'cat'.

OK, here it is:
```

[    15.485] 
X.Org X Server 1.12.3
Release Date: 2012-07-09
[    15.485] X Protocol Version 11, Revision 0
[    15.485] Build Operating System: Linux 2.6.24-31-xen i686 Ubuntu
[    15.485] Current Operating System: Linux roger-Aspire-M1610 3.5.0-10-generic #10-Ubuntu SMP Mon Aug 13 16:35:16 UTC 2012 i686
[    15.485] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-10-generic root=UUID=aa930990-0b62-4bea-971b-6fb5332311cd ro quiet splash vt.handoff=7
[    15.486] Build Date: 09 July 2012  05:18:23PM
[    15.486] xorg-server 2:1.12.3+git20120709+server-1.12-branch.60e0d205-0ubuntu0ricotz~precise (For technical support please see http://www.ubuntu.com/support) 
[    15.486] Current version of pixman: 0.26.0
[    15.486] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    15.486] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    15.486] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb  1 07:11:32 2013
[    15.500] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    15.500] (==) No Layout section.  Using the first Screen section.
[    15.500] (==) No screen section available. Using defaults.
[    15.500] (**) |-->Screen "Default Screen Section" (0)
[    15.500] (**) |   |-->Monitor "<default monitor>"
[    15.501] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    15.501] (==) Automatically adding devices
[    15.501] (==) Automatically enabling devices
[    15.501] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    15.501] 	Entry deleted from font path.
[    15.501] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    15.501] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    15.501] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    15.501] (II) Loader magic: 0xb77775a0
[    15.501] (II) Module ABI versions:
[    15.501] 	X.Org ANSI C Emulation: 0.4
[    15.501] 	X.Org Video Driver: 12.0
[    15.501] 	X.Org XInput driver : 16.0
[    15.501] 	X.Org Server Extension : 6.0
[    15.502] (--) PCI:*(0:1:0:0) 1002:7187:174b:5920 rev 0, Mem @ 0xd0000000/268435456, 0xfdcf0000/65536, I/O @ 0x0000de00/256, BIOS @ 0x????????/131072
[    15.502] (--) PCI: (0:1:0:1) 1002:71a7:174b:5921 rev 0, Mem @ 0xfdce0000/65536
[    15.502] (II) Open ACPI successful (/var/run/acpid.socket)
[    15.502] (II) LoadModule: "extmod"
[    15.533] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    15.533] (II) Module extmod: vendor="X.Org Foundation"
[    15.533] 	compiled for 1.12.3, module version = 1.0.0
[    15.533] 	Module class: X.Org Server Extension
[    15.533] 	ABI class: X.Org Server Extension, version 6.0
[    15.533] (II) Loading extension MIT-SCREEN-SAVER
[    15.533] (II) Loading extension XFree86-VidModeExtension
[    15.533] (II) Loading extension XFree86-DGA
[    15.533] (II) Loading extension DPMS
[    15.533] (II) Loading extension XVideo
[    15.533] (II) Loading extension XVideo-MotionCompensation
[    15.533] (II) Loading extension X-Resource
[    15.533] (II) LoadModule: "dbe"
[    15.534] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    15.534] (II) Module dbe: vendor="X.Org Foundation"
[    15.534] 	compiled for 1.12.3, module version = 1.0.0
[    15.534] 	Module class: X.Org Server Extension
[    15.534] 	ABI class: X.Org Server Extension, version 6.0
[    15.534] (II) Loading extension DOUBLE-BUFFER
[    15.534] (II) LoadModule: "glx"
[    15.534] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    15.534] (II) Module glx: vendor="X.Org Foundation"
[    15.534] 	compiled for 1.12.3, module version = 1.0.0
[    15.534] 	ABI class: X.Org Server Extension, version 6.0
[    15.534] (==) AIGLX enabled
[    15.534] (II) Loading extension GLX
[    15.534] (II) LoadModule: "record"
[    15.535] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    15.535] (II) Module record: vendor="X.Org Foundation"
[    15.535] 	compiled for 1.12.3, module version = 1.13.0
[    15.535] 	Module class: X.Org Server Extension
[    15.535] 	ABI class: X.Org Server Extension, version 6.0
[    15.535] (II) Loading extension RECORD
[    15.535] (II) LoadModule: "dri"
[    15.535] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    15.536] (II) Module dri: vendor="X.Org Foundation"
[    15.536] 	compiled for 1.12.3, module version = 1.0.0
[    15.536] 	ABI class: X.Org Server Extension, version 6.0
[    15.536] (II) Loading extension XFree86-DRI
[    15.536] (II) LoadModule: "dri2"
[    15.536] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.536] (II) Module dri2: vendor="X.Org Foundation"
[    15.536] 	compiled for 1.12.3, module version = 1.2.0
[    15.536] 	ABI class: X.Org Server Extension, version 6.0
[    15.536] (II) Loading extension DRI2
[    15.536] (==) Matched fglrx as autoconfigured driver 0
[    15.536] (==) Matched ati as autoconfigured driver 1
[    15.536] (==) Matched vesa as autoconfigured driver 2
[    15.536] (==) Matched fbdev as autoconfigured driver 3
[    15.536] (==) Assigned the driver to the xf86ConfigLayout
[    15.536] (II) LoadModule: "fglrx"
[    15.537] (WW) Warning, couldn't open module fglrx
[    15.537] (II) UnloadModule: "fglrx"
[    15.537] (II) Unloading fglrx
[    15.537] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    15.537] (II) LoadModule: "ati"
[    15.538] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    15.538] (II) Module ati: vendor="X.Org Foundation"
[    15.538] 	compiled for 1.12.3, module version = 6.99.99
[    15.538] 	Module class: X.Org Video Driver
[    15.538] 	ABI class: X.Org Video Driver, version 12.0
[    15.538] (II) LoadModule: "radeon"
[    15.538] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    15.538] (II) Module radeon: vendor="X.Org Foundation"
[    15.538] 	compiled for 1.12.3, module version = 6.99.99
[    15.538] 	Module class: X.Org Video Driver
[    15.538] 	ABI class: X.Org Video Driver, version 12.0
[    15.538] (II) LoadModule: "vesa"
[    15.539] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.539] (II) Module vesa: vendor="X.Org Foundation"
[    15.539] 	compiled for 1.12.3, module version = 2.3.2
[    15.539] 	Module class: X.Org Video Driver
[    15.539] 	ABI class: X.Org Video Driver, version 12.0
[    15.539] (II) LoadModule: "fbdev"
[    15.539] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.539] (II) Module fbdev: vendor="X.Org Foundation"
[    15.539] 	compiled for 1.12.3, module version = 0.4.3
[    15.539] 	Module class: X.Org Video Driver
[    15.539] 	ABI class: X.Org Video Driver, version 12.0
[    15.539] (==) Matched fglrx as autoconfigured driver 0
[    15.539] (==) Matched ati as autoconfigured driver 1
[    15.539] (==) Matched vesa as autoconfigured driver 2
[    15.539] (==) Matched fbdev as autoconfigured driver 3
[    15.539] (==) Assigned the driver to the xf86ConfigLayout
[    15.539] (II) LoadModule: "fglrx"
[    15.540] (WW) Warning, couldn't open module fglrx
[    15.540] (II) UnloadModule: "fglrx"
[    15.540] (II) Unloading fglrx
[    15.540] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    15.540] (II) LoadModule: "ati"
[    15.540] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    15.540] (II) Module ati: vendor="X.Org Foundation"
[    15.540] 	compiled for 1.12.3, module version = 6.99.99
[    15.540] 	Module class: X.Org Video Driver
[    15.540] 	ABI class: X.Org Video Driver, version 12.0
[    15.540] (II) LoadModule: "vesa"
[    15.541] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    15.541] (II) Module vesa: vendor="X.Org Foundation"
[    15.541] 	compiled for 1.12.3, module version = 2.3.2
[    15.541] 	Module class: X.Org Video Driver
[    15.541] 	ABI class: X.Org Video Driver, version 12.0
[    15.541] (II) UnloadModule: "vesa"
[    15.541] (II) Unloading vesa
[    15.541] (II) Failed to load module "vesa" (already loaded, 0)
[    15.541] (II) LoadModule: "fbdev"
[    15.541] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    15.541] (II) Module fbdev: vendor="X.Org Foundation"
[    15.541] 	compiled for 1.12.3, module version = 0.4.3
[    15.541] 	Module class: X.Org Video Driver
[    15.541] 	ABI class: X.Org Video Driver, version 12.0
[    15.541] (II) UnloadModule: "fbdev"
[    15.541] (II) Unloading fbdev
[    15.541] (II) Failed to load module "fbdev" (already loaded, 0)
[    15.541] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE
[    15.547] (II) VESA: driver for VESA chipsets: vesa
[    15.547] (II) FBDEV: driver for framebuffer: fbdev
[    15.547] (++) using VT number 7

[    15.547] (II) [KMS] Kernel modesetting enabled.
[    15.547] (WW) Falling back to old probe method for vesa
[    15.547] (WW) Falling back to old probe method for fbdev
[    15.547] (II) Loading sub module "fbdevhw"
[    15.547] (II) LoadModule: "fbdevhw"
[    15.547] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    15.547] (II) Module fbdevhw: vendor="X.Org Foundation"
[    15.547] 	compiled for 1.12.3, module version = 0.0.2
[    15.547] 	ABI class: X.Org Video Driver, version 12.0
[    15.548] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    15.548] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    15.548] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    15.548] (==) RADEON(0): Default visual is TrueColor
[    15.548] (==) RADEON(0): RGB weight 888
[    15.548] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    15.548] (--) RADEON(0): Chipset: "ATI Radeon X1300/X1550" (ChipID = 0x7187)
[    15.548] drmOpenDevice: node name is /dev/dri/card0
[    15.548] drmOpenDevice: open result is 9, (OK)
[    15.548] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    15.548] drmOpenDevice: node name is /dev/dri/card0
[    15.548] drmOpenDevice: open result is 9, (OK)
[    15.548] drmOpenByBusid: drmOpenMinor returns 9
[    15.548] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    15.548] (II) Loading sub module "dri2"
[    15.548] (II) LoadModule: "dri2"
[    15.548] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.548] (II) Module dri2: vendor="X.Org Foundation"
[    15.548] 	compiled for 1.12.3, module version = 1.2.0
[    15.548] 	ABI class: X.Org Server Extension, version 6.0
[    15.548] (II) Loading sub module "exa"
[    15.548] (II) LoadModule: "exa"
[    15.549] (II) Loading /usr/lib/xorg/modules/libexa.so
[    15.549] (II) Module exa: vendor="X.Org Foundation"
[    15.549] 	compiled for 1.12.3, module version = 2.5.0
[    15.549] 	ABI class: X.Org Video Driver, version 12.0
[    15.549] (II) RADEON(0): KMS Color Tiling: enabled
[    15.549] (II) RADEON(0): KMS Pageflipping: enabled
[    15.549] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    15.581] (II) RADEON(0): Output VGA-0 has no monitor section
[    15.628] (II) RADEON(0): Output S-video has no monitor section
[    15.676] (II) RADEON(0): Output DVI-0 has no monitor section
[    15.708] (II) RADEON(0): EDID for output VGA-0
[    15.708] (II) RADEON(0): Manufacturer: ACR  Model: ad80  Serial#: 1918929268
[    15.708] (II) RADEON(0): Year: 2007  Week: 26
[    15.708] (II) RADEON(0): EDID Version: 1.3
[    15.708] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    15.708] (II) RADEON(0): Sync:  Separate
[    15.708] (II) RADEON(0): Max Image Size [cm]: horiz.: 41  vert.: 26
[    15.708] (II) RADEON(0): Gamma: 2.20
[    15.708] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    15.708] (II) RADEON(0): First detailed timing not preferred mode in violation of standard!
[    15.708] (II) RADEON(0): redX: 0.650 redY: 0.345   greenX: 0.287 greenY: 0.600
[    15.708] (II) RADEON(0): blueX: 0.140 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
[    15.708] (II) RADEON(0): Supported established timings:
[    15.708] (II) RADEON(0): 720x400@70Hz
[    15.708] (II) RADEON(0): 640x480@60Hz
[    15.708] (II) RADEON(0): 640x480@67Hz
[    15.708] (II) RADEON(0): 640x480@72Hz
[    15.708] (II) RADEON(0): 640x480@75Hz
[    15.708] (II) RADEON(0): 800x600@56Hz
[    15.708] (II) RADEON(0): 800x600@60Hz
[    15.708] (II) RADEON(0): 800x600@72Hz
[    15.708] (II) RADEON(0): 800x600@75Hz
[    15.708] (II) RADEON(0): 832x624@75Hz
[    15.708] (II) RADEON(0): 1024x768@60Hz
[    15.708] (II) RADEON(0): 1024x768@70Hz
[    15.708] (II) RADEON(0): 1024x768@75Hz
[    15.708] (II) RADEON(0): 1280x1024@75Hz
[    15.708] (II) RADEON(0): 1152x864@75Hz
[    15.708] (II) RADEON(0): Manufacturer's mask: 0
[    15.708] (II) RADEON(0): Supported standard timings:
[    15.708] (II) RADEON(0): #0: hsize: 1400  vsize 1050  refresh: 75  vid: 20368
[    15.708] (II) RADEON(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    15.708] (II) RADEON(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    15.708] (II) RADEON(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    15.708] (II) RADEON(0): #4: hsize: 1280  vsize 800  refresh: 75  vid: 3969
[    15.708] (II) RADEON(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    15.709] (II) RADEON(0): #6: hsize: 1152  vsize 921  refresh: 76  vid: 36977
[    15.709] (II) RADEON(0): #7: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    15.709] (II) RADEON(0): Supported detailed timing:
[    15.709] (II) RADEON(0): clock: 89.0 MHz   Image Size:  410 x 257 mm
[    15.709] (II) RADEON(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1600 h_border: 0
[    15.709] (II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
[    15.709] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 84 kHz, PixClock max 145 MHz
[    15.709] (II) RADEON(0): Serial No: L800C0104025
[    15.709] (II) RADEON(0): Monitor name: AL1916W
[    15.709] (II) RADEON(0): EDID (in hex):
[    15.709] (II) RADEON(0): 	00ffffffffffff00047280ad74896072
[    15.709] (II) RADEON(0): 	1a11010308291a78e89ae5a658499923
[    15.709] (II) RADEON(0): 	115054bfef80904f950f81808140810f
[    15.709] (II) RADEON(0): 	81007190714fc422a0a050841a303020
[    15.709] (II) RADEON(0): 	36009a011100001e000000fd00384c1f
[    15.709] (II) RADEON(0): 	540e000a202020202020000000ff004c
[    15.709] (II) RADEON(0): 	38303043303130343032350a000000fc
[    15.709] (II) RADEON(0): 	00414c31393136570a202020202000f7
[    15.709] (II) RADEON(0): EDID vendor "ACR", prod id 44416
[    15.709] (II) RADEON(0): Using EDID range info for horizontal sync
[    15.709] (II) RADEON(0): Using EDID range info for vertical refresh
[    15.709] (II) RADEON(0): Printing DDC gathered Modelines:
[    15.709] (II) RADEON(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz e)
[    15.709] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    15.709] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    15.709] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    15.709] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    15.709] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    15.709] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    15.709] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    15.709] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    15.709] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    15.709] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    15.709] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    15.709] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    15.709] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    15.709] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    15.709] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    15.709] (II) RADEON(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[    15.709] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    15.709] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    15.709] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    15.709] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[    15.709] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    15.709] (II) RADEON(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz e)
[    15.709] (II) RADEON(0): Not using mode "1400x1050" (bad mode clock/interlace/doublescan)
[    15.709] (II) RADEON(0): Printing probed modes for output VGA-0
[    15.709] (II) RADEON(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz e)
[    15.709] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    15.709] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    15.709] (II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    15.709] (II) RADEON(0): Modeline "1440x900"x60.1   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz e)
[    15.709] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    15.710] (II) RADEON(0): Modeline "1152x921"x76.0  113.52  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz)
[    15.710] (II) RADEON(0): Modeline "1366x768"x60.0   85.89  1366 1439 1583 1800  768 769 772 795 -hsync +vsync (47.7 kHz)
[    15.710] (II) RADEON(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz e)
[    15.710] (II) RADEON(0): Modeline "1280x800"x74.9  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[    15.710] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz e)
[    15.710] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    15.710] (II) RADEON(0): Modeline "1280x768"x74.9  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz e)
[    15.710] (II) RADEON(0): Modeline "1280x768"x59.9   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz e)
[    15.710] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[    15.710] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    15.710] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    15.710] (II) RADEON(0): Modeline "1024x576"x60.0   46.97  1024 1064 1168 1312  576 577 580 597 -hsync +vsync (35.8 kHz)
[    15.710] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    15.710] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    15.710] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    15.710] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    15.710] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    15.710] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[    15.710] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[    15.710] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    15.710] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    15.710] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    15.710] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    15.756] (II) RADEON(0): EDID for output S-video
[    15.804] (II) RADEON(0): EDID for output DVI-0
[    15.804] (II) RADEON(0): Output VGA-0 connected
[    15.804] (II) RADEON(0): Output S-video disconnected
[    15.804] (II) RADEON(0): Output DVI-0 disconnected
[    15.804] (II) RADEON(0): Using exact sizes for initial modes
[    15.804] (II) RADEON(0): Output VGA-0 using initial mode 1440x900
[    15.804] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    15.804] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:4000000 visible:3a1c000
[    15.804] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    15.804] (**) RADEON(0): Display dimensions: (410, 260) mm
[    15.804] (**) RADEON(0): DPI set to (89, 87)
[    15.804] (II) Loading sub module "fb"
[    15.804] (II) LoadModule: "fb"
[    15.805] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.805] (II) Module fb: vendor="X.Org Foundation"
[    15.805] 	compiled for 1.12.3, module version = 1.0.0
[    15.805] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    15.805] (II) Loading sub module "ramdac"
[    15.805] (II) LoadModule: "ramdac"
[    15.805] (II) Module "ramdac" already built-in
[    15.805] (II) UnloadModule: "vesa"
[    15.805] (II) Unloading vesa
[    15.805] (II) UnloadModule: "fbdev"
[    15.805] (II) Unloading fbdev
[    15.805] (II) UnloadSubModule: "fbdevhw"
[    15.805] (II) Unloading fbdevhw
[    15.805] (--) Depth 24 pixmap format is 32 bpp
[    15.805] (II) RADEON(0): [DRI2] Setup complete
[    15.805] (II) RADEON(0): [DRI2]   DRI driver: r300
[    15.805] (II) RADEON(0): [DRI2]   VDPAU driver: r300
[    15.805] (II) RADEON(0): Front buffer size: 5244K
[    15.805] (II) RADEON(0): VRAM usage limit set to 48834K
[    15.805] (==) RADEON(0): Backing store disabled
[    15.805] (II) RADEON(0): Direct rendering enabled
[    15.805] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    15.805] (II) RADEON(0): Setting EXA maxPitchBytes
[    15.805] (II) EXA(0): Driver allocated offscreen pixmaps
[    15.805] (II) EXA(0): Driver registered support for the following operations:
[    15.805] (II)         Solid
[    15.805] (II)         Copy
[    15.805] (II)         Composite (RENDER acceleration)
[    15.805] (II)         UploadToScreen
[    15.805] (II)         DownloadFromScreen
[    15.805] (II) RADEON(0): Acceleration enabled
[    15.806] (==) RADEON(0): DPMS enabled
[    15.806] (==) RADEON(0): Silken mouse enabled
[    15.806] (II) RADEON(0): Set up textured video
[    15.806] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    15.806] (II) RADEON(0): [XvMC] Extension initialized.
[    15.806] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    15.806] (--) RandR disabled
[    15.806] (II) Initializing built-in extension Generic Event Extension
[    15.806] (II) Initializing built-in extension SHAPE
[    15.806] (II) Initializing built-in extension MIT-SHM
[    15.806] (II) Initializing built-in extension XInputExtension
[    15.806] (II) Initializing built-in extension XTEST
[    15.806] (II) Initializing built-in extension BIG-REQUESTS
[    15.806] (II) Initializing built-in extension SYNC
[    15.806] (II) Initializing built-in extension XKEYBOARD
[    15.806] (II) Initializing built-in extension XC-MISC
[    15.806] (II) Initializing built-in extension SECURITY
[    15.806] (II) Initializing built-in extension XINERAMA
[    15.806] (II) Initializing built-in extension XFIXES
[    15.806] (II) Initializing built-in extension RENDER
[    15.806] (II) Initializing built-in extension RANDR
[    15.806] (II) Initializing built-in extension COMPOSITE
[    15.806] (II) Initializing built-in extension DAMAGE
[    15.838] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    15.838] (II) AIGLX: enabled GLX_INTEL_swap_event
[    15.838] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    15.838] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    15.839] (II) AIGLX: Loaded and initialized r300
[    15.839] (II) GLX: Initialized DRI2 GL provider for screen 0
[    15.868] (II) RADEON(0): Setting screen physical size to 380 x 238
[    15.892] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.898] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    15.898] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.898] (II) LoadModule: "evdev"
[    15.899] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.899] (II) Module evdev: vendor="X.Org Foundation"
[    15.899] 	compiled for 1.12.1, module version = 2.7.0
[    15.899] 	Module class: X.Org XInput Driver
[    15.899] 	ABI class: X.Org XInput driver, version 16.0
[    15.899] (II) Using input driver 'evdev' for 'Power Button'
[    15.899] (**) Power Button: always reports core events
[    15.899] (**) evdev: Power Button: Device: "/dev/input/event1"
[    15.899] (--) evdev: Power Button: Vendor 0 Product 0x1
[    15.899] (--) evdev: Power Button: Found keys
[    15.899] (II) evdev: Power Button: Configuring as keyboard
[    15.899] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    15.899] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    15.899] (**) Option "xkb_rules" "evdev"
[    15.899] (**) Option "xkb_model" "pc105"
[    15.899] (**) Option "xkb_layout" "us"
[    15.900] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    15.900] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.900] (II) Using input driver 'evdev' for 'Power Button'
[    15.901] (**) Power Button: always reports core events
[    15.901] (**) evdev: Power Button: Device: "/dev/input/event0"
[    15.901] (--) evdev: Power Button: Vendor 0 Product 0x1
[    15.901] (--) evdev: Power Button: Found keys
[    15.901] (II) evdev: Power Button: Configuring as keyboard
[    15.901] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    15.901] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    15.901] (**) Option "xkb_rules" "evdev"
[    15.901] (**) Option "xkb_model" "pc105"
[    15.901] (**) Option "xkb_layout" "us"
[    15.902] (II) config/udev: Adding input device Chicony USB Keyboard (/dev/input/event2)
[    15.902] (**) Chicony USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    15.902] (II) Using input driver 'evdev' for 'Chicony USB Keyboard'
[    15.902] (**) Chicony USB Keyboard: always reports core events
[    15.902] (**) evdev: Chicony USB Keyboard: Device: "/dev/input/event2"
[    15.902] (--) evdev: Chicony USB Keyboard: Vendor 0x4f2 Product 0x111
[    15.902] (--) evdev: Chicony USB Keyboard: Found keys
[    15.902] (II) evdev: Chicony USB Keyboard: Configuring as keyboard
[    15.902] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.0/input/input2/event2"
[    15.902] (II) XINPUT: Adding extended input device "Chicony USB Keyboard" (type: KEYBOARD, id 8)
[    15.902] (**) Option "xkb_rules" "evdev"
[    15.902] (**) Option "xkb_model" "pc105"
[    15.902] (**) Option "xkb_layout" "us"
[    15.903] (II) config/udev: Adding input device Chicony USB Keyboard (/dev/input/event3)
[    15.903] (**) Chicony USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    15.903] (II) Using input driver 'evdev' for 'Chicony USB Keyboard'
[    15.903] (**) Chicony USB Keyboard: always reports core events
[    15.903] (**) evdev: Chicony USB Keyboard: Device: "/dev/input/event3"
[    15.903] (--) evdev: Chicony USB Keyboard: Vendor 0x4f2 Product 0x111
[    15.904] (--) evdev: Chicony USB Keyboard: Found keys
[    15.904] (II) evdev: Chicony USB Keyboard: Configuring as keyboard
[    15.904] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.1/input/input3/event3"
[    15.904] (II) XINPUT: Adding extended input device "Chicony USB Keyboard" (type: KEYBOARD, id 9)
[    15.904] (**) Option "xkb_rules" "evdev"
[    15.904] (**) Option "xkb_model" "pc105"
[    15.904] (**) Option "xkb_layout" "us"
[    15.905] (II) config/udev: Adding input device HDA SIS966 Line Out Surround (/dev/input/event10)
[    15.905] (II) No input driver specified, ignoring this device.
[    15.905] (II) This device may have been added with another device file.
[    15.906] (II) config/udev: Adding input device HDA SIS966 Line Out Front (/dev/input/event11)
[    15.906] (II) No input driver specified, ignoring this device.
[    15.906] (II) This device may have been added with another device file.
[    15.906] (II) config/udev: Adding input device HDA SIS966 Line (/dev/input/event4)
[    15.907] (II) No input driver specified, ignoring this device.
[    15.907] (II) This device may have been added with another device file.
[    15.907] (II) config/udev: Adding input device HDA SIS966 Front Mic (/dev/input/event5)
[    15.907] (II) No input driver specified, ignoring this device.
[    15.907] (II) This device may have been added with another device file.
[    15.910] (II) config/udev: Adding input device HDA SIS966 Rear Mic (/dev/input/event6)
[    15.910] (II) No input driver specified, ignoring this device.
[    15.910] (II) This device may have been added with another device file.
[    15.910] (II) config/udev: Adding input device HDA SIS966 Front Headphone (/dev/input/event7)
[    15.910] (II) No input driver specified, ignoring this device.
[    15.910] (II) This device may have been added with another device file.
[    15.911] (II) config/udev: Adding input device HDA SIS966 Line Out Side (/dev/input/event8)
[    15.911] (II) No input driver specified, ignoring this device.
[    15.911] (II) This device may have been added with another device file.
[    15.911] (II) config/udev: Adding input device HDA SIS966 Line Out CLFE (/dev/input/event9)
[    15.911] (II) No input driver specified, ignoring this device.
[    15.911] (II) This device may have been added with another device file.
[    15.912] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event12)
[    15.912] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[    15.912] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[    15.912] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    15.912] (**) evdev: ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event12"
[    15.912] (--) evdev: ImPS/2 Generic Wheel Mouse: Vendor 0x2 Product 0x5
[    15.912] (--) evdev: ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    15.912] (--) evdev: ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[    15.912] (--) evdev: ImPS/2 Generic Wheel Mouse: Found relative axes
[    15.912] (--) evdev: ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    15.912] (II) evdev: ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    15.912] (II) evdev: ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[    15.912] (**) evdev: ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    15.912] (**) evdev: ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.912] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input12/event12"
[    15.912] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE, id 10)
[    15.912] (II) evdev: ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[    15.912] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    15.912] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[    15.912] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[    15.913] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[    15.913] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[    15.913] (II) No input driver specified, ignoring this device.
[    15.913] (II) This device may have been added with another device file.
[    75.287] (II) RADEON(0): EDID vendor "ACR", prod id 44416
[    75.288] (II) RADEON(0): Using hsync ranges from config file
[    75.288] (II) RADEON(0): Using vrefresh ranges from config file
[    75.288] (II) RADEON(0): Printing DDC gathered Modelines:
[    75.288] (II) RADEON(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz e)
[    75.288] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    75.288] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    75.288] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    75.288] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    75.288] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    75.288] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    75.288] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    75.288] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    75.288] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    75.288] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    75.288] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    75.288] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    75.288] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    75.288] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    75.288] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    75.288] (II) RADEON(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[    75.288] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    75.288] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    75.288] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    75.288] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[    75.288] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    75.288] (II) RADEON(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz e)
[    77.279] (II) XKB: reuse xkmfile /var/lib/xkb/server-518754FAB1FA320CD11E67E5F27005732682D4B3.xkm
[    78.657] (II) RADEON(0): EDID vendor "ACR", prod id 44416
[    78.657] (II) RADEON(0): Using hsync ranges from config file
[    78.657] (II) RADEON(0): Using vrefresh ranges from config file
[    78.657] (II) RADEON(0): Printing DDC gathered Modelines:
[    78.657] (II) RADEON(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz e)
[    78.657] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    78.657] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    78.657] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    78.657] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    78.657] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    78.657] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    78.657] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    78.657] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    78.657] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    78.657] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    78.657] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    78.657] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    78.657] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    78.657] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    78.657] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    78.657] (II) RADEON(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[    78.657] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    78.657] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    78.657] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    78.657] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[    78.657] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    78.657] (II) RADEON(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz e)
[    97.964] (II) RADEON(0): EDID vendor "ACR", prod id 44416
[    97.964] (II) RADEON(0): Using hsync ranges from config file
[    97.964] (II) RADEON(0): Using vrefresh ranges from config file
[    97.964] (II) RADEON(0): Printing DDC gathered Modelines:
[    97.964] (II) RADEON(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz e)
[    97.964] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    97.964] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    97.964] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    97.964] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    97.964] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    97.964] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    97.964] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    97.964] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    97.964] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    97.964] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    97.964] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    97.964] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    97.964] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    97.964] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    97.964] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    97.964] (II) RADEON(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[    97.964] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    97.964] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    97.964] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    97.964] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[    97.964] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[    97.964] (II) RADEON(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz e)
[ 14283.782] (II) RADEON(0): EDID vendor "ACR", prod id 44416
[ 14283.906] (II) RADEON(0): Using hsync ranges from config file
[ 14283.906] (II) RADEON(0): Using vrefresh ranges from config file
[ 14283.906] (II) RADEON(0): Printing DDC gathered Modelines:
[ 14283.906] (II) RADEON(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[ 14283.906] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 14283.907] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[ 14283.907] (II) RADEON(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[ 14283.907] (II) RADEON(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[ 14283.907] (II) RADEON(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz e)

```

---

### Post by Yellow Pasque on 2013-02-01
Yeah, that does look odd with the "x0.0" at the end of the modeline names (should be "x60.0). What resolution do you get and what are you trying to achieve?
```
xrandr -q
```

---

### Post by Acharn on 2013-02-01
> **kurt18947 said:**
> If you choose to go with a new video card, I have a low end Nvidia -8400GS and SWMBO has a a GT210 (or something like that) both running on AMD Gigabyte MoBo s with integrated ATI/AMD graphics.  I just disabled onboard video and set the PCIe slot as preferred.  Installed the video card, booted, loaded the Nvidia drivers (though the open source drivers aren't bad) and we were both up & running.  No issues though 12.10 Gnome remix seems to prefer the open source driver at times for stability.

This seems like an intriguing possibility. There's a graphics connector on the MoBo which doesn't seem to do anything. The graphics card shows up under the 'pci' section when I check 'lshw', but the output doesn't show an onboard graphics processor. The motherboard is an Acer F672CR, and the chipsets used all seem to be SiS. Can you point me to a tutorial on how to disable/enable the onboard graphics chip? Just to play around with. I think I'm going to go for a new graphics card anyway. I was able to find the spec sheet and it says my power supply is 250 Watts, so I suppose I need to spring for that too, but they're only about $10 here in Thailand. Also, I've been pretty happy with the open source Radeon driver. And that's probably what I would prefer to use with the new card. As I said earlier, I'm not into games, or any other applications, that are heavy on graphics.

---

### Post by Acharn on 2013-02-01
> **Temüjin said:**
> Yeah, that does look odd with the "x0.0" at the end of the modeline names (should be "x60.0). What resolution do you get and what are you trying to achieve?
```
xrandr -q
```

I wonder if we've been talking at cross-purposes. The log I sent you was from a session on my 12.04 installation. Here's the log when I'm booted to 12.10 from a USB stick:
```

[   140.408] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[   140.409] X Protocol Version 11, Revision 0
[   140.409] Build Operating System: Linux 3.2.0-26-generic i686 Ubuntu
[   140.409] Current Operating System: Linux ubuntu 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686
[   140.409] Kernel command line: noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --  nomodeset
[   140.409] Build Date: 08 October 2012  03:34:08PM
[   140.409] xorg-server 2:1.13.0-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[   140.409] Current version of pixman: 0.26.0
[   140.409] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   140.409] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   140.409] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb  1 08:13:14 2013
[   140.411] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   140.420] (==) No Layout section.  Using the first Screen section.
[   140.421] (==) No screen section available. Using defaults.
[   140.421] (**) |-->Screen "Default Screen Section" (0)
[   140.421] (**) |   |-->Monitor "<default monitor>"
[   140.427] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   140.428] (==) Automatically adding devices
[   140.428] (==) Automatically enabling devices
[   140.428] (==) Automatically adding GPU devices
[   140.436] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   140.436] 	Entry deleted from font path.
[   140.436] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   140.436] 	Entry deleted from font path.
[   140.436] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   140.436] 	Entry deleted from font path.
[   151.497] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   151.497] 	Entry deleted from font path.
[   151.497] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   151.497] 	Entry deleted from font path.
[   151.498] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   151.498] 	Entry deleted from font path.
[   151.498] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   151.498] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   151.498] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   151.498] (II) Loader magic: 0xb776c640
[   151.498] (II) Module ABI versions:
[   151.498] 	X.Org ANSI C Emulation: 0.4
[   151.498] 	X.Org Video Driver: 13.0
[   151.498] 	X.Org XInput driver : 18.0
[   151.498] 	X.Org Server Extension : 7.0
[   151.499] (II) config/udev: Adding drm device (/dev/dri/card0)
[   151.502] (--) PCI:*(0:1:0:0) 1002:7187:174b:5920 rev 0, Mem @ 0xd0000000/268435456, 0xfdcf0000/65536, I/O @ 0x0000de00/256, BIOS @ 0x????????/131072
[   151.502] (--) PCI: (0:1:0:1) 1002:71a7:174b:5921 rev 0, Mem @ 0xfdce0000/65536
[   151.502] (II) Open ACPI successful (/var/run/acpid.socket)
[   151.502] Initializing built-in extension Generic Event Extension
[   151.502] Initializing built-in extension SHAPE
[   151.502] Initializing built-in extension MIT-SHM
[   151.502] Initializing built-in extension XInputExtension
[   151.502] Initializing built-in extension XTEST
[   151.502] Initializing built-in extension BIG-REQUESTS
[   151.502] Initializing built-in extension SYNC
[   151.502] Initializing built-in extension XKEYBOARD
[   151.502] Initializing built-in extension XC-MISC
[   151.502] Initializing built-in extension SECURITY
[   151.502] Initializing built-in extension XINERAMA
[   151.502] Initializing built-in extension XFIXES
[   151.502] Initializing built-in extension RENDER
[   151.502] Initializing built-in extension RANDR
[   151.502] Initializing built-in extension COMPOSITE
[   151.502] Initializing built-in extension DAMAGE
[   151.502] Initializing built-in extension MIT-SCREEN-SAVER
[   151.502] Initializing built-in extension DOUBLE-BUFFER
[   151.503] Initializing built-in extension RECORD
[   151.503] Initializing built-in extension DPMS
[   151.503] Initializing built-in extension X-Resource
[   151.503] Initializing built-in extension XVideo
[   151.503] Initializing built-in extension XVideo-MotionCompensation
[   151.503] Initializing built-in extension XFree86-VidModeExtension
[   151.503] Initializing built-in extension XFree86-DGA
[   151.503] Initializing built-in extension XFree86-DRI
[   151.503] Initializing built-in extension DRI2
[   151.503] (II) LoadModule: "glx"
[   153.228] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   163.139] (II) Module glx: vendor="X.Org Foundation"
[   163.139] 	compiled for 1.13.0, module version = 1.0.0
[   163.139] 	ABI class: X.Org Server Extension, version 7.0
[   163.139] (==) AIGLX enabled
[   163.146] Loading extension GLX
[   163.146] (==) Matched fglrx as autoconfigured driver 0
[   163.146] (==) Matched ati as autoconfigured driver 1
[   163.146] (==) Matched fglrx as autoconfigured driver 2
[   163.146] (==) Matched ati as autoconfigured driver 3
[   163.146] (==) Matched vesa as autoconfigured driver 4
[   163.146] (==) Matched modesetting as autoconfigured driver 5
[   163.146] (==) Matched fbdev as autoconfigured driver 6
[   163.146] (==) Assigned the driver to the xf86ConfigLayout
[   163.146] (II) LoadModule: "fglrx"
[   163.147] (WW) Warning, couldn't open module fglrx
[   163.147] (II) UnloadModule: "fglrx"
[   163.147] (II) Unloading fglrx
[   163.147] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   163.147] (II) LoadModule: "ati"
[   163.148] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   163.178] (II) Module ati: vendor="X.Org Foundation"
[   163.178] 	compiled for 1.13.0, module version = 6.99.99
[   163.178] 	Module class: X.Org Video Driver
[   163.178] 	ABI class: X.Org Video Driver, version 13.0
[   163.178] (II) LoadModule: "radeon"
[   163.196] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   163.255] (II) Module radeon: vendor="X.Org Foundation"
[   163.255] 	compiled for 1.13.0, module version = 6.99.99
[   163.255] 	Module class: X.Org Video Driver
[   163.255] 	ABI class: X.Org Video Driver, version 13.0
[   163.255] (II) LoadModule: "vesa"
[   163.294] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   163.303] (II) Module vesa: vendor="X.Org Foundation"
[   163.303] 	compiled for 1.12.99.902, module version = 2.3.2
[   163.303] 	Module class: X.Org Video Driver
[   163.303] 	ABI class: X.Org Video Driver, version 13.0
[   163.304] (II) LoadModule: "modesetting"
[   163.304] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   163.326] (II) Module modesetting: vendor="X.Org Foundation"
[   163.326] 	compiled for 1.13.0, module version = 0.5.0
[   163.326] 	Module class: X.Org Video Driver
[   163.326] 	ABI class: X.Org Video Driver, version 13.0
[   163.326] (II) LoadModule: "fbdev"
[   163.328] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   163.330] (II) Module fbdev: vendor="X.Org Foundation"
[   163.330] 	compiled for 1.12.99.902, module version = 0.4.3
[   163.330] 	Module class: X.Org Video Driver
[   163.330] 	ABI class: X.Org Video Driver, version 13.0
[   163.331] (==) Matched fglrx as autoconfigured driver 0
[   163.331] (==) Matched ati as autoconfigured driver 1
[   163.331] (==) Matched fglrx as autoconfigured driver 2
[   163.331] (==) Matched ati as autoconfigured driver 3
[   163.331] (==) Matched vesa as autoconfigured driver 4
[   163.331] (==) Matched modesetting as autoconfigured driver 5
[   163.331] (==) Matched fbdev as autoconfigured driver 6
[   163.331] (==) Assigned the driver to the xf86ConfigLayout
[   163.331] (II) LoadModule: "fglrx"
[   163.331] (WW) Warning, couldn't open module fglrx
[   163.331] (II) UnloadModule: "fglrx"
[   163.331] (II) Unloading fglrx
[   163.331] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   163.331] (II) LoadModule: "ati"
[   163.332] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   163.332] (II) Module ati: vendor="X.Org Foundation"
[   163.332] 	compiled for 1.13.0, module version = 6.99.99
[   163.332] 	Module class: X.Org Video Driver
[   163.332] 	ABI class: X.Org Video Driver, version 13.0
[   163.332] (II) LoadModule: "vesa"
[   163.332] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   163.332] (II) Module vesa: vendor="X.Org Foundation"
[   163.332] 	compiled for 1.12.99.902, module version = 2.3.2
[   163.332] 	Module class: X.Org Video Driver
[   163.332] 	ABI class: X.Org Video Driver, version 13.0
[   163.332] (II) UnloadModule: "vesa"
[   163.332] (II) Unloading vesa
[   163.332] (II) Failed to load module "vesa" (already loaded, 0)
[   163.332] (II) LoadModule: "modesetting"
[   163.332] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   163.332] (II) Module modesetting: vendor="X.Org Foundation"
[   163.332] 	compiled for 1.13.0, module version = 0.5.0
[   163.332] 	Module class: X.Org Video Driver
[   163.332] 	ABI class: X.Org Video Driver, version 13.0
[   163.332] (II) UnloadModule: "modesetting"
[   163.332] (II) Unloading modesetting
[   163.332] (II) Failed to load module "modesetting" (already loaded, 0)
[   163.332] (II) LoadModule: "fbdev"
[   163.333] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   163.333] (II) Module fbdev: vendor="X.Org Foundation"
[   163.333] 	compiled for 1.12.99.902, module version = 0.4.3
[   163.333] 	Module class: X.Org Video Driver
[   163.333] 	ABI class: X.Org Video Driver, version 13.0
[   163.333] (II) UnloadModule: "fbdev"
[   163.333] (II) Unloading fbdev
[   163.333] (II) Failed to load module "fbdev" (already loaded, 0)
[   163.333] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE
[   163.339] (II) VESA: driver for VESA chipsets: vesa
[   163.339] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   163.339] (II) FBDEV: driver for framebuffer: fbdev
[   163.339] (++) using VT number 7

[   163.341] (II) [KMS] drm report modesetting isn't supported.
[   163.341] (II) [KMS] drm report modesetting isn't supported.
[   163.341] (II) [KMS] drm report modesetting isn't supported.
[   163.341] (II) [KMS] drm report modesetting isn't supported.
[   163.341] (II) [KMS] drm report modesetting isn't supported.
[   163.341] (WW) Falling back to old probe method for modesetting
[   163.344] (WW) Falling back to old probe method for fbdev
[   163.344] (II) Loading sub module "fbdevhw"
[   163.345] (II) LoadModule: "fbdevhw"
[   163.345] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   163.348] (II) Module fbdevhw: vendor="X.Org Foundation"
[   163.348] 	compiled for 1.13.0, module version = 0.0.2
[   163.348] 	ABI class: X.Org Video Driver, version 13.0
[   163.348] (EE) open /dev/fb0: No such file or directory
[   163.348] (EE) Screen 0 deleted because of no matching config section.
[   163.348] (II) UnloadModule: "radeon"
[   163.348] (EE) Screen 0 deleted because of no matching config section.
[   163.348] (II) UnloadModule: "radeon"
[   163.348] (EE) Screen 0 deleted because of no matching config section.
[   163.348] (II) UnloadModule: "radeon"
[   163.348] (EE) Screen 0 deleted because of no matching config section.
[   163.348] (II) UnloadModule: "radeon"
[   163.348] (II) Loading sub module "vbe"
[   163.348] (II) LoadModule: "vbe"
[   163.349] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   163.351] (II) Module vbe: vendor="X.Org Foundation"
[   163.351] 	compiled for 1.13.0, module version = 1.1.0
[   163.351] 	ABI class: X.Org Video Driver, version 13.0
[   163.351] (II) Loading sub module "int10"
[   163.351] (II) LoadModule: "int10"
[   163.352] (II) Loading /usr/lib/xorg/modules/libint10.so
[   163.357] (II) Module int10: vendor="X.Org Foundation"
[   163.357] 	compiled for 1.13.0, module version = 1.0.0
[   163.357] 	ABI class: X.Org Video Driver, version 13.0
[   163.357] (II) VESA(0): initializing int10
[   163.536] (II) VESA(0): VESA BIOS detected
[   163.536] (II) VESA(0): VESA VBE Version 3.0
[   163.536] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[   163.537] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[   163.537] (II) VESA(0): VESA VBE OEM Software Rev: 9.12
[   163.537] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[   163.537] (II) VESA(0): VESA VBE OEM Product: RV516
[   163.537] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[   163.556] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   163.556] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[   163.556] (==) VESA(0): RGB weight 888
[   163.556] (==) VESA(0): Default visual is TrueColor
[   163.556] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[   163.556] (II) Loading sub module "ddc"
[   163.556] (II) LoadModule: "ddc"
[   163.556] (II) Module "ddc" already built-in
[   163.657] (II) VESA(0): VESA VBE DDC supported
[   163.657] (II) VESA(0): VESA VBE DDC Level 2
[   163.657] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[   163.757] (II) VESA(0): VESA VBE DDC read successfully
[   163.757] (II) VESA(0): Manufacturer: ACR  Model: ad80  Serial#: 1918929268
[   163.757] (II) VESA(0): Year: 2007  Week: 26
[   163.757] (II) VESA(0): EDID Version: 1.3
[   163.757] (II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[   163.757] (II) VESA(0): Sync:  Separate
[   163.757] (II) VESA(0): Max Image Size [cm]: horiz.: 41  vert.: 26
[   163.757] (II) VESA(0): Gamma: 2.20
[   163.757] (II) VESA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[   163.757] (II) VESA(0): First detailed timing not preferred mode in violation of standard!
[   163.757] (II) VESA(0): redX: 0.650 redY: 0.345   greenX: 0.287 greenY: 0.600
[   163.757] (II) VESA(0): blueX: 0.140 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
[   163.757] (II) VESA(0): Supported established timings:
[   163.757] (II) VESA(0): 720x400@70Hz
[   163.757] (II) VESA(0): 640x480@60Hz
[   163.757] (II) VESA(0): 640x480@67Hz
[   163.757] (II) VESA(0): 640x480@72Hz
[   163.757] (II) VESA(0): 640x480@75Hz
[   163.757] (II) VESA(0): 800x600@56Hz
[   163.757] (II) VESA(0): 800x600@60Hz
[   163.757] (II) VESA(0): 800x600@72Hz
[   163.757] (II) VESA(0): 800x600@75Hz
[   163.757] (II) VESA(0): 832x624@75Hz
[   163.757] (II) VESA(0): 1024x768@60Hz
[   163.757] (II) VESA(0): 1024x768@70Hz
[   163.757] (II) VESA(0): 1024x768@75Hz
[   163.757] (II) VESA(0): 1280x1024@75Hz
[   163.757] (II) VESA(0): 1152x864@75Hz
[   163.757] (II) VESA(0): Manufacturer's mask: 0
[   163.757] (II) VESA(0): Supported standard timings:
[   163.757] (II) VESA(0): #0: hsize: 1400  vsize 1050  refresh: 75  vid: 20368
[   163.757] (II) VESA(0): #1: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[   163.757] (II) VESA(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   163.757] (II) VESA(0): #3: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   163.757] (II) VESA(0): #4: hsize: 1280  vsize 800  refresh: 75  vid: 3969
[   163.757] (II) VESA(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
[   163.757] (II) VESA(0): #6: hsize: 1152  vsize 921  refresh: 76  vid: 36977
[   163.757] (II) VESA(0): #7: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   163.757] (II) VESA(0): Supported detailed timing:
[   163.757] (II) VESA(0): clock: 89.0 MHz   Image Size:  410 x 257 mm
[   163.757] (II) VESA(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1600 h_border: 0
[   163.757] (II) VESA(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
[   163.757] (II) VESA(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 84 kHz, PixClock max 145 MHz
[   163.757] (II) VESA(0): Serial No: L800C0104025
[   163.757] (II) VESA(0): Monitor name: AL1916W
[   163.757] (II) VESA(0): EDID (in hex):
[   163.758] (II) VESA(0): 	00ffffffffffff00047280ad74896072
[   163.758] (II) VESA(0): 	1a11010308291a78e89ae5a658499923
[   163.758] (II) VESA(0): 	115054bfef80904f950f81808140810f
[   163.758] (II) VESA(0): 	81007190714fc422a0a050841a303020
[   163.758] (II) VESA(0): 	36009a011100001e000000fd00384c1f
[   163.758] (II) VESA(0): 	540e000a202020202020000000ff004c
[   163.758] (II) VESA(0): 	38303043303130343032350a000000fc
[   163.758] (II) VESA(0): 	00414c31393136570a202020202000f7
[   163.758] (II) VESA(0): EDID vendor "ACR", prod id 44416
[   163.758] (II) VESA(0): Using EDID range info for horizontal sync
[   163.758] (II) VESA(0): Using EDID range info for vertical refresh
[   163.758] (II) VESA(0): Printing DDC gathered Modelines:
[   163.758] (II) VESA(0): Modeline "1440x900"x0.0   89.00  1440 1488 1520 1600  900 903 909 926 +hsync +vsync (55.6 kHz e)
[   163.758] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   163.758] (II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   163.758] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   163.758] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   163.758] (II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   163.758] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   163.758] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   163.758] (II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   163.758] (II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   163.758] (II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   163.758] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   163.758] (II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   163.758] (II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   163.758] (II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   163.758] (II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   163.758] (II) VESA(0): Modeline "1400x1050"x0.0  156.00  1400 1504 1648 1896  1050 1053 1057 1099 -hsync +vsync (82.3 kHz e)
[   163.758] (II) VESA(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[   163.758] (II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   163.758] (II) VESA(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   163.758] (II) VESA(0): Modeline "1280x800"x0.0  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz e)
[   163.758] (II) VESA(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz e)
[   163.758] (II) VESA(0): Modeline "1152x921"x76.0  113.47  1152 1224 1352 1552  921 922 925 962 -hsync +vsync (73.1 kHz e)
[   163.758] (II) VESA(0): Searching for matching VESA mode(s):
[   163.758] Mode: 100 (640x400)
[   163.758] 	ModeAttributes: 0xbb
[   163.758] 	WinAAttributes: 0x7
[   163.758] 	WinBAttributes: 0x0
[   163.758] 	WinGranularity: 64
[   163.758] 	WinSize: 64
[   163.758] 	WinASegment: 0xa000
[   163.758] 	WinBSegment: 0x0
[   163.759] 	WinFuncPtr: 0xc0004d11
[   163.759] 	BytesPerScanline: 640
[   163.759] 	XResolution: 640
[   163.759] 	YResolution: 400
[   163.759] 	XCharSize: 8
[   163.759] 	YCharSize: 16
[   163.759] 	NumberOfPlanes: 1
[   163.759] 	BitsPerPixel: 8
[   163.759] 	NumberOfBanks: 1
[   163.759] 	MemoryModel: 4
[   163.759] 	BankSize: 0
[   163.759] 	NumberOfImages: 63
[   163.759] 	RedMaskSize: 0
[   163.759] 	RedFieldPosition: 0
[   163.759] 	GreenMaskSize: 0
[   163.759] 	GreenFieldPosition: 0
[   163.759] 	BlueMaskSize: 0
[   163.759] 	BlueFieldPosition: 0
[   163.759] 	RsvdMaskSize: 0
[   163.759] 	RsvdFieldPosition: 0
[   163.759] 	DirectColorModeInfo: 0
[   163.759] 	PhysBasePtr: 0xd0000000
[   163.759] 	LinBytesPerScanLine: 640
[   163.759] 	BnkNumberOfImagePages: 63
[   163.759] 	LinNumberOfImagePages: 63
[   163.759] 	LinRedMaskSize: 0
[   163.759] 	LinRedFieldPosition: 0
[   163.759] 	LinGreenMaskSize: 0
[   163.759] 	LinGreenFieldPosition: 0
[   163.759] 	LinBlueMaskSize: 0
[   163.759] 	LinBlueFieldPosition: 0
[   163.759] 	LinRsvdMaskSize: 0
[   163.759] 	LinRsvdFieldPosition: 0
[   163.759] 	MaxPixelClock: 400000000
[   163.759] Mode: 101 (640x480)
[   163.759] 	ModeAttributes: 0xbb
[   163.759] 	WinAAttributes: 0x7
[   163.759] 	WinBAttributes: 0x0
[   163.759] 	WinGranularity: 64
[   163.759] 	WinSize: 64
[   163.759] 	WinASegment: 0xa000
[   163.759] 	WinBSegment: 0x0
[   163.759] 	WinFuncPtr: 0xc0004d11
[   163.759] 	BytesPerScanline: 640
[   163.759] 	XResolution: 640
[   163.759] 	YResolution: 480
[   163.759] 	XCharSize: 8
[   163.759] 	YCharSize: 16
[   163.759] 	NumberOfPlanes: 1
[   163.759] 	BitsPerPixel: 8
[   163.759] 	NumberOfBanks: 1
[   163.759] 	MemoryModel: 4
[   163.759] 	BankSize: 0
[   163.759] 	NumberOfImages: 50
[   163.759] 	RedMaskSize: 0
[   163.759] 	RedFieldPosition: 0
[   163.759] 	GreenMaskSize: 0
[   163.759] 	GreenFieldPosition: 0
[   163.759] 	BlueMaskSize: 0
[   163.759] 	BlueFieldPosition: 0
[   163.759] 	RsvdMaskSize: 0
[   163.759] 	RsvdFieldPosition: 0
[   163.759] 	DirectColorModeInfo: 0
[   163.759] 	PhysBasePtr: 0xd0000000
[   163.759] 	LinBytesPerScanLine: 640
[   163.759] 	BnkNumberOfImagePages: 50
[   163.759] 	LinNumberOfImagePages: 50
[   163.759] 	LinRedMaskSize: 0
[   163.759] 	LinRedFieldPosition: 0
[   163.759] 	LinGreenMaskSize: 0
[   163.759] 	LinGreenFieldPosition: 0
[   163.759] 	LinBlueMaskSize: 0
[   163.759] 	LinBlueFieldPosition: 0
[   163.759] 	LinRsvdMaskSize: 0
[   163.759] 	LinRsvdFieldPosition: 0
[   163.759] 	MaxPixelClock: 400000000
[   163.760] Mode: 103 (800x600)
[   163.760] 	ModeAttributes: 0xbb
[   163.760] 	WinAAttributes: 0x7
[   163.760] 	WinBAttributes: 0x0
[   163.760] 	WinGranularity: 64
[   163.760] 	WinSize: 64
[   163.760] 	WinASegment: 0xa000
[   163.760] 	WinBSegment: 0x0
[   163.760] 	WinFuncPtr: 0xc0004d11
[   163.760] 	BytesPerScanline: 832
[   163.760] 	XResolution: 800
[   163.760] 	YResolution: 600
[   163.760] 	XCharSize: 8
[   163.760] 	YCharSize: 14
[   163.760] 	NumberOfPlanes: 1
[   163.760] 	BitsPerPixel: 8
[   163.760] 	NumberOfBanks: 1
[   163.760] 	MemoryModel: 4
[   163.760] 	BankSize: 0
[   163.760] 	NumberOfImages: 31
[   163.760] 	RedMaskSize: 0
[   163.760] 	RedFieldPosition: 0
[   163.760] 	GreenMaskSize: 0
[   163.760] 	GreenFieldPosition: 0
[   163.760] 	BlueMaskSize: 0
[   163.760] 	BlueFieldPosition: 0
[   163.760] 	RsvdMaskSize: 0
[   163.760] 	RsvdFieldPosition: 0
[   163.760] 	DirectColorModeInfo: 0
[   163.760] 	PhysBasePtr: 0xd0000000
[   163.760] 	LinBytesPerScanLine: 832
[   163.760] 	BnkNumberOfImagePages: 31
[   163.760] 	LinNumberOfImagePages: 31
[   163.760] 	LinRedMaskSize: 0
[   163.760] 	LinRedFieldPosition: 0
[   163.760] 	LinGreenMaskSize: 0
[   163.760] 	LinGreenFieldPosition: 0
[   163.760] 	LinBlueMaskSize: 0
[   163.760] 	LinBlueFieldPosition: 0
[   163.760] 	LinRsvdMaskSize: 0
[   163.760] 	LinRsvdFieldPosition: 0
[   163.760] 	MaxPixelClock: 400000000
[   163.760] Mode: 105 (1024x768)
[   163.760] 	ModeAttributes: 0xbb
[   163.760] 	WinAAttributes: 0x7
[   163.760] 	WinBAttributes: 0x0
[   163.760] 	WinGranularity: 64
[   163.760] 	WinSize: 64
[   163.760] 	WinASegment: 0xa000
[   163.760] 	WinBSegment: 0x0
[   163.760] 	WinFuncPtr: 0xc0004d11
[   163.760] 	BytesPerScanline: 1024
[   163.760] 	XResolution: 1024
[   163.760] 	YResolution: 768
[   163.760] 	XCharSize: 8
[   163.760] 	YCharSize: 16
[   163.760] 	NumberOfPlanes: 1
[   163.760] 	BitsPerPixel: 8
[   163.760] 	NumberOfBanks: 1
[   163.760] 	MemoryModel: 4
[   163.760] 	BankSize: 0
[   163.761] 	NumberOfImages: 18
[   163.761] 	RedMaskSize: 0
[   163.761] 	RedFieldPosition: 0
[   163.761] 	GreenMaskSize: 0
[   163.761] 	GreenFieldPosition: 0
[   163.761] 	BlueMaskSize: 0
[   163.761] 	BlueFieldPosition: 0
[   163.761] 	RsvdMaskSize: 0
[   163.761] 	RsvdFieldPosition: 0
[   163.761] 	DirectColorModeInfo: 0
[   163.761] 	PhysBasePtr: 0xd0000000
[   163.761] 	LinBytesPerScanLine: 1024
[   163.761] 	BnkNumberOfImagePages: 18
[   163.761] 	LinNumberOfImagePages: 18
[   163.761] 	LinRedMaskSize: 0
[   163.761] 	LinRedFieldPosition: 0
[   163.761] 	LinGreenMaskSize: 0
[   163.761] 	LinGreenFieldPosition: 0
[   163.761] 	LinBlueMaskSize: 0
[   163.761] 	LinBlueFieldPosition: 0
[   163.761] 	LinRsvdMaskSize: 0
[   163.761] 	LinRsvdFieldPosition: 0
[   163.761] 	MaxPixelClock: 400000000
[   163.761] Mode: 107 (1280x1024)
[   163.761] 	ModeAttributes: 0xbb
[   163.761] 	WinAAttributes: 0x7
[   163.761] 	WinBAttributes: 0x0
[   163.761] 	WinGranularity: 64
[   163.761] 	WinSize: 64
[   163.761] 	WinASegment: 0xa000
[   163.761] 	WinBSegment: 0x0
[   163.761] 	WinFuncPtr: 0xc0004d11
[   163.761] 	BytesPerScanline: 1280
[   163.761] 	XResolution: 1280
[   163.761] 	YResolution: 1024
[   163.761] 	XCharSize: 8
[   163.761] 	YCharSize: 16
[   163.761] 	NumberOfPlanes: 1
[   163.761] 	BitsPerPixel: 8
[   163.761] 	NumberOfBanks: 1
[   163.761] 	MemoryModel: 4
[   163.761] 	BankSize: 0
[   163.761] 	NumberOfImages: 11
[   163.761] 	RedMaskSize: 0
[   163.761] 	RedFieldPosition: 0
[   163.761] 	GreenMaskSize: 0
[   163.761] 	GreenFieldPosition: 0
[   163.761] 	BlueMaskSize: 0
[   163.761] 	BlueFieldPosition: 0
[   163.761] 	RsvdMaskSize: 0
[   163.761] 	RsvdFieldPosition: 0
[   163.761] 	DirectColorModeInfo: 0
[   163.761] 	PhysBasePtr: 0xd0000000
[   163.761] 	LinBytesPerScanLine: 1280
[   163.761] 	BnkNumberOfImagePages: 11
[   163.761] 	LinNumberOfImagePages: 11
[   163.761] 	LinRedMaskSize: 0
[   163.761] 	LinRedFieldPosition: 0
[   163.761] 	LinGreenMaskSize: 0
[   163.761] 	LinGreenFieldPosition: 0
[   163.761] 	LinBlueMaskSize: 0
[   163.761] 	LinBlueFieldPosition: 0
[   163.761] 	LinRsvdMaskSize: 0
[   163.761] 	LinRsvdFieldPosition: 0
[   163.761] 	MaxPixelClock: 400000000
[   163.762] Mode: 109 (132x25)
[   163.762] 	ModeAttributes: 0xa
[   163.762] 	WinAAttributes: 0x7
[   163.762] 	WinBAttributes: 0x0
[   163.762] 	WinGranularity: 64
[   163.762] 	WinSize: 64
[   163.762] 	WinASegment: 0xb000
[   163.762] 	WinBSegment: 0x0
[   163.762] 	WinFuncPtr: 0xc0004d11
[   163.762] 	BytesPerScanline: 160
[   163.762] 	XResolution: 132
[   163.762] 	YResolution: 25
[   163.762] 	XCharSize: 8
[   163.762] 	YCharSize: 16
[   163.762] 	NumberOfPlanes: 1
[   163.762] 	BitsPerPixel: 4
[   163.762] 	NumberOfBanks: 1
[   163.762] 	MemoryModel: 0
[   163.762] 	BankSize: 0
[   163.762] 	NumberOfImages: 2
[   163.762] 	RedMaskSize: 8
[   163.762] 	RedFieldPosition: 16
[   163.762] 	GreenMaskSize: 8
[   163.762] 	GreenFieldPosition: 8
[   163.762] 	BlueMaskSize: 8
[   163.762] 	BlueFieldPosition: 0
[   163.762] 	RsvdMaskSize: 0
[   163.762] 	RsvdFieldPosition: 0
[   163.762] 	DirectColorModeInfo: 0
[   163.762] 	PhysBasePtr: 0xd0000000
[   163.762] 	LinBytesPerScanLine: 160
[   163.762] 	BnkNumberOfImagePages: 2
[   163.762] 	LinNumberOfImagePages: 2
[   163.762] 	LinRedMaskSize: 8
[   163.762] 	LinRedFieldPosition: 16
[   163.762] 	LinGreenMaskSize: 8
[   163.762] 	LinGreenFieldPosition: 8
[   163.762] 	LinBlueMaskSize: 8
[   163.762] 	LinBlueFieldPosition: 0
[   163.762] 	LinRsvdMaskSize: 0
[   163.762] 	LinRsvdFieldPosition: 0
[   163.762] 	MaxPixelClock: 400000000
[   163.762] Mode: 10a (132x43)
[   163.762] 	ModeAttributes: 0xa
[   163.762] 	WinAAttributes: 0x7
[   163.762] 	WinBAttributes: 0x0
[   163.762] 	WinGranularity: 64
[   163.762] 	WinSize: 64
[   163.762] 	WinASegment: 0xb000
[   163.762] 	WinBSegment: 0x0
[   163.762] 	WinFuncPtr: 0xc0004d11
[   163.762] 	BytesPerScanline: 160
[   163.762] 	XResolution: 132
[   163.762] 	YResolution: 43
[   163.762] 	XCharSize: 8
[   163.762] 	YCharSize: 16
[   163.762] 	NumberOfPlanes: 1
[   163.762] 	BitsPerPixel: 4
[   163.762] 	NumberOfBanks: 1
[   163.762] 	MemoryModel: 0
[   163.762] 	BankSize: 0
[   163.762] 	NumberOfImages: 2
[   163.762] 	RedMaskSize: 8
[   163.762] 	RedFieldPosition: 16
[   163.762] 	GreenMaskSize: 8
[   163.762] 	GreenFieldPosition: 8
[   163.762] 	BlueMaskSize: 8
[   163.762] 	BlueFieldPosition: 0
[   163.762] 	RsvdMaskSize: 0
[   163.762] 	RsvdFieldPosition: 0
[   163.762] 	DirectColorModeInfo: 0
[   163.762] 	PhysBasePtr: 0xd0000000
[   163.762] 	LinBytesPerScanLine: 160
[   163.762] 	BnkNumberOfImagePages: 2
[   163.762] 	LinNumberOfImagePages: 2
[   163.762] 	LinRedMaskSize: 8
[   163.762] 	LinRedFieldPosition: 16
[   163.762] 	LinGreenMaskSize: 8
[   163.762] 	LinGreenFieldPosition: 8
[   163.762] 	LinBlueMaskSize: 8
[   163.763] 	LinBlueFieldPosition: 0
[   163.763] 	LinRsvdMaskSize: 0
[   163.763] 	LinRsvdFieldPosition: 0
[   163.763] 	MaxPixelClock: 400000000
[   163.763] Mode: 130 (132x44)
[   163.763] 	ModeAttributes: 0xa
[   163.763] 	WinAAttributes: 0x7
[   163.763] 	WinBAttributes: 0x0
[   163.763] 	WinGranularity: 64
[   163.763] 	WinSize: 64
[   163.763] 	WinASegment: 0xb000
[   163.763] 	WinBSegment: 0x0
[   163.763] 	WinFuncPtr: 0xc0004d11
[   163.763] 	BytesPerScanline: 160
[   163.763] 	XResolution: 132
[   163.763] 	YResolution: 44
[   163.763] 	XCharSize: 8
[   163.763] 	YCharSize: 16
[   163.763] 	NumberOfPlanes: 1
[   163.763] 	BitsPerPixel: 4
[   163.763] 	NumberOfBanks: 1
[   163.763] 	MemoryModel: 0
[   163.763] 	BankSize: 0
[   163.763] 	NumberOfImages: 2
[   163.763] 	RedMaskSize: 8
[   163.763] 	RedFieldPosition: 16
[   163.763] 	GreenMaskSize: 8
[   163.763] 	GreenFieldPosition: 8
[   163.763] 	BlueMaskSize: 8
[   163.763] 	BlueFieldPosition: 0
[   163.763] 	RsvdMaskSize: 0
[   163.763] 	RsvdFieldPosition: 0
[   163.763] 	DirectColorModeInfo: 0
[   163.763] 	PhysBasePtr: 0xd0000000
[   163.763] 	LinBytesPerScanLine: 160
[   163.763] 	BnkNumberOfImagePages: 2
[   163.763] 	LinNumberOfImagePages: 2
[   163.763] 	LinRedMaskSize: 8
[   163.763] 	LinRedFieldPosition: 16
[   163.763] 	LinGreenMaskSize: 8
[   163.763] 	LinGreenFieldPosition: 8
[   163.763] 	LinBlueMaskSize: 8
[   163.763] 	LinBlueFieldPosition: 0
[   163.763] 	LinRsvdMaskSize: 0
[   163.763] 	LinRsvdFieldPosition: 0
[   163.763] 	MaxPixelClock: 400000000
[   163.763] Mode: 110 (640x480)
[   163.763] 	ModeAttributes: 0xbb
[   163.763] 	WinAAttributes: 0x7
[   163.763] 	WinBAttributes: 0x0
[   163.763] 	WinGranularity: 64
[   163.763] 	WinSize: 64
[   163.763] 	WinASegment: 0xa000
[   163.763] 	WinBSegment: 0x0
[   163.763] 	WinFuncPtr: 0xc0004d11
[   163.763] 	BytesPerScanline: 1280
[   163.763] 	XResolution: 640
[   163.763] 	YResolution: 480
[   163.763] 	XCharSize: 8
[   163.763] 	YCharSize: 16
[   163.763] 	NumberOfPlanes: 1
[   163.763] 	BitsPerPixel: 16
[   163.764] 	NumberOfBanks: 1
[   163.764] 	MemoryModel: 6
[   163.764] 	BankSize: 0
[   163.764] 	NumberOfImages: 24
[   163.764] 	RedMaskSize: 5
[   163.764] 	RedFieldPosition: 10
[   163.764] 	GreenMaskSize: 5
[   163.764] 	GreenFieldPosition: 5
[   163.764] 	BlueMaskSize: 5
[   163.764] 	BlueFieldPosition: 0
[   163.764] 	RsvdMaskSize: 0
[   163.764] 	RsvdFieldPosition: 0
[   163.764] 	DirectColorModeInfo: 0
[   163.764] 	PhysBasePtr: 0xd0000000
[   163.764] 	LinBytesPerScanLine: 1280
[   163.764] 	BnkNumberOfImagePages: 24
[   163.764] 	LinNumberOfImagePages: 24
[   163.764] 	LinRedMaskSize: 5
[   163.764] 	LinRedFieldPosition: 10
[   163.764] 	LinGreenMaskSize: 5
[   163.764] 	LinGreenFieldPosition: 5
[   163.764] 	LinBlueMaskSize: 5
[   163.764] 	LinBlueFieldPosition: 0
[   163.764] 	LinRsvdMaskSize: 0
[   163.764] 	LinRsvdFieldPosition: 0
[   163.764] 	MaxPixelClock: 400000000
[   163.764] Mode: 111 (640x480)
[   163.764] 	ModeAttributes: 0xbb
[   163.764] 	WinAAttributes: 0x7
[   163.764] 	WinBAttributes: 0x0
[   163.764] 	WinGranularity: 64
[   163.764] 	WinSize: 64
[   163.764] 	WinASegment: 0xa000
[   163.764] 	WinBSegment: 0x0
[   163.764] 	WinFuncPtr: 0xc0004d11
[   163.764] 	BytesPerScanline: 1280
[   163.764] 	XResolution: 640
[   163.764] 	YResolution: 480
[   163.764] 	XCharSize: 8
[   163.764] 	YCharSize: 16
[   163.764] 	NumberOfPlanes: 1
[   163.764] 	BitsPerPixel: 16
[   163.764] 	NumberOfBanks: 1
[   163.764] 	MemoryModel: 6
[   163.764] 	BankSize: 0
[   163.764] 	NumberOfImages: 24
[   163.764] 	RedMaskSize: 5
[   163.764] 	RedFieldPosition: 11
[   163.764] 	GreenMaskSize: 6
[   163.764] 	GreenFieldPosition: 5
[   163.764] 	BlueMaskSize: 5
[   163.764] 	BlueFieldPosition: 0
[   163.764] 	RsvdMaskSize: 0
[   163.764] 	RsvdFieldPosition: 0
[   163.764] 	DirectColorModeInfo: 0
[   163.764] 	PhysBasePtr: 0xd0000000
[   163.764] 	LinBytesPerScanLine: 1280
[   163.764] 	BnkNumberOfImagePages: 24
[   163.764] 	LinNumberOfImagePages: 24
[   163.764] 	LinRedMaskSize: 5
[   163.764] 	LinRedFieldPosition: 11
[   163.764] 	LinGreenMaskSize: 6
[   163.764] 	LinGreenFieldPosition: 5
[   163.764] 	LinBlueMaskSize: 5
[   163.764] 	LinBlueFieldPosition: 0
[   163.764] 	LinRsvdMaskSize: 0
[   163.764] 	LinRsvdFieldPosition: 0
[   163.764] 	MaxPixelClock: 400000000
[   163.765] *Mode: 112 (640x480)
[   163.765] 	ModeAttributes: 0xbb
[   163.765] 	WinAAttributes: 0x7
[   163.765] 	WinBAttributes: 0x0
[   163.765] 	WinGranularity: 64
[   163.765] 	WinSize: 64
[   163.765] 	WinASegment: 0xa000
[   163.765] 	WinBSegment: 0x0
[   163.765] 	WinFuncPtr: 0xc0004d11
[   163.765] 	BytesPerScanline: 2560
[   163.765] 	XResolution: 640
[   163.765] 	YResolution: 480
[   163.765] 	XCharSize: 8
[   163.765] 	YCharSize: 16
[   163.765] 	NumberOfPlanes: 1
[   163.765] 	BitsPerPixel: 32
[   163.765] 	NumberOfBanks: 1
[   163.765] 	MemoryModel: 6
[   163.765] 	BankSize: 0
[   163.765] 	NumberOfImages: 12
[   163.765] 	RedMaskSize: 8
[   163.765] 	RedFieldPosition: 16
[   163.765] 	GreenMaskSize: 8
[   163.765] 	GreenFieldPosition: 8
[   163.765] 	BlueMaskSize: 8
[   163.765] 	BlueFieldPosition: 0
[   163.765] 	RsvdMaskSize: 0
[   163.765] 	RsvdFieldPosition: 0
[   163.765] 	DirectColorModeInfo: 0
[   163.765] 	PhysBasePtr: 0xd0000000
[   163.765] 	LinBytesPerScanLine: 2560
[   163.765] 	BnkNumberOfImagePages: 12
[   163.765] 	LinNumberOfImagePages: 12
[   163.765] 	LinRedMaskSize: 8
[   163.765] 	LinRedFieldPosition: 16
[   163.765] 	LinGreenMaskSize: 8
[   163.765] 	LinGreenFieldPosition: 8
[   163.765] 	LinBlueMaskSize: 8
[   163.765] 	LinBlueFieldPosition: 0
[   163.765] 	LinRsvdMaskSize: 0
[   163.765] 	LinRsvdFieldPosition: 0
[   163.765] 	MaxPixelClock: 400000000
[   163.765] Mode: 113 (800x600)
[   163.765] 	ModeAttributes: 0xbb
[   163.765] 	WinAAttributes: 0x7
[   163.765] 	WinBAttributes: 0x0
[   163.765] 	WinGranularity: 64
[   163.765] 	WinSize: 64
[   163.765] 	WinASegment: 0xa000
[   163.765] 	WinBSegment: 0x0
[   163.765] 	WinFuncPtr: 0xc0004d11
[   163.765] 	BytesPerScanline: 1600
[   163.765] 	XResolution: 800
[   163.765] 	YResolution: 600
[   163.765] 	XCharSize: 8
[   163.765] 	YCharSize: 14
[   163.765] 	NumberOfPlanes: 1
[   163.765] 	BitsPerPixel: 16
[   163.765] 	NumberOfBanks: 1
[   163.765] 	MemoryModel: 6
[   163.765] 	BankSize: 0
[   163.765] 	NumberOfImages: 16
[   163.765] 	RedMaskSize: 5
[   163.765] 	RedFieldPosition: 10
[   163.765] 	GreenMaskSize: 5
[   163.765] 	GreenFieldPosition: 5
[   163.765] 	BlueMaskSize: 5
[   163.765] 	BlueFieldPosition: 0
[   163.765] 	RsvdMaskSize: 0
[   163.765] 	RsvdFieldPosition: 0
[   163.766] 	DirectColorModeInfo: 0
[   163.766] 	PhysBasePtr: 0xd0000000
[   163.766] 	LinBytesPerScanLine: 1600
[   163.766] 	BnkNumberOfImagePages: 16
[   163.766] 	LinNumberOfImagePages: 16
[   163.766] 	LinRedMaskSize: 5
[   163.766] 	LinRedFieldPosition: 10
[   163.766] 	LinGreenMaskSize: 5
[   163.766] 	LinGreenFieldPosition: 5
[   163.766] 	LinBlueMaskSize: 5
[   163.766] 	LinBlueFieldPosition: 0
[   163.766] 	LinRsvdMaskSize: 0
[   163.766] 	LinRsvdFieldPosition: 0
[   163.766] 	MaxPixelClock: 400000000
[   163.766] Mode: 114 (800x600)
[   163.766] 	ModeAttributes: 0xbb
[   163.766] 	WinAAttributes: 0x7
[   163.766] 	WinBAttributes: 0x0
[   163.766] 	WinGranularity: 64
[   163.766] 	WinSize: 64
[   163.766] 	WinASegment: 0xa000
[   163.766] 	WinBSegment: 0x0
[   163.766] 	WinFuncPtr: 0xc0004d11
[   163.766] 	BytesPerScanline: 1600
[   163.766] 	XResolution: 800
[   163.766] 	YResolution: 600
[   163.766] 	XCharSize: 8
[   163.766] 	YCharSize: 14
[   163.766] 	NumberOfPlanes: 1
[   163.766] 	BitsPerPixel: 16
[   163.766] 	NumberOfBanks: 1
[   163.766] 	MemoryModel: 6
[   163.766] 	BankSize: 0
[   163.766] 	NumberOfImages: 16
[   163.766] 	RedMaskSize: 5
[   163.766] 	RedFieldPosition: 11
[   163.766] 	GreenMaskSize: 6
[   163.766] 	GreenFieldPosition: 5
[   163.766] 	BlueMaskSize: 5
[   163.766] 	BlueFieldPosition: 0
[   163.766] 	RsvdMaskSize: 0
[   163.766] 	RsvdFieldPosition: 0
[   163.766] 	DirectColorModeInfo: 0
[   163.766] 	PhysBasePtr: 0xd0000000
[   163.766] 	LinBytesPerScanLine: 1600
[   163.766] 	BnkNumberOfImagePages: 16
[   163.766] 	LinNumberOfImagePages: 16
[   163.766] 	LinRedMaskSize: 5
[   163.766] 	LinRedFieldPosition: 11
[   163.766] 	LinGreenMaskSize: 6
[   163.766] 	LinGreenFieldPosition: 5
[   163.766] 	LinBlueMaskSize: 5
[   163.766] 	LinBlueFieldPosition: 0
[   163.766] 	LinRsvdMaskSize: 0
[   163.766] 	LinRsvdFieldPosition: 0
[   163.766] 	MaxPixelClock: 400000000
[   163.767] *Mode: 115 (800x600)
[   163.767] 	ModeAttributes: 0xbb
[   163.767] 	WinAAttributes: 0x7
[   163.767] 	WinBAttributes: 0x0
[   163.767] 	WinGranularity: 64
[   163.767] 	WinSize: 64
[   163.767] 	WinASegment: 0xa000
[   163.767] 	WinBSegment: 0x0
[   163.767] 	WinFuncPtr: 0xc0004d11
[   163.767] 	BytesPerScanline: 3200
[   163.767] 	XResolution: 800
[   163.767] 	YResolution: 600
[   163.767] 	XCharSize: 8
[   163.767] 	YCharSize: 14
[   163.767] 	NumberOfPlanes: 1
[   163.767] 	BitsPerPixel: 32
[   163.767] 	NumberOfBanks: 1
[   163.767] 	MemoryModel: 6
[   163.767] 	BankSize: 0
[   163.767] 	NumberOfImages: 7
[   163.767] 	RedMaskSize: 8
[   163.767] 	RedFieldPosition: 16
[   163.767] 	GreenMaskSize: 8
[   163.767] 	GreenFieldPosition: 8
[   163.767] 	BlueMaskSize: 8
[   163.767] 	BlueFieldPosition: 0
[   163.767] 	RsvdMaskSize: 0
[   163.767] 	RsvdFieldPosition: 0
[   163.767] 	DirectColorModeInfo: 0
[   163.767] 	PhysBasePtr: 0xd0000000
[   163.767] 	LinBytesPerScanLine: 3200
[   163.767] 	BnkNumberOfImagePages: 7
[   163.767] 	LinNumberOfImagePages: 7
[   163.767] 	LinRedMaskSize: 8
[   163.767] 	LinRedFieldPosition: 16
[   163.767] 	LinGreenMaskSize: 8
[   163.767] 	LinGreenFieldPosition: 8
[   163.767] 	LinBlueMaskSize: 8
[   163.767] 	LinBlueFieldPosition: 0
[   163.767] 	LinRsvdMaskSize: 0
[   163.767] 	LinRsvdFieldPosition: 0
[   163.767] 	MaxPixelClock: 400000000
[   163.767] Mode: 116 (1024x768)
[   163.767] 	ModeAttributes: 0xbb
[   163.767] 	WinAAttributes: 0x7
[   163.767] 	WinBAttributes: 0x0
[   163.767] 	WinGranularity: 64
[   163.767] 	WinSize: 64
[   163.767] 	WinASegment: 0xa000
[   163.767] 	WinBSegment: 0x0
[   163.767] 	WinFuncPtr: 0xc0004d11
[   163.767] 	BytesPerScanline: 2048
[   163.767] 	XResolution: 1024
[   163.767] 	YResolution: 768
[   163.767] 	XCharSize: 8
[   163.767] 	YCharSize: 16
[   163.767] 	NumberOfPlanes: 1
[   163.767] 	BitsPerPixel: 16
[   163.767] 	NumberOfBanks: 1
[   163.767] 	MemoryModel: 6
[   163.767] 	BankSize: 0
[   163.767] 	NumberOfImages: 9
[   163.767] 	RedMaskSize: 5
[   163.767] 	RedFieldPosition: 10
[   163.767] 	GreenMaskSize: 5
[   163.767] 	GreenFieldPosition: 5
[   163.767] 	BlueMaskSize: 5
[   163.767] 	BlueFieldPosition: 0
[   163.767] 	RsvdMaskSize: 0
[   163.767] 	RsvdFieldPosition: 0
[   163.767] 	DirectColorModeInfo: 0
[   163.767] 	PhysBasePtr: 0xd0000000
[   163.767] 	LinBytesPerScanLine: 2048
[   163.767] 	BnkNumberOfImagePages: 9
[   163.767] 	LinNumberOfImagePages: 9
[   163.767] 	LinRedMaskSize: 5
[   163.767] 	LinRedFieldPosition: 10
[   163.767] 	LinGreenMaskSize: 5
[   163.768] 	LinGreenFieldPosition: 5
[   163.768] 	LinBlueMaskSize: 5
[   163.768] 	LinBlueFieldPosition: 0
[   163.768] 	LinRsvdMaskSize: 0
[   163.768] 	LinRsvdFieldPosition: 0
[   163.768] 	MaxPixelClock: 400000000
[   163.768] Mode: 117 (1024x768)
[   163.768] 	ModeAttributes: 0xbb
[   163.768] 	WinAAttributes: 0x7
[   163.768] 	WinBAttributes: 0x0
[   163.768] 	WinGranularity: 64
[   163.768] 	WinSize: 64
[   163.768] 	WinASegment: 0xa000
[   163.768] 	WinBSegment: 0x0
[   163.768] 	WinFuncPtr: 0xc0004d11
[   163.768] 	BytesPerScanline: 2048
[   163.768] 	XResolution: 1024
[   163.768] 	YResolution: 768
[   163.768] 	XCharSize: 8
[   163.768] 	YCharSize: 16
[   163.768] 	NumberOfPlanes: 1
[   163.768] 	BitsPerPixel: 16
[   163.768] 	NumberOfBanks: 1
[   163.768] 	MemoryModel: 6
[   163.768] 	BankSize: 0
[   163.768] 	NumberOfImages: 9
[   163.768] 	RedMaskSize: 5
[   163.768] 	RedFieldPosition: 11
[   163.768] 	GreenMaskSize: 6
[   163.768] 	GreenFieldPosition: 5
[   163.768] 	BlueMaskSize: 5
[   163.768] 	BlueFieldPosition: 0
[   163.768] 	RsvdMaskSize: 0
[   163.768] 	RsvdFieldPosition: 0
[   163.768] 	DirectColorModeInfo: 0
[   163.768] 	PhysBasePtr: 0xd0000000
[   163.768] 	LinBytesPerScanLine: 2048
[   163.768] 	BnkNumberOfImagePages: 9
[   163.768] 	LinNumberOfImagePages: 9
[   163.768] 	LinRedMaskSize: 5
[   163.768] 	LinRedFieldPosition: 11
[   163.768] 	LinGreenMaskSize: 6
[   163.768] 	LinGreenFieldPosition: 5
[   163.768] 	LinBlueMaskSize: 5
[   163.768] 	LinBlueFieldPosition: 0
[   163.768] 	LinRsvdMaskSize: 0
[   163.768] 	LinRsvdFieldPosition: 0
[   163.768] 	MaxPixelClock: 400000000
[   163.768] *Mode: 118 (1024x768)
[   163.768] 	ModeAttributes: 0xbb
[   163.768] 	WinAAttributes: 0x7
[   163.768] 	WinBAttributes: 0x0
[   163.768] 	WinGranularity: 64
[   163.768] 	WinSize: 64
[   163.768] 	WinASegment: 0xa000
[   163.768] 	WinBSegment: 0x0
[   163.769] 	WinFuncPtr: 0xc0004d11
[   163.769] 	BytesPerScanline: 4096
[   163.769] 	XResolution: 1024
[   163.769] 	YResolution: 768
[   163.769] 	XCharSize: 8
[   163.769] 	YCharSize: 16
[   163.769] 	NumberOfPlanes: 1
[   163.769] 	BitsPerPixel: 32
[   163.769] 	NumberOfBanks: 1
[   163.769] 	MemoryModel: 6
[   163.769] 	BankSize: 0
[   163.769] 	NumberOfImages: 4
[   163.769] 	RedMaskSize: 8
[   163.769] 	RedFieldPosition: 16
[   163.769] 	GreenMaskSize: 8
[   163.769] 	GreenFieldPosition: 8
[   163.769] 	BlueMaskSize: 8
[   163.769] 	BlueFieldPosition: 0
[   163.769] 	RsvdMaskSize: 0
[   163.769] 	RsvdFieldPosition: 0
[   163.769] 	DirectColorModeInfo: 0
[   163.769] 	PhysBasePtr: 0xd0000000
[   163.769] 	LinBytesPerScanLine: 4096
[   163.769] 	BnkNumberOfImagePages: 4
[   163.769] 	LinNumberOfImagePages: 4
[   163.769] 	LinRedMaskSize: 8
[   163.769] 	LinRedFieldPosition: 16
[   163.769] 	LinGreenMaskSize: 8
[   163.769] 	LinGreenFieldPosition: 8
[   163.769] 	LinBlueMaskSize: 8
[   163.769] 	LinBlueFieldPosition: 0
[   163.769] 	LinRsvdMaskSize: 0
[   163.769] 	LinRsvdFieldPosition: 0
[   163.769] 	MaxPixelClock: 400000000
[   163.769] Mode: 119 (1280x1024)
[   163.769] 	ModeAttributes: 0xbb
[   163.769] 	WinAAttributes: 0x7
[   163.769] 	WinBAttributes: 0x0
[   163.769] 	WinGranularity: 64
[   163.769] 	WinSize: 64
[   163.769] 	WinASegment: 0xa000
[   163.769] 	WinBSegment: 0x0
[   163.769] 	WinFuncPtr: 0xc0004d11
[   163.769] 	BytesPerScanline: 2560
[   163.769] 	XResolution: 1280
[   163.769] 	YResolution: 1024
[   163.769] 	XCharSize: 8
[   163.769] 	YCharSize: 16
[   163.769] 	NumberOfPlanes: 1
[   163.769] 	BitsPerPixel: 16
[   163.769] 	NumberOfBanks: 1
[   163.769] 	MemoryModel: 6
[   163.769] 	BankSize: 0
[   163.769] 	NumberOfImages: 5
[   163.769] 	RedMaskSize: 5
[   163.769] 	RedFieldPosition: 10
[   163.769] 	GreenMaskSize: 5
[   163.769] 	GreenFieldPosition: 5
[   163.769] 	BlueMaskSize: 5
[   163.769] 	BlueFieldPosition: 0
[   163.769] 	RsvdMaskSize: 0
[   163.769] 	RsvdFieldPosition: 0
[   163.769] 	DirectColorModeInfo: 0
[   163.769] 	PhysBasePtr: 0xd0000000
[   163.769] 	LinBytesPerScanLine: 2560
[   163.769] 	BnkNumberOfImagePages: 5
[   163.769] 	LinNumberOfImagePages: 5
[   163.769] 	LinRedMaskSize: 5
[   163.769] 	LinRedFieldPosition: 10
[   163.769] 	LinGreenMaskSize: 5
[   163.769] 	LinGreenFieldPosition: 5
[   163.769] 	LinBlueMaskSize: 5
[   163.769] 	LinBlueFieldPosition: 0
[   163.769] 	LinRsvdMaskSize: 0
[   163.769] 	LinRsvdFieldPosition: 0
[   163.769] 	MaxPixelClock: 400000000
[   163.770] Mode: 11a (1280x1024)
[   163.770] 	ModeAttributes: 0xbb
[   163.770] 	WinAAttributes: 0x7
[   163.770] 	WinBAttributes: 0x0
[   163.770] 	WinGranularity: 64
[   163.770] 	WinSize: 64
[   163.770] 	WinASegment: 0xa000
[   163.770] 	WinBSegment: 0x0
[   163.770] 	WinFuncPtr: 0xc0004d11
[   163.770] 	BytesPerScanline: 2560
[   163.770] 	XResolution: 1280
[   163.770] 	YResolution: 1024
[   163.770] 	XCharSize: 8
[   163.770] 	YCharSize: 16
[   163.770] 	NumberOfPlanes: 1
[   163.770] 	BitsPerPixel: 16
[   163.770] 	NumberOfBanks: 1
[   163.770] 	MemoryModel: 6
[   163.770] 	BankSize: 0
[   163.770] 	NumberOfImages: 5
[   163.770] 	RedMaskSize: 5
[   163.770] 	RedFieldPosition: 11
[   163.770] 	GreenMaskSize: 6
[   163.770] 	GreenFieldPosition: 5
[   163.770] 	BlueMaskSize: 5
[   163.770] 	BlueFieldPosition: 0
[   163.770] 	RsvdMaskSize: 0
[   163.770] 	RsvdFieldPosition: 0
[   163.770] 	DirectColorModeInfo: 0
[   163.770] 	PhysBasePtr: 0xd0000000
[   163.770] 	LinBytesPerScanLine: 2560
[   163.770] 	BnkNumberOfImagePages: 5
[   163.770] 	LinNumberOfImagePages: 5
[   163.770] 	LinRedMaskSize: 5
[   163.770] 	LinRedFieldPosition: 11
[   163.770] 	LinGreenMaskSize: 6
[   163.770] 	LinGreenFieldPosition: 5
[   163.770] 	LinBlueMaskSize: 5
[   163.770] 	LinBlueFieldPosition: 0
[   163.770] 	LinRsvdMaskSize: 0
[   163.770] 	LinRsvdFieldPosition: 0
[   163.770] 	MaxPixelClock: 400000000
[   163.770] *Mode: 11b (1280x1024)
[   163.770] 	ModeAttributes: 0xbb
[   163.770] 	WinAAttributes: 0x7
[   163.770] 	WinBAttributes: 0x0
[   163.770] 	WinGranularity: 64
[   163.770] 	WinSize: 64
[   163.770] 	WinASegment: 0xa000
[   163.770] 	WinBSegment: 0x0
[   163.770] 	WinFuncPtr: 0xc0004d11
[   163.770] 	BytesPerScanline: 5120
[   163.770] 	XResolution: 1280
[   163.770] 	YResolution: 1024
[   163.770] 	XCharSize: 8
[   163.770] 	YCharSize: 16
[   163.770] 	NumberOfPlanes: 1
[   163.770] 	BitsPerPixel: 32
[   163.771] 	NumberOfBanks: 1
[   163.771] 	MemoryModel: 6
[   163.771] 	BankSize: 0
[   163.771] 	NumberOfImages: 2
[   163.771] 	RedMaskSize: 8
[   163.771] 	RedFieldPosition: 16
[   163.771] 	GreenMaskSize: 8
[   163.771] 	GreenFieldPosition: 8
[   163.771] 	BlueMaskSize: 8
[   163.771] 	BlueFieldPosition: 0
[   163.771] 	RsvdMaskSize: 0
[   163.771] 	RsvdFieldPosition: 0
[   163.771] 	DirectColorModeInfo: 0
[   163.771] 	PhysBasePtr: 0xd0000000
[   163.771] 	LinBytesPerScanLine: 5120
[   163.771] 	BnkNumberOfImagePages: 2
[   163.771] 	LinNumberOfImagePages: 2
[   163.771] 	LinRedMaskSize: 8
[   163.771] 	LinRedFieldPosition: 16
[   163.771] 	LinGreenMaskSize: 8
[   163.771] 	LinGreenFieldPosition: 8
[   163.771] 	LinBlueMaskSize: 8
[   163.771] 	LinBlueFieldPosition: 0
[   163.771] 	LinRsvdMaskSize: 0
[   163.771] 	LinRsvdFieldPosition: 0
[   163.771] 	MaxPixelClock: 400000000
[   163.771] Mode: 10d (320x200)
[   163.771] 	ModeAttributes: 0xbb
[   163.771] 	WinAAttributes: 0x7
[   163.771] 	WinBAttributes: 0x0
[   163.771] 	WinGranularity: 64
[   163.771] 	WinSize: 64
[   163.771] 	WinASegment: 0xa000
[   163.771] 	WinBSegment: 0x0
[   163.771] 	WinFuncPtr: 0xc0004d11
[   163.771] 	BytesPerScanline: 640
[   163.771] 	XResolution: 320
[   163.771] 	YResolution: 200
[   163.771] 	XCharSize: 8
[   163.771] 	YCharSize: 8
[   163.771] 	NumberOfPlanes: 1
[   163.771] 	BitsPerPixel: 16
[   163.771] 	NumberOfBanks: 1
[   163.771] 	MemoryModel: 6
[   163.771] 	BankSize: 0
[   163.771] 	NumberOfImages: 127
[   163.771] 	RedMaskSize: 5
[   163.771] 	RedFieldPosition: 10
[   163.771] 	GreenMaskSize: 5
[   163.771] 	GreenFieldPosition: 5
[   163.771] 	BlueMaskSize: 5
[   163.771] 	BlueFieldPosition: 0
[   163.771] 	RsvdMaskSize: 0
[   163.771] 	RsvdFieldPosition: 0
[   163.771] 	DirectColorModeInfo: 0
[   163.771] 	PhysBasePtr: 0xd0000000
[   163.771] 	LinBytesPerScanLine: 640
[   163.771] 	BnkNumberOfImagePages: 127
[   163.771] 	LinNumberOfImagePages: 127
[   163.771] 	LinRedMaskSize: 5
[   163.771] 	LinRedFieldPosition: 10
[   163.771] 	LinGreenMaskSize: 5
[   163.771] 	LinGreenFieldPosition: 5
[   163.771] 	LinBlueMaskSize: 5
[   163.771] 	LinBlueFieldPosition: 0
[   163.771] 	LinRsvdMaskSize: 0
[   163.771] 	LinRsvdFieldPosition: 0
[   163.771] 	MaxPixelClock: 400000000
[   163.772] Mode: 10e (320x200)
[   163.772] 	ModeAttributes: 0xbb
[   163.772] 	WinAAttributes: 0x7
[   163.772] 	WinBAttributes: 0x0
[   163.772] 	WinGranularity: 64
[   163.772] 	WinSize: 64
[   163.772] 	WinASegment: 0xa000
[   163.772] 	WinBSegment: 0x0
[   163.772] 	WinFuncPtr: 0xc0004d11
[   163.772] 	BytesPerScanline: 640
[   163.772] 	XResolution: 320
[   163.772] 	YResolution: 200
[   163.772] 	XCharSize: 8
[   163.772] 	YCharSize: 8
[   163.772] 	NumberOfPlanes: 1
[   163.772] 	BitsPerPixel: 16
[   163.772] 	NumberOfBanks: 1
[   163.772] 	MemoryModel: 6
[   163.772] 	BankSize: 0
[   163.772] 	NumberOfImages: 127
[   163.772] 	RedMaskSize: 5
[   163.772] 	RedFieldPosition: 11
[   163.772] 	GreenMaskSize: 6
[   163.772] 	GreenFieldPosition: 5
[   163.772] 	BlueMaskSize: 5
[   163.772] 	BlueFieldPosition: 0
[   163.772] 	RsvdMaskSize: 0
[   163.772] 	RsvdFieldPosition: 0
[   163.772] 	DirectColorModeInfo: 0
[   163.772] 	PhysBasePtr: 0xd0000000
[   163.772] 	LinBytesPerScanLine: 640
[   163.772] 	BnkNumberOfImagePages: 127
[   163.772] 	LinNumberOfImagePages: 127
[   163.772] 	LinRedMaskSize: 5
[   163.772] 	LinRedFieldPosition: 11
[   163.772] 	LinGreenMaskSize: 6
[   163.772] 	LinGreenFieldPosition: 5
[   163.772] 	LinBlueMaskSize: 5
[   163.772] 	LinBlueFieldPosition: 0
[   163.772] 	LinRsvdMaskSize: 0
[   163.772] 	LinRsvdFieldPosition: 0
[   163.772] 	MaxPixelClock: 400000000
[   163.772] *Mode: 10f (320x200)
[   163.772] 	ModeAttributes: 0xbb
[   163.772] 	WinAAttributes: 0x7
[   163.772] 	WinBAttributes: 0x0
[   163.772] 	WinGranularity: 64
[   163.772] 	WinSize: 64
[   163.772] 	WinASegment: 0xa000
[   163.772] 	WinBSegment: 0x0
[   163.772] 	WinFuncPtr: 0xc0004d11
[   163.772] 	BytesPerScanline: 1280
[   163.772] 	XResolution: 320
[   163.772] 	YResolution: 200
[   163.772] 	XCharSize: 8
[   163.772] 	YCharSize: 8
[   163.772] 	NumberOfPlanes: 1
[   163.772] 	BitsPerPixel: 32
[   163.772] 	NumberOfBanks: 1
[   163.772] 	MemoryModel: 6
[   163.772] 	BankSize: 0
[   163.772] 	NumberOfImages: 63
[   163.772] 	RedMaskSize: 8
[   163.772] 	RedFieldPosition: 16
[   163.772] 	GreenMaskSize: 8
[   163.772] 	GreenFieldPosition: 8
[   163.772] 	BlueMaskSize: 8
[   163.773] 	BlueFieldPosition: 0
[   163.773] 	RsvdMaskSize: 0
[   163.773] 	RsvdFieldPosition: 0
[   163.773] 	DirectColorModeInfo: 0
[   163.773] 	PhysBasePtr: 0xd0000000
[   163.773] 	LinBytesPerScanLine: 1280
[   163.773] 	BnkNumberOfImagePages: 63
[   163.773] 	LinNumberOfImagePages: 63
[   163.773] 	LinRedMaskSize: 8
[   163.773] 	LinRedFieldPosition: 16
[   163.773] 	LinGreenMaskSize: 8
[   163.773] 	LinGreenFieldPosition: 8
[   163.773] 	LinBlueMaskSize: 8
[   163.773] 	LinBlueFieldPosition: 0
[   163.773] 	LinRsvdMaskSize: 0
[   163.773] 	LinRsvdFieldPosition: 0
[   163.773] 	MaxPixelClock: 400000000
[   163.773] *Mode: 120 (320x200)
[   163.773] 	ModeAttributes: 0xbb
[   163.773] 	WinAAttributes: 0x7
[   163.773] 	WinBAttributes: 0x0
[   163.773] 	WinGranularity: 64
[   163.773] 	WinSize: 64
[   163.773] 	WinASegment: 0xa000
[   163.773] 	WinBSegment: 0x0
[   163.773] 	WinFuncPtr: 0xc0004d11
[   163.773] 	BytesPerScanline: 1280
[   163.773] 	XResolution: 320
[   163.773] 	YResolution: 200
[   163.773] 	XCharSize: 8
[   163.773] 	YCharSize: 8
[   163.773] 	NumberOfPlanes: 1
[   163.773] 	BitsPerPixel: 32
[   163.773] 	NumberOfBanks: 1
[   163.773] 	MemoryModel: 6
[   163.773] 	BankSize: 0
[   163.773] 	NumberOfImages: 63
[   163.773] 	RedMaskSize: 8
[   163.773] 	RedFieldPosition: 16
[   163.773] 	GreenMaskSize: 8
[   163.773] 	GreenFieldPosition: 8
[   163.773] 	BlueMaskSize: 8
[   163.773] 	BlueFieldPosition: 0
[   163.773] 	RsvdMaskSize: 0
[   163.773] 	RsvdFieldPosition: 0
[   163.773] 	DirectColorModeInfo: 0
[   163.773] 	PhysBasePtr: 0xd0000000
[   163.773] 	LinBytesPerScanLine: 1280
[   163.773] 	BnkNumberOfImagePages: 63
[   163.773] 	LinNumberOfImagePages: 63
[   163.773] 	LinRedMaskSize: 8
[   163.773] 	LinRedFieldPosition: 16
[   163.773] 	LinGreenMaskSize: 8
[   163.773] 	LinGreenFieldPosition: 8
[   163.773] 	LinBlueMaskSize: 8
[   163.773] 	LinBlueFieldPosition: 0
[   163.773] 	LinRsvdMaskSize: 0
[   163.773] 	LinRsvdFieldPosition: 0
[   163.773] 	MaxPixelClock: 400000000
[   163.774] Mode: 193 (320x240)
[   163.774] 	ModeAttributes: 0xbb
[   163.774] 	WinAAttributes: 0x7
[   163.774] 	WinBAttributes: 0x0
[   163.774] 	WinGranularity: 64
[   163.774] 	WinSize: 64
[   163.774] 	WinASegment: 0xa000
[   163.774] 	WinBSegment: 0x0
[   163.774] 	WinFuncPtr: 0xc0004d11
[   163.774] 	BytesPerScanline: 320
[   163.774] 	XResolution: 320
[   163.774] 	YResolution: 240
[   163.774] 	XCharSize: 8
[   163.774] 	YCharSize: 8
[   163.774] 	NumberOfPlanes: 1
[   163.774] 	BitsPerPixel: 8
[   163.774] 	NumberOfBanks: 1
[   163.774] 	MemoryModel: 4
[   163.774] 	BankSize: 0
[   163.774] 	NumberOfImages: 127
[   163.774] 	RedMaskSize: 0
[   163.774] 	RedFieldPosition: 0
[   163.774] 	GreenMaskSize: 0
[   163.774] 	GreenFieldPosition: 0
[   163.774] 	BlueMaskSize: 0
[   163.774] 	BlueFieldPosition: 0
[   163.774] 	RsvdMaskSize: 0
[   163.774] 	RsvdFieldPosition: 0
[   163.774] 	DirectColorModeInfo: 0
[   163.774] 	PhysBasePtr: 0xd0000000
[   163.774] 	LinBytesPerScanLine: 320
[   163.774] 	BnkNumberOfImagePages: 127
[   163.774] 	LinNumberOfImagePages: 127
[   163.774] 	LinRedMaskSize: 0
[   163.774] 	LinRedFieldPosition: 0
[   163.774] 	LinGreenMaskSize: 0
[   163.774] 	LinGreenFieldPosition: 0
[   163.774] 	LinBlueMaskSize: 0
[   163.774] 	LinBlueFieldPosition: 0
[   163.774] 	LinRsvdMaskSize: 0
[   163.774] 	LinRsvdFieldPosition: 0
[   163.774] 	MaxPixelClock: 400000000
[   163.774] Mode: 194 (320x240)
[   163.774] 	ModeAttributes: 0xbb
[   163.774] 	WinAAttributes: 0x7
[   163.774] 	WinBAttributes: 0x0
[   163.774] 	WinGranularity: 64
[   163.774] 	WinSize: 64
[   163.774] 	WinASegment: 0xa000
[   163.774] 	WinBSegment: 0x0
[   163.774] 	WinFuncPtr: 0xc0004d11
[   163.774] 	BytesPerScanline: 640
[   163.774] 	XResolution: 320
[   163.774] 	YResolution: 240
[   163.774] 	XCharSize: 8
[   163.774] 	YCharSize: 8
[   163.774] 	NumberOfPlanes: 1
[   163.774] 	BitsPerPixel: 16
[   163.774] 	NumberOfBanks: 1
[   163.774] 	MemoryModel: 6
[   163.774] 	BankSize: 0
[   163.774] 	NumberOfImages: 84
[   163.774] 	RedMaskSize: 5
[   163.774] 	RedFieldPosition: 10
[   163.774] 	GreenMaskSize: 5
[   163.774] 	GreenFieldPosition: 5
[   163.774] 	BlueMaskSize: 5
[   163.774] 	BlueFieldPosition: 0
[   163.774] 	RsvdMaskSize: 0
[   163.774] 	RsvdFieldPosition: 0
[   163.774] 	DirectColorModeInfo: 0
[   163.774] 	PhysBasePtr: 0xd0000000
[   163.774] 	LinBytesPerScanLine: 640
[   163.774] 	BnkNumberOfImagePages: 84
[   163.774] 	LinNumberOfImagePages: 84
[   163.774] 	LinRedMaskSize: 5
[   163.774] 	LinRedFieldPosition: 10
[   163.774] 	LinGreenMaskSize: 5
[   163.774] 	LinGreenFieldPosition: 5
[   163.775] 	LinBlueMaskSize: 5
[   163.775] 	LinBlueFieldPosition: 0
[   163.775] 	LinRsvdMaskSize: 0
[   163.775] 	LinRsvdFieldPosition: 0
[   163.775] 	MaxPixelClock: 400000000
[   163.775] Mode: 195 (320x240)
[   163.775] 	ModeAttributes: 0xbb
[   163.775] 	WinAAttributes: 0x7
[   163.775] 	WinBAttributes: 0x0
[   163.775] 	WinGranularity: 64
[   163.775] 	WinSize: 64
[   163.775] 	WinASegment: 0xa000
[   163.775] 	WinBSegment: 0x0
[   163.775] 	WinFuncPtr: 0xc0004d11
[   163.775] 	BytesPerScanline: 640
[   163.775] 	XResolution: 320
[   163.775] 	YResolution: 240
[   163.775] 	XCharSize: 8
[   163.775] 	YCharSize: 8
[   163.775] 	NumberOfPlanes: 1
[   163.775] 	BitsPerPixel: 16
[   163.775] 	NumberOfBanks: 1
[   163.775] 	MemoryModel: 6
[   163.775] 	BankSize: 0
[   163.775] 	NumberOfImages: 84
[   163.775] 	RedMaskSize: 5
[   163.775] 	RedFieldPosition: 11
[   163.775] 	GreenMaskSize: 6
[   163.775] 	GreenFieldPosition: 5
[   163.775] 	BlueMaskSize: 5
[   163.775] 	BlueFieldPosition: 0
[   163.775] 	RsvdMaskSize: 0
[   163.775] 	RsvdFieldPosition: 0
[   163.775] 	DirectColorModeInfo: 0
[   163.775] 	PhysBasePtr: 0xd0000000
[   163.775] 	LinBytesPerScanLine: 640
[   163.775] 	BnkNumberOfImagePages: 84
[   163.775] 	LinNumberOfImagePages: 84
[   163.775] 	LinRedMaskSize: 5
[   163.775] 	LinRedFieldPosition: 11
[   163.775] 	LinGreenMaskSize: 6
[   163.775] 	LinGreenFieldPosition: 5
[   163.775] 	LinBlueMaskSize: 5
[   163.775] 	LinBlueFieldPosition: 0
[   163.775] 	LinRsvdMaskSize: 0
[   163.775] 	LinRsvdFieldPosition: 0
[   163.775] 	MaxPixelClock: 400000000
[   163.775] *Mode: 196 (320x240)
[   163.775] 	ModeAttributes: 0xbb
[   163.775] 	WinAAttributes: 0x7
[   163.775] 	WinBAttributes: 0x0
[   163.775] 	WinGranularity: 64
[   163.775] 	WinSize: 64
[   163.775] 	WinASegment: 0xa000
[   163.775] 	WinBSegment: 0x0
[   163.776] 	WinFuncPtr: 0xc0004d11
[   163.776] 	BytesPerScanline: 1280
[   163.776] 	XResolution: 320
[   163.776] 	YResolution: 240
[   163.776] 	XCharSize: 8
[   163.776] 	YCharSize: 8
[   163.776] 	NumberOfPlanes: 1
[   163.776] 	BitsPerPixel: 32
[   163.776] 	NumberOfBanks: 1
[   163.776] 	MemoryModel: 6
[   163.776] 	BankSize: 0
[   163.776] 	NumberOfImages: 50
[   163.776] 	RedMaskSize: 8
[   163.776] 	RedFieldPosition: 16
[   163.776] 	GreenMaskSize: 8
[   163.776] 	GreenFieldPosition: 8
[   163.776] 	BlueMaskSize: 8
[   163.776] 	BlueFieldPosition: 0
[   163.776] 	RsvdMaskSize: 0
[   163.776] 	RsvdFieldPosition: 0
[   163.776] 	DirectColorModeInfo: 0
[   163.776] 	PhysBasePtr: 0xd0000000
[   163.776] 	LinBytesPerScanLine: 1280
[   163.776] 	BnkNumberOfImagePages: 50
[   163.776] 	LinNumberOfImagePages: 50
[   163.776] 	LinRedMaskSize: 8
[   163.776] 	LinRedFieldPosition: 16
[   163.776] 	LinGreenMaskSize: 8
[   163.776] 	LinGreenFieldPosition: 8
[   163.776] 	LinBlueMaskSize: 8
[   163.776] 	LinBlueFieldPosition: 0
[   163.776] 	LinRsvdMaskSize: 0
[   163.776] 	LinRsvdFieldPosition: 0
[   163.776] 	MaxPixelClock: 400000000
[   163.776] Mode: 1b3 (512x384)
[   163.776] 	ModeAttributes: 0xbb
[   163.776] 	WinAAttributes: 0x7
[   163.776] 	WinBAttributes: 0x0
[   163.776] 	WinGranularity: 64
[   163.776] 	WinSize: 64
[   163.776] 	WinASegment: 0xa000
[   163.776] 	WinBSegment: 0x0
[   163.776] 	WinFuncPtr: 0xc0004d11
[   163.776] 	BytesPerScanline: 512
[   163.776] 	XResolution: 512
[   163.776] 	YResolution: 384
[   163.776] 	XCharSize: 8
[   163.776] 	YCharSize: 16
[   163.776] 	NumberOfPlanes: 1
[   163.776] 	BitsPerPixel: 8
[   163.776] 	NumberOfBanks: 1
[   163.776] 	MemoryModel: 4
[   163.776] 	BankSize: 0
[   163.776] 	NumberOfImages: 63
[   163.776] 	RedMaskSize: 0
[   163.776] 	RedFieldPosition: 0
[   163.776] 	GreenMaskSize: 0
[   163.776] 	GreenFieldPosition: 0
[   163.776] 	BlueMaskSize: 0
[   163.776] 	BlueFieldPosition: 0
[   163.776] 	RsvdMaskSize: 0
[   163.776] 	RsvdFieldPosition: 0
[   163.776] 	DirectColorModeInfo: 0
[   163.776] 	PhysBasePtr: 0xd0000000
[   163.776] 	LinBytesPerScanLine: 512
[   163.776] 	BnkNumberOfImagePages: 63
[   163.776] 	LinNumberOfImagePages: 63
[   163.776] 	LinRedMaskSize: 0
[   163.776] 	LinRedFieldPosition: 0
[   163.776] 	LinGreenMaskSize: 0
[   163.776] 	LinGreenFieldPosition: 0
[   163.776] 	LinBlueMaskSize: 0
[   163.776] 	LinBlueFieldPosition: 0
[   163.776] 	LinRsvdMaskSize: 0
[   163.776] 	LinRsvdFieldPosition: 0
[   163.776] 	MaxPixelClock: 400000000
[   163.777] Mode: 1b4 (512x384)
[   163.777] 	ModeAttributes: 0xbb
[   163.777] 	WinAAttributes: 0x7
[   163.777] 	WinBAttributes: 0x0
[   163.777] 	WinGranularity: 64
[   163.777] 	WinSize: 64
[   163.777] 	WinASegment: 0xa000
[   163.777] 	WinBSegment: 0x0
[   163.777] 	WinFuncPtr: 0xc0004d11
[   163.777] 	BytesPerScanline: 1024
[   163.777] 	XResolution: 512
[   163.777] 	YResolution: 384
[   163.777] 	XCharSize: 8
[   163.777] 	YCharSize: 16
[   163.777] 	NumberOfPlanes: 1
[   163.777] 	BitsPerPixel: 16
[   163.777] 	NumberOfBanks: 1
[   163.777] 	MemoryModel: 6
[   163.777] 	BankSize: 0
[   163.777] 	NumberOfImages: 35
[   163.777] 	RedMaskSize: 5
[   163.777] 	RedFieldPosition: 10
[   163.777] 	GreenMaskSize: 5
[   163.777] 	GreenFieldPosition: 5
[   163.777] 	BlueMaskSize: 5
[   163.777] 	BlueFieldPosition: 0
[   163.777] 	RsvdMaskSize: 0
[   163.777] 	RsvdFieldPosition: 0
[   163.777] 	DirectColorModeInfo: 0
[   163.777] 	PhysBasePtr: 0xd0000000
[   163.777] 	LinBytesPerScanLine: 1024
[   163.777] 	BnkNumberOfImagePages: 35
[   163.777] 	LinNumberOfImagePages: 35
[   163.777] 	LinRedMaskSize: 5
[   163.777] 	LinRedFieldPosition: 10
[   163.777] 	LinGreenMaskSize: 5
[   163.777] 	LinGreenFieldPosition: 5
[   163.777] 	LinBlueMaskSize: 5
[   163.777] 	LinBlueFieldPosition: 0
[   163.777] 	LinRsvdMaskSize: 0
[   163.777] 	LinRsvdFieldPosition: 0
[   163.777] 	MaxPixelClock: 400000000
[   163.777] Mode: 1b5 (512x384)
[   163.777] 	ModeAttributes: 0xbb
[   163.777] 	WinAAttributes: 0x7
[   163.777] 	WinBAttributes: 0x0
[   163.777] 	WinGranularity: 64
[   163.777] 	WinSize: 64
[   163.777] 	WinASegment: 0xa000
[   163.777] 	WinBSegment: 0x0
[   163.777] 	WinFuncPtr: 0xc0004d11
[   163.777] 	BytesPerScanline: 1024
[   163.777] 	XResolution: 512
[   163.777] 	YResolution: 384
[   163.777] 	XCharSize: 8
[   163.777] 	YCharSize: 16
[   163.777] 	NumberOfPlanes: 1
[   163.778] 	BitsPerPixel: 16
[   163.778] 	NumberOfBanks: 1
[   163.778] 	MemoryModel: 6
[   163.778] 	BankSize: 0
[   163.778] 	NumberOfImages: 35
[   163.778] 	RedMaskSize: 5
[   163.778] 	RedFieldPosition: 11
[   163.778] 	GreenMaskSize: 6
[   163.778] 	GreenFieldPosition: 5
[   163.778] 	BlueMaskSize: 5
[   163.778] 	BlueFieldPosition: 0
[   163.778] 	RsvdMaskSize: 0
[   163.778] 	RsvdFieldPosition: 0
[   163.778] 	DirectColorModeInfo: 0
[   163.778] 	PhysBasePtr: 0xd0000000
[   163.778] 	LinBytesPerScanLine: 1024
[   163.778] 	BnkNumberOfImagePages: 35
[   163.778] 	LinNumberOfImagePages: 35
[   163.778] 	LinRedMaskSize: 5
[   163.778] 	LinRedFieldPosition: 11
[   163.778] 	LinGreenMaskSize: 6
[   163.778] 	LinGreenFieldPosition: 5
[   163.778] 	LinBlueMaskSize: 5
[   163.778] 	LinBlueFieldPosition: 0
[   163.778] 	LinRsvdMaskSize: 0
[   163.778] 	LinRsvdFieldPosition: 0
[   163.778] 	MaxPixelClock: 400000000
[   163.778] *Mode: 1b6 (512x384)
[   163.778] 	ModeAttributes: 0xbb
[   163.778] 	WinAAttributes: 0x7
[   163.778] 	WinBAttributes: 0x0
[   163.778] 	WinGranularity: 64
[   163.778] 	WinSize: 64
[   163.778] 	WinASegment: 0xa000
[   163.778] 	WinBSegment: 0x0
[   163.778] 	WinFuncPtr: 0xc0004d11
[   163.778] 	BytesPerScanline: 2048
[   163.778] 	XResolution: 512
[   163.778] 	YResolution: 384
[   163.778] 	XCharSize: 8
[   163.778] 	YCharSize: 16
[   163.778] 	NumberOfPlanes: 1
[   163.778] 	BitsPerPixel: 32
[   163.778] 	NumberOfBanks: 1
[   163.778] 	MemoryModel: 6
[   163.778] 	BankSize: 0
[   163.778] 	NumberOfImages: 18
[   163.778] 	RedMaskSize: 8
[   163.778] 	RedFieldPosition: 16
[   163.778] 	GreenMaskSize: 8
[   163.778] 	GreenFieldPosition: 8
[   163.778] 	BlueMaskSize: 8
[   163.778] 	BlueFieldPosition: 0
[   163.778] 	RsvdMaskSize: 0
[   163.778] 	RsvdFieldPosition: 0
[   163.778] 	DirectColorModeInfo: 0
[   163.778] 	PhysBasePtr: 0xd0000000
[   163.778] 	LinBytesPerScanLine: 2048
[   163.778] 	BnkNumberOfImagePages: 18
[   163.778] 	LinNumberOfImagePages: 18
[   163.778] 	LinRedMaskSize: 8
[   163.778] 	LinRedFieldPosition: 16
[   163.778] 	LinGreenMaskSize: 8
[   163.778] 	LinGreenFieldPosition: 8
[   163.778] 	LinBlueMaskSize: 8
[   163.778] 	LinBlueFieldPosition: 0
[   163.778] 	LinRsvdMaskSize: 0
[   163.778] 	LinRsvdFieldPosition: 0
[   163.778] 	MaxPixelClock: 400000000
[   163.779] Mode: 1c3 (640x350)
[   163.779] 	ModeAttributes: 0xbb
[   163.779] 	WinAAttributes: 0x7
[   163.779] 	WinBAttributes: 0x0
[   163.779] 	WinGranularity: 64
[   163.779] 	WinSize: 64
[   163.779] 	WinASegment: 0xa000
[   163.779] 	WinBSegment: 0x0
[   163.779] 	WinFuncPtr: 0xc0004d11
[   163.779] 	BytesPerScanline: 640
[   163.779] 	XResolution: 640
[   163.779] 	YResolution: 350
[   163.779] 	XCharSize: 8
[   163.779] 	YCharSize: 14
[   163.779] 	NumberOfPlanes: 1
[   163.779] 	BitsPerPixel: 8
[   163.779] 	NumberOfBanks: 1
[   163.779] 	MemoryModel: 4
[   163.779] 	BankSize: 0
[   163.779] 	NumberOfImages: 63
[   163.779] 	RedMaskSize: 0
[   163.779] 	RedFieldPosition: 0
[   163.779] 	GreenMaskSize: 0
[   163.779] 	GreenFieldPosition: 0
[   163.779] 	BlueMaskSize: 0
[   163.779] 	BlueFieldPosition: 0
[   163.779] 	RsvdMaskSize: 0
[   163.779] 	RsvdFieldPosition: 0
[   163.779] 	DirectColorModeInfo: 0
[   163.779] 	PhysBasePtr: 0xd0000000
[   163.779] 	LinBytesPerScanLine: 640
[   163.779] 	BnkNumberOfImagePages: 63
[   163.779] 	LinNumberOfImagePages: 63
[   163.779] 	LinRedMaskSize: 0
[   163.779] 	LinRedFieldPosition: 0
[   163.779] 	LinGreenMaskSize: 0
[   163.779] 	LinGreenFieldPosition: 0
[   163.779] 	LinBlueMaskSize: 0
[   163.779] 	LinBlueFieldPosition: 0
[   163.779] 	LinRsvdMaskSize: 0
[   163.779] 	LinRsvdFieldPosition: 0
[   163.779] 	MaxPixelClock: 400000000
[   163.779] Mode: 1c4 (640x350)
[   163.779] 	ModeAttributes: 0xbb
[   163.779] 	WinAAttributes: 0x7
[   163.779] 	WinBAttributes: 0x0
[   163.779] 	WinGranularity: 64
[   163.779] 	WinSize: 64
[   163.779] 	WinASegment: 0xa000
[   163.779] 	WinBSegment: 0x0
[   163.779] 	WinFuncPtr: 0xc0004d11
[   163.779] 	BytesPerScanline: 1280
[   163.779] 	XResolution: 640
[   163.779] 	YResolution: 350
[   163.779] 	XCharSize: 8
[   163.779] 	YCharSize: 14
[   163.779] 	NumberOfPlanes: 1
[   163.779] 	BitsPerPixel: 16
[   163.779] 	NumberOfBanks: 1
[   163.779] 	MemoryModel: 6
[   163.779] 	BankSize: 0
[   163.779] 	NumberOfImages: 35
[   163.779] 	RedMaskSize: 5
[   163.780] 	RedFieldPosition: 10
[   163.780] 	GreenMaskSize: 5
[   163.780] 	GreenFieldPosition: 5
[   163.780] 	BlueMaskSize: 5
[   163.780] 	BlueFieldPosition: 0
[   163.780] 	RsvdMaskSize: 0
[   163.780] 	RsvdFieldPosition: 0
[   163.780] 	DirectColorModeInfo: 0
[   163.780] 	PhysBasePtr: 0xd0000000
[   163.780] 	LinBytesPerScanLine: 1280
[   163.780] 	BnkNumberOfImagePages: 35
[   163.780] 	LinNumberOfImagePages: 35
[   163.780] 	LinRedMaskSize: 5
[   163.780] 	LinRedFieldPosition: 10
[   163.780] 	LinGreenMaskSize: 5
[   163.780] 	LinGreenFieldPosition: 5
[   163.780] 	LinBlueMaskSize: 5
[   163.780] 	LinBlueFieldPosition: 0
[   163.780] 	LinRsvdMaskSize: 0
[   163.780] 	LinRsvdFieldPosition: 0
[   163.780] 	MaxPixelClock: 400000000
[   163.780] Mode: 1c5 (640x350)
[   163.780] 	ModeAttributes: 0xbb
[   163.780] 	WinAAttributes: 0x7
[   163.780] 	WinBAttributes: 0x0
[   163.780] 	WinGranularity: 64
[   163.780] 	WinSize: 64
[   163.780] 	WinASegment: 0xa000
[   163.780] 	WinBSegment: 0x0
[   163.780] 	WinFuncPtr: 0xc0004d11
[   163.780] 	BytesPerScanline: 1280
[   163.780] 	XResolution: 640
[   163.780] 	YResolution: 350
[   163.780] 	XCharSize: 8
[   163.780] 	YCharSize: 14
[   163.780] 	NumberOfPlanes: 1
[   163.780] 	BitsPerPixel: 16
[   163.780] 	NumberOfBanks: 1
[   163.780] 	MemoryModel: 6
[   163.780] 	BankSize: 0
[   163.780] 	NumberOfImages: 35
[   163.780] 	RedMaskSize: 5
[   163.780] 	RedFieldPosition: 11
[   163.780] 	GreenMaskSize: 6
[   163.780] 	GreenFieldPosition: 5
[   163.780] 	BlueMaskSize: 5
[   163.780] 	BlueFieldPosition: 0
[   163.780] 	RsvdMaskSize: 0
[   163.780] 	RsvdFieldPosition: 0
[   163.780] 	DirectColorModeInfo: 0
[   163.780] 	PhysBasePtr: 0xd0000000
[   163.780] 	LinBytesPerScanLine: 1280
[   163.780] 	BnkNumberOfImagePages: 35
[   163.780] 	LinNumberOfImagePages: 35
[   163.780] 	LinRedMaskSize: 5
[   163.780] 	LinRedFieldPosition: 11
[   163.780] 	LinGreenMaskSize: 6
[   163.780] 	LinGreenFieldPosition: 5
[   163.780] 	LinBlueMaskSize: 5
[   163.780] 	LinBlueFieldPosition: 0
[   163.780] 	LinRsvdMaskSize: 0
[   163.780] 	LinRsvdFieldPosition: 0
[   163.780] 	MaxPixelClock: 400000000
[   163.781] *Mode: 1c6 (640x350)
[   163.781] 	ModeAttributes: 0xbb
[   163.781] 	WinAAttributes: 0x7
[   163.781] 	WinBAttributes: 0x0
[   163.781] 	WinGranularity: 64
[   163.781] 	WinSize: 64
[   163.781] 	WinASegment: 0xa000
[   163.781] 	WinBSegment: 0x0
[   163.781] 	WinFuncPtr: 0xc0004d11
[   163.781] 	BytesPerScanline: 2560
[   163.781] 	XResolution: 640
[   163.781] 	YResolution: 350
[   163.781] 	XCharSize: 8
[   163.781] 	YCharSize: 14
[   163.781] 	NumberOfPlanes: 1
[   163.781] 	BitsPerPixel: 32
[   163.781] 	NumberOfBanks: 1
[   163.781] 	MemoryModel: 6
[   163.781] 	BankSize: 0
[   163.781] 	NumberOfImages: 17
[   163.781] 	RedMaskSize: 8
[   163.781] 	RedFieldPosition: 16
[   163.781] 	GreenMaskSize: 8
[   163.781] 	GreenFieldPosition: 8
[   163.781] 	BlueMaskSize: 8
[   163.781] 	BlueFieldPosition: 0
[   163.781] 	RsvdMaskSize: 0
[   163.781] 	RsvdFieldPosition: 0
[   163.781] 	DirectColorModeInfo: 0
[   163.781] 	PhysBasePtr: 0xd0000000
[   163.781] 	LinBytesPerScanLine: 2560
[   163.781] 	BnkNumberOfImagePages: 17
[   163.781] 	LinNumberOfImagePages: 17
[   163.781] 	LinRedMaskSize: 8
[   163.781] 	LinRedFieldPosition: 16
[   163.781] 	LinGreenMaskSize: 8
[   163.781] 	LinGreenFieldPosition: 8
[   163.781] 	LinBlueMaskSize: 8
[   163.781] 	LinBlueFieldPosition: 0
[   163.781] 	LinRsvdMaskSize: 0
[   163.781] 	LinRsvdFieldPosition: 0
[   163.781] 	MaxPixelClock: 400000000
[   163.781] Mode: 183 (640x400)
[   163.781] 	ModeAttributes: 0xbb
[   163.781] 	WinAAttributes: 0x7
[   163.781] 	WinBAttributes: 0x0
[   163.781] 	WinGranularity: 64
[   163.781] 	WinSize: 64
[   163.781] 	WinASegment: 0xa000
[   163.781] 	WinBSegment: 0x0
[   163.781] 	WinFuncPtr: 0xc0004d11
[   163.781] 	BytesPerScanline: 640
[   163.781] 	XResolution: 640
[   163.781] 	YResolution: 400
[   163.781] 	XCharSize: 8
[   163.781] 	YCharSize: 16
[   163.781] 	NumberOfPlanes: 1
[   163.781] 	BitsPerPixel: 8
[   163.781] 	NumberOfBanks: 1
[   163.781] 	MemoryModel: 4
[   163.781] 	BankSize: 0
[   163.781] 	NumberOfImages: 63
[   163.781] 	RedMaskSize: 0
[   163.781] 	RedFieldPosition: 0
[   163.781] 	GreenMaskSize: 0
[   163.781] 	GreenFieldPosition: 0
[   163.781] 	BlueMaskSize: 0
[   163.781] 	BlueFieldPosition: 0
[   163.781] 	RsvdMaskSize: 0
[   163.781] 	RsvdFieldPosition: 0
[   163.782] 	DirectColorModeInfo: 0
[   163.782] 	PhysBasePtr: 0xd0000000
[   163.782] 	LinBytesPerScanLine: 640
[   163.782] 	BnkNumberOfImagePages: 63
[   163.782] 	LinNumberOfImagePages: 63
[   163.782] 	LinRedMaskSize: 0
[   163.782] 	LinRedFieldPosition: 0
[   163.782] 	LinGreenMaskSize: 0
[   163.782] 	LinGreenFieldPosition: 0
[   163.782] 	LinBlueMaskSize: 0
[   163.782] 	LinBlueFieldPosition: 0
[   163.782] 	LinRsvdMaskSize: 0
[   163.782] 	LinRsvdFieldPosition: 0
[   163.782] 	MaxPixelClock: 400000000
[   163.782] Mode: 184 (640x400)
[   163.782] 	ModeAttributes: 0xbb
[   163.782] 	WinAAttributes: 0x7
[   163.782] 	WinBAttributes: 0x0
[   163.782] 	WinGranularity: 64
[   163.782] 	WinSize: 64
[   163.782] 	WinASegment: 0xa000
[   163.782] 	WinBSegment: 0x0
[   163.782] 	WinFuncPtr: 0xc0004d11
[   163.782] 	BytesPerScanline: 1280
[   163.782] 	XResolution: 640
[   163.782] 	YResolution: 400
[   163.782] 	XCharSize: 8
[   163.782] 	YCharSize: 16
[   163.782] 	NumberOfPlanes: 1
[   163.782] 	BitsPerPixel: 16
[   163.782] 	NumberOfBanks: 1
[   163.782] 	MemoryModel: 6
[   163.782] 	BankSize: 0
[   163.782] 	NumberOfImages: 31
[   163.782] 	RedMaskSize: 5
[   163.782] 	RedFieldPosition: 10
[   163.782] 	GreenMaskSize: 5
[   163.782] 	GreenFieldPosition: 5
[   163.782] 	BlueMaskSize: 5
[   163.782] 	BlueFieldPosition: 0
[   163.782] 	RsvdMaskSize: 0
[   163.782] 	RsvdFieldPosition: 0
[   163.782] 	DirectColorModeInfo: 0
[   163.782] 	PhysBasePtr: 0xd0000000
[   163.782] 	LinBytesPerScanLine: 1280
[   163.782] 	BnkNumberOfImagePages: 31
[   163.782] 	LinNumberOfImagePages: 31
[   163.782] 	LinRedMaskSize: 5
[   163.782] 	LinRedFieldPosition: 10
[   163.782] 	LinGreenMaskSize: 5
[   163.782] 	LinGreenFieldPosition: 5
[   163.782] 	LinBlueMaskSize: 5
[   163.782] 	LinBlueFieldPosition: 0
[   163.782] 	LinRsvdMaskSize: 0
[   163.782] 	LinRsvdFieldPosition: 0
[   163.782] 	MaxPixelClock: 400000000
[   163.783] Mode: 185 (640x400)
[   163.783] 	ModeAttributes: 0xbb
[   163.783] 	WinAAttributes: 0x7
[   163.783] 	WinBAttributes: 0x0
[   163.783] 	WinGranularity: 64
[   163.783] 	WinSize: 64
[   163.783] 	WinASegment: 0xa000
[   163.783] 	WinBSegment: 0x0
[   163.783] 	WinFuncPtr: 0xc0004d11
[   163.783] 	BytesPerScanline: 1280
[   163.783] 	XResolution: 640
[   163.783] 	YResolution: 400
[   163.783] 	XCharSize: 8
[   163.783] 	YCharSize: 16
[   163.783] 	NumberOfPlanes: 1
[   163.783] 	BitsPerPixel: 16
[   163.783] 	NumberOfBanks: 1
[   163.783] 	MemoryModel: 6
[   163.783] 	BankSize: 0
[   163.783] 	NumberOfImages: 31
[   163.783] 	RedMaskSize: 5
[   163.783] 	RedFieldPosition: 11
[   163.783] 	GreenMaskSize: 6
[   163.783] 	GreenFieldPosition: 5
[   163.783] 	BlueMaskSize: 5
[   163.783] 	BlueFieldPosition: 0
[   163.783] 	RsvdMaskSize: 0
[   163.783] 	RsvdFieldPosition: 0
[   163.783] 	DirectColorModeInfo: 0
[   163.783] 	PhysBasePtr: 0xd0000000
[   163.783] 	LinBytesPerScanLine: 1280
[   163.783] 	BnkNumberOfImagePages: 31
[   163.783] 	LinNumberOfImagePages: 31
[   163.783] 	LinRedMaskSize: 5
[   163.783] 	LinRedFieldPosition: 11
[   163.783] 	LinGreenMaskSize: 6
[   163.783] 	LinGreenFieldPosition: 5
[   163.783] 	LinBlueMaskSize: 5
[   163.783] 	LinBlueFieldPosition: 0
[   163.783] 	LinRsvdMaskSize: 0
[   163.783] 	LinRsvdFieldPosition: 0
[   163.783] 	MaxPixelClock: 400000000
[   163.783] *Mode: 186 (640x400)
[   163.783] 	ModeAttributes: 0xbb
[   163.783] 	WinAAttributes: 0x7
[   163.783] 	WinBAttributes: 0x0
[   163.783] 	WinGranularity: 64
[   163.783] 	WinSize: 64
[   163.783] 	WinASegment: 0xa000
[   163.783] 	WinBSegment: 0x0
[   163.783] 	WinFuncPtr: 0xc0004d11
[   163.783] 	BytesPerScanline: 2560
[   163.783] 	XResolution: 640
[   163.783] 	YResolution: 400
[   163.783] 	XCharSize: 8
[   163.783] 	YCharSize: 16
[   163.783] 	NumberOfPlanes: 1
[   163.783] 	BitsPerPixel: 32
[   163.783] 	NumberOfBanks: 1
[   163.783] 	MemoryModel: 6
[   163.783] 	BankSize: 0
[   163.783] 	NumberOfImages: 15
[   163.783] 	RedMaskSize: 8
[   163.783] 	RedFieldPosition: 16
[   163.783] 	GreenMaskSize: 8
[   163.783] 	GreenFieldPosition: 8
[   163.783] 	BlueMaskSize: 8
[   163.783] 	BlueFieldPosition: 0
[   163.783] 	RsvdMaskSize: 0
[   163.783] 	RsvdFieldPosition: 0
[   163.783] 	DirectColorModeInfo: 0
[   163.783] 	PhysBasePtr: 0xd0000000
[   163.783] 	LinBytesPerScanLine: 2560
[   163.784] 	BnkNumberOfImagePages: 15
[   163.784] 	LinNumberOfImagePages: 15
[   163.784] 	LinRedMaskSize: 8
[   163.784] 	LinRedFieldPosition: 16
[   163.784] 	LinGreenMaskSize: 8
[   163.784] 	LinGreenFieldPosition: 8
[   163.784] 	LinBlueMaskSize: 8
[   163.784] 	LinBlueFieldPosition: 0
[   163.784] 	LinRsvdMaskSize: 0
[   163.784] 	LinRsvdFieldPosition: 0
[   163.784] 	MaxPixelClock: 400000000
[   163.784] Mode: 133 (720x400)
[   163.784] 	ModeAttributes: 0xbb
[   163.784] 	WinAAttributes: 0x7
[   163.784] 	WinBAttributes: 0x0
[   163.784] 	WinGranularity: 64
[   163.784] 	WinSize: 64
[   163.784] 	WinASegment: 0xa000
[   163.784] 	WinBSegment: 0x0
[   163.784] 	WinFuncPtr: 0xc0004d11
[   163.784] 	BytesPerScanline: 768
[   163.784] 	XResolution: 720
[   163.784] 	YResolution: 400
[   163.784] 	XCharSize: 8
[   163.784] 	YCharSize: 16
[   163.784] 	NumberOfPlanes: 1
[   163.784] 	BitsPerPixel: 8
[   163.784] 	NumberOfBanks: 1
[   163.784] 	MemoryModel: 4
[   163.784] 	BankSize: 0
[   163.784] 	NumberOfImages: 50
[   163.784] 	RedMaskSize: 0
[   163.784] 	RedFieldPosition: 0
[   163.784] 	GreenMaskSize: 0
[   163.784] 	GreenFieldPosition: 0
[   163.784] 	BlueMaskSize: 0
[   163.784] 	BlueFieldPosition: 0
[   163.784] 	RsvdMaskSize: 0
[   163.784] 	RsvdFieldPosition: 0
[   163.784] 	DirectColorModeInfo: 0
[   163.784] 	PhysBasePtr: 0xd0000000
[   163.784] 	LinBytesPerScanLine: 768
[   163.784] 	BnkNumberOfImagePages: 50
[   163.784] 	LinNumberOfImagePages: 50
[   163.784] 	LinRedMaskSize: 0
[   163.784] 	LinRedFieldPosition: 0
[   163.784] 	LinGreenMaskSize: 0
[   163.784] 	LinGreenFieldPosition: 0
[   163.784] 	LinBlueMaskSize: 0
[   163.784] 	LinBlueFieldPosition: 0
[   163.784] 	LinRsvdMaskSize: 0
[   163.784] 	LinRsvdFieldPosition: 0
[   163.784] 	MaxPixelClock: 400000000
[   163.785] Mode: 134 (720x400)
[   163.785] 	ModeAttributes: 0xbb
[   163.785] 	WinAAttributes: 0x7
[   163.785] 	WinBAttributes: 0x0
[   163.785] 	WinGranularity: 64
[   163.785] 	WinSize: 64
[   163.785] 	WinASegment: 0xa000
[   163.785] 	WinBSegment: 0x0
[   163.785] 	WinFuncPtr: 0xc0004d11
[   163.785] 	BytesPerScanline: 1472
[   163.785] 	XResolution: 720
[   163.785] 	YResolution: 400
[   163.785] 	XCharSize: 8
[   163.785] 	YCharSize: 16
[   163.785] 	NumberOfPlanes: 1
[   163.785] 	BitsPerPixel: 16
[   163.785] 	NumberOfBanks: 1
[   163.785] 	MemoryModel: 6
[   163.785] 	BankSize: 0
[   163.785] 	NumberOfImages: 27
[   163.785] 	RedMaskSize: 5
[   163.785] 	RedFieldPosition: 10
[   163.785] 	GreenMaskSize: 5
[   163.785] 	GreenFieldPosition: 5
[   163.785] 	BlueMaskSize: 5
[   163.785] 	BlueFieldPosition: 0
[   163.785] 	RsvdMaskSize: 0
[   163.785] 	RsvdFieldPosition: 0
[   163.785] 	DirectColorModeInfo: 0
[   163.785] 	PhysBasePtr: 0xd0000000
[   163.785] 	LinBytesPerScanLine: 1472
[   163.785] 	BnkNumberOfImagePages: 27
[   163.785] 	LinNumberOfImagePages: 27
[   163.785] 	LinRedMaskSize: 5
[   163.785] 	LinRedFieldPosition: 10
[   163.785] 	LinGreenMaskSize: 5
[   163.785] 	LinGreenFieldPosition: 5
[   163.785] 	LinBlueMaskSize: 5
[   163.785] 	LinBlueFieldPosition: 0
[   163.785] 	LinRsvdMaskSize: 0
[   163.785] 	LinRsvdFieldPosition: 0
[   163.785] 	MaxPixelClock: 400000000
[   163.785] Mode: 135 (720x400)
[   163.785] 	ModeAttributes: 0xbb
[   163.785] 	WinAAttributes: 0x7
[   163.785] 	WinBAttributes: 0x0
[   163.785] 	WinGranularity: 64
[   163.785] 	WinSize: 64
[   163.785] 	WinASegment: 0xa000
[   163.785] 	WinBSegment: 0x0
[   163.785] 	WinFuncPtr: 0xc0004d11
[   163.785] 	BytesPerScanline: 1472
[   163.785] 	XResolution: 720
[   163.785] 	YResolution: 400
[   163.785] 	XCharSize: 8
[   163.785] 	YCharSize: 16
[   163.785] 	NumberOfPlanes: 1
[   163.785] 	BitsPerPixel: 16
[   163.785] 	NumberOfBanks: 1
[   163.785] 	MemoryModel: 6
[   163.785] 	BankSize: 0
[   163.785] 	NumberOfImages: 27
[   163.785] 	RedMaskSize: 5
[   163.785] 	RedFieldPosition: 11
[   163.785] 	GreenMaskSize: 6
[   163.785] 	GreenFieldPosition: 5
[   163.785] 	BlueMaskSize: 5
[   163.785] 	BlueFieldPosition: 0
[   163.785] 	RsvdMaskSize: 0
[   163.785] 	RsvdFieldPosition: 0
[   163.785] 	DirectColorModeInfo: 0
[   163.785] 	PhysBasePtr: 0xd0000000
[   163.785] 	LinBytesPerScanLine: 1472
[   163.785] 	BnkNumberOfImagePages: 27
[   163.785] 	LinNumberOfImagePages: 27
[   163.786] 	LinRedMaskSize: 5
[   163.786] 	LinRedFieldPosition: 11
[   163.786] 	LinGreenMaskSize: 6
[   163.786] 	LinGreenFieldPosition: 5
[   163.786] 	LinBlueMaskSize: 5
[   163.786] 	LinBlueFieldPosition: 0
[   163.786] 	LinRsvdMaskSize: 0
[   163.786] 	LinRsvdFieldPosition: 0
[   163.786] 	MaxPixelClock: 400000000
[   163.786] *Mode: 136 (720x400)
[   163.786] 	ModeAttributes: 0xbb
[   163.786] 	WinAAttributes: 0x7
[   163.786] 	WinBAttributes: 0x0
[   163.786] 	WinGranularity: 64
[   163.786] 	WinSize: 64
[   163.786] 	WinASegment: 0xa000
[   163.786] 	WinBSegment: 0x0
[   163.786] 	WinFuncPtr: 0xc0004d11
[   163.786] 	BytesPerScanline: 2944
[   163.786] 	XResolution: 720
[   163.786] 	YResolution: 400
[   163.786] 	XCharSize: 8
[   163.786] 	YCharSize: 16
[   163.786] 	NumberOfPlanes: 1
[   163.786] 	BitsPerPixel: 32
[   163.786] 	NumberOfBanks: 1
[   163.786] 	MemoryModel: 6
[   163.786] 	BankSize: 0
[   163.786] 	NumberOfImages: 13
[   163.786] 	RedMaskSize: 8
[   163.786] 	RedFieldPosition: 16
[   163.786] 	GreenMaskSize: 8
[   163.786] 	GreenFieldPosition: 8
[   163.786] 	BlueMaskSize: 8
[   163.786] 	BlueFieldPosition: 0
[   163.786] 	RsvdMaskSize: 0
[   163.786] 	RsvdFieldPosition: 0
[   163.786] 	DirectColorModeInfo: 0
[   163.786] 	PhysBasePtr: 0xd0000000
[   163.786] 	LinBytesPerScanLine: 2944
[   163.786] 	BnkNumberOfImagePages: 13
[   163.786] 	LinNumberOfImagePages: 13
[   163.786] 	LinRedMaskSize: 8
[   163.786] 	LinRedFieldPosition: 16
[   163.786] 	LinGreenMaskSize: 8
[   163.786] 	LinGreenFieldPosition: 8
[   163.786] 	LinBlueMaskSize: 8
[   163.786] 	LinBlueFieldPosition: 0
[   163.786] 	LinRsvdMaskSize: 0
[   163.786] 	LinRsvdFieldPosition: 0
[   163.786] 	MaxPixelClock: 400000000
[   163.786] Mode: 153 (1152x864)
[   163.787] 	ModeAttributes: 0xbb
[   163.787] 	WinAAttributes: 0x7
[   163.787] 	WinBAttributes: 0x0
[   163.787] 	WinGranularity: 64
[   163.787] 	WinSize: 64
[   163.787] 	WinASegment: 0xa000
[   163.787] 	WinBSegment: 0x0
[   163.787] 	WinFuncPtr: 0xc0004d11
[   163.787] 	BytesPerScanline: 1152
[   163.787] 	XResolution: 1152
[   163.787] 	YResolution: 864
[   163.787] 	XCharSize: 8
[   163.787] 	YCharSize: 16
[   163.787] 	NumberOfPlanes: 1
[   163.787] 	BitsPerPixel: 8
[   163.787] 	NumberOfBanks: 1
[   163.787] 	MemoryModel: 4
[   163.787] 	BankSize: 0
[   163.787] 	NumberOfImages: 15
[   163.787] 	RedMaskSize: 0
[   163.787] 	RedFieldPosition: 0
[   163.787] 	GreenMaskSize: 0
[   163.787] 	GreenFieldPosition: 0
[   163.787] 	BlueMaskSize: 0
[   163.787] 	BlueFieldPosition: 0
[   163.787] 	RsvdMaskSize: 0
[   163.787] 	RsvdFieldPosition: 0
[   163.787] 	DirectColorModeInfo: 0
[   163.787] 	PhysBasePtr: 0xd0000000
[   163.787] 	LinBytesPerScanLine: 1152
[   163.787] 	BnkNumberOfImagePages: 15
[   163.787] 	LinNumberOfImagePages: 15
[   163.787] 	LinRedMaskSize: 0
[   163.787] 	LinRedFieldPosition: 0
[   163.787] 	LinGreenMaskSize: 0
[   163.787] 	LinGreenFieldPosition: 0
[   163.787] 	LinBlueMaskSize: 0
[   163.787] 	LinBlueFieldPosition: 0
[   163.787] 	LinRsvdMaskSize: 0
[   163.787] 	LinRsvdFieldPosition: 0
[   163.787] 	MaxPixelClock: 400000000
[   163.787] Mode: 154 (1152x864)
[   163.787] 	ModeAttributes: 0xbb
[   163.787] 	WinAAttributes: 0x7
[   163.787] 	WinBAttributes: 0x0
[   163.787] 	WinGranularity: 64
[   163.787] 	WinSize: 64
[   163.787] 	WinASegment: 0xa000
[   163.787] 	WinBSegment: 0x0
[   163.787] 	WinFuncPtr: 0xc0004d11
[   163.787] 	BytesPerScanline: 2304
[   163.787] 	XResolution: 1152
[   163.787] 	YResolution: 864
[   163.787] 	XCharSize: 8
[   163.787] 	YCharSize: 16
[   163.787] 	NumberOfPlanes: 1
[   163.787] 	BitsPerPixel: 16
[   163.787] 	NumberOfBanks: 1
[   163.787] 	MemoryModel: 6
[   163.787] 	BankSize: 0
[   163.787] 	NumberOfImages: 7
[   163.787] 	RedMaskSize: 5
[   163.787] 	RedFieldPosition: 10
[   163.787] 	GreenMaskSize: 5
[   163.787] 	GreenFieldPosition: 5
[   163.787] 	BlueMaskSize: 5
[   163.787] 	BlueFieldPosition: 0
[   163.787] 	RsvdMaskSize: 0
[   163.787] 	RsvdFieldPosition: 0
[   163.787] 	DirectColorModeInfo: 0
[   163.787] 	PhysBasePtr: 0xd0000000
[   163.787] 	LinBytesPerScanLine: 2304
[   163.787] 	BnkNumberOfImagePages: 7
[   163.787] 	LinNumberOfImagePages: 7
[   163.787] 	LinRedMaskSize: 5
[   163.787] 	LinRedFieldPosition: 10
[   163.787] 	LinGreenMaskSize: 5
[   163.787] 	LinGreenFieldPosition: 5
[   163.788] 	LinBlueMaskSize: 5
[   163.788] 	LinBlueFieldPosition: 0
[   163.788] 	LinRsvdMaskSize: 0
[   163.788] 	LinRsvdFieldPosition: 0
[   163.788] 	MaxPixelClock: 400000000
[   163.788] Mode: 155 (1152x864)
[   163.788] 	ModeAttributes: 0xbb
[   163.788] 	WinAAttributes: 0x7
[   163.788] 	WinBAttributes: 0x0
[   163.788] 	WinGranularity: 64
[   163.788] 	WinSize: 64
[   163.788] 	WinASegment: 0xa000
[   163.788] 	WinBSegment: 0x0
[   163.788] 	WinFuncPtr: 0xc0004d11
[   163.788] 	BytesPerScanline: 2304
[   163.788] 	XResolution: 1152
[   163.788] 	YResolution: 864
[   163.788] 	XCharSize: 8
[   163.788] 	YCharSize: 16
[   163.788] 	NumberOfPlanes: 1
[   163.788] 	BitsPerPixel: 16
[   163.788] 	NumberOfBanks: 1
[   163.788] 	MemoryModel: 6
[   163.788] 	BankSize: 0
[   163.788] 	NumberOfImages: 7
[   163.788] 	RedMaskSize: 5
[   163.788] 	RedFieldPosition: 11
[   163.788] 	GreenMaskSize: 6
[   163.788] 	GreenFieldPosition: 5
[   163.788] 	BlueMaskSize: 5
[   163.788] 	BlueFieldPosition: 0
[   163.788] 	RsvdMaskSize: 0
[   163.788] 	RsvdFieldPosition: 0
[   163.788] 	DirectColorModeInfo: 0
[   163.788] 	PhysBasePtr: 0xd0000000
[   163.788] 	LinBytesPerScanLine: 2304
[   163.788] 	BnkNumberOfImagePages: 7
[   163.788] 	LinNumberOfImagePages: 7
[   163.788] 	LinRedMaskSize: 5
[   163.788] 	LinRedFieldPosition: 11
[   163.788] 	LinGreenMaskSize: 6
[   163.788] 	LinGreenFieldPosition: 5
[   163.788] 	LinBlueMaskSize: 5
[   163.788] 	LinBlueFieldPosition: 0
[   163.788] 	LinRsvdMaskSize: 0
[   163.788] 	LinRsvdFieldPosition: 0
[   163.788] 	MaxPixelClock: 400000000
[   163.788] *Mode: 156 (1152x864)
[   163.789] 	ModeAttributes: 0xbb
[   163.789] 	WinAAttributes: 0x7
[   163.789] 	WinBAttributes: 0x0
[   163.789] 	WinGranularity: 64
[   163.789] 	WinSize: 64
[   163.789] 	WinASegment: 0xa000
[   163.789] 	WinBSegment: 0x0
[   163.789] 	WinFuncPtr: 0xc0004d11
[   163.789] 	BytesPerScanline: 4608
[   163.789] 	XResolution: 1152
[   163.789] 	YResolution: 864
[   163.789] 	XCharSize: 8
[   163.789] 	YCharSize: 16
[   163.789] 	NumberOfPlanes: 1
[   163.789] 	BitsPerPixel: 32
[   163.789] 	NumberOfBanks: 1
[   163.789] 	MemoryModel: 6
[   163.789] 	BankSize: 0
[   163.789] 	NumberOfImages: 3
[   163.789] 	RedMaskSize: 8
[   163.789] 	RedFieldPosition: 16
[   163.789] 	GreenMaskSize: 8
[   163.789] 	GreenFieldPosition: 8
[   163.789] 	BlueMaskSize: 8
[   163.789] 	BlueFieldPosition: 0
[   163.789] 	RsvdMaskSize: 0
[   163.789] 	RsvdFieldPosition: 0
[   163.789] 	DirectColorModeInfo: 0
[   163.789] 	PhysBasePtr: 0xd0000000
[   163.789] 	LinBytesPerScanLine: 4608
[   163.789] 	BnkNumberOfImagePages: 3
[   163.789] 	LinNumberOfImagePages: 3
[   163.789] 	LinRedMaskSize: 8
[   163.789] 	LinRedFieldPosition: 16
[   163.789] 	LinGreenMaskSize: 8
[   163.789] 	LinGreenFieldPosition: 8
[   163.789] 	LinBlueMaskSize: 8
[   163.789] 	LinBlueFieldPosition: 0
[   163.789] 	LinRsvdMaskSize: 0
[   163.789] 	LinRsvdFieldPosition: 0
[   163.789] 	MaxPixelClock: 400000000
[   163.789] Mode: 163 (1280x1024)
[   163.789] 	ModeAttributes: 0xbb
[   163.789] 	WinAAttributes: 0x7
[   163.789] 	WinBAttributes: 0x0
[   163.789] 	WinGranularity: 64
[   163.789] 	WinSize: 64
[   163.789] 	WinASegment: 0xa000
[   163.789] 	WinBSegment: 0x0
[   163.789] 	WinFuncPtr: 0xc0004d11
[   163.789] 	BytesPerScanline: 1280
[   163.789] 	XResolution: 1280
[   163.789] 	YResolution: 1024
[   163.789] 	XCharSize: 8
[   163.789] 	YCharSize: 16
[   163.789] 	NumberOfPlanes: 1
[   163.789] 	BitsPerPixel: 8
[   163.789] 	NumberOfBanks: 1
[   163.789] 	MemoryModel: 4
[   163.789] 	BankSize: 0
[   163.789] 	NumberOfImages: 11
[   163.789] 	RedMaskSize: 0
[   163.789] 	RedFieldPosition: 0
[   163.789] 	GreenMaskSize: 0
[   163.789] 	GreenFieldPosition: 0
[   163.789] 	BlueMaskSize: 0
[   163.789] 	BlueFieldPosition: 0
[   163.789] 	RsvdMaskSize: 0
[   163.789] 	RsvdFieldPosition: 0
[   163.789] 	DirectColorModeInfo: 0
[   163.789] 	PhysBasePtr: 0xd0000000
[   163.789] 	LinBytesPerScanLine: 1280
[   163.789] 	BnkNumberOfImagePages: 11
[   163.789] 	LinNumberOfImagePages: 11
[   163.789] 	LinRedMaskSize: 0
[   163.789] 	LinRedFieldPosition: 0
[   163.789] 	LinGreenMaskSize: 0
[   163.790] 	LinGreenFieldPosition: 0
[   163.790] 	LinBlueMaskSize: 0
[   163.790] 	LinBlueFieldPosition: 0
[   163.790] 	LinRsvdMaskSize: 0
[   163.790] 	LinRsvdFieldPosition: 0
[   163.790] 	MaxPixelClock: 400000000
[   163.790] Mode: 164 (1280x1024)
[   163.790] 	ModeAttributes: 0xbb
[   163.790] 	WinAAttributes: 0x7
[   163.790] 	WinBAttributes: 0x0
[   163.790] 	WinGranularity: 64
[   163.790] 	WinSize: 64
[   163.790] 	WinASegment: 0xa000
[   163.790] 	WinBSegment: 0x0
[   163.790] 	WinFuncPtr: 0xc0004d11
[   163.790] 	BytesPerScanline: 2560
[   163.790] 	XResolution: 1280
[   163.790] 	YResolution: 1024
[   163.790] 	XCharSize: 8
[   163.790] 	YCharSize: 16
[   163.790] 	NumberOfPlanes: 1
[   163.790] 	BitsPerPixel: 16
[   163.790] 	NumberOfBanks: 1
[   163.790] 	MemoryModel: 6
[   163.790] 	BankSize: 0
[   163.790] 	NumberOfImages: 5
[   163.790] 	RedMaskSize: 5
[   163.790] 	RedFieldPosition: 10
[   163.790] 	GreenMaskSize: 5
[   163.790] 	GreenFieldPosition: 5
[   163.790] 	BlueMaskSize: 5
[   163.790] 	BlueFieldPosition: 0
[   163.790] 	RsvdMaskSize: 0
[   163.790] 	RsvdFieldPosition: 0
[   163.790] 	DirectColorModeInfo: 0
[   163.790] 	PhysBasePtr: 0xd0000000
[   163.790] 	LinBytesPerScanLine: 2560
[   163.790] 	BnkNumberOfImagePages: 5
[   163.790] 	LinNumberOfImagePages: 5
[   163.790] 	LinRedMaskSize: 5
[   163.790] 	LinRedFieldPosition: 10
[   163.790] 	LinGreenMaskSize: 5
[   163.790] 	LinGreenFieldPosition: 5
[   163.790] 	LinBlueMaskSize: 5
[   163.790] 	LinBlueFieldPosition: 0
[   163.790] 	LinRsvdMaskSize: 0
[   163.790] 	LinRsvdFieldPosition: 0
[   163.790] 	MaxPixelClock: 400000000
[   163.790] Mode: 165 (1280x1024)
[   163.791] 	ModeAttributes: 0xbb
[   163.791] 	WinAAttributes: 0x7
[   163.791] 	WinBAttributes: 0x0
[   163.791] 	WinGranularity: 64
[   163.791] 	WinSize: 64
[   163.791] 	WinASegment: 0xa000
[   163.791] 	WinBSegment: 0x0
[   163.791] 	WinFuncPtr: 0xc0004d11
[   163.791] 	BytesPerScanline: 2560
[   163.791] 	XResolution: 1280
[   163.791] 	YResolution: 1024
[   163.791] 	XCharSize: 8
[   163.791] 	YCharSize: 16
[   163.791] 	NumberOfPlanes: 1
[   163.791] 	BitsPerPixel: 16
[   163.791] 	NumberOfBanks: 1
[   163.791] 	MemoryModel: 6
[   163.791] 	BankSize: 0
[   163.791] 	NumberOfImages: 5
[   163.791] 	RedMaskSize: 5
[   163.791] 	RedFieldPosition: 11
[   163.791] 	GreenMaskSize: 6
[   163.791] 	GreenFieldPosition: 5
[   163.791] 	BlueMaskSize: 5
[   163.791] 	BlueFieldPosition: 0
[   163.791] 	RsvdMaskSize: 0
[   163.791] 	RsvdFieldPosition: 0
[   163.791] 	DirectColorModeInfo: 0
[   163.791] 	PhysBasePtr: 0xd0000000
[   163.791] 	LinBytesPerScanLine: 2560
[   163.791] 	BnkNumberOfImagePages: 5
[   163.791] 	LinNumberOfImagePages: 5
[   163.791] 	LinRedMaskSize: 5
[   163.791] 	LinRedFieldPosition: 11
[   163.791] 	LinGreenMaskSize: 6
[   163.791] 	LinGreenFieldPosition: 5
[   163.791] 	LinBlueMaskSize: 5
[   163.791] 	LinBlueFieldPosition: 0
[   163.791] 	LinRsvdMaskSize: 0
[   163.791] 	LinRsvdFieldPosition: 0
[   163.791] 	MaxPixelClock: 400000000
[   163.791] *Mode: 166 (1280x1024)
[   163.791] 	ModeAttributes: 0xbb
[   163.791] 	WinAAttributes: 0x7
[   163.791] 	WinBAttributes: 0x0
[   163.791] 	WinGranularity: 64
[   163.791] 	WinSize: 64
[   163.791] 	WinASegment: 0xa000
[   163.791] 	WinBSegment: 0x0
[   163.791] 	WinFuncPtr: 0xc0004d11
[   163.791] 	BytesPerScanline: 5120
[   163.791] 	XResolution: 1280
[   163.791] 	YResolution: 1024
[   163.791] 	XCharSize: 8
[   163.791] 	YCharSize: 16
[   163.791] 	NumberOfPlanes: 1
[   163.791] 	BitsPerPixel: 32
[   163.791] 	NumberOfBanks: 1
[   163.791] 	MemoryModel: 6
[   163.791] 	BankSize: 0
[   163.791] 	NumberOfImages: 2
[   163.791] 	RedMaskSize: 8
[   163.791] 	RedFieldPosition: 16
[   163.791] 	GreenMaskSize: 8
[   163.791] 	GreenFieldPosition: 8
[   163.791] 	BlueMaskSize: 8
[   163.791] 	BlueFieldPosition: 0
[   163.791] 	RsvdMaskSize: 0
[   163.791] 	RsvdFieldPosition: 0
[   163.791] 	DirectColorModeInfo: 0
[   163.791] 	PhysBasePtr: 0xd0000000
[   163.791] 	LinBytesPerScanLine: 5120
[   163.791] 	BnkNumberOfImagePages: 2
[   163.791] 	LinNumberOfImagePages: 2
[   163.791] 	LinRedMaskSize: 8
[   163.791] 	LinRedFieldPosition: 16
[   163.792] 	LinGreenMaskSize: 8
[   163.792] 	LinGreenFieldPosition: 8
[   163.792] 	LinBlueMaskSize: 8
[   163.792] 	LinBlueFieldPosition: 0
[   163.792] 	LinRsvdMaskSize: 0
[   163.792] 	LinRsvdFieldPosition: 0
[   163.792] 	MaxPixelClock: 400000000
[   163.792] *Mode: 121 (640x480)
[   163.792] 	ModeAttributes: 0xbb
[   163.792] 	WinAAttributes: 0x7
[   163.792] 	WinBAttributes: 0x0
[   163.792] 	WinGranularity: 64
[   163.792] 	WinSize: 64
[   163.792] 	WinASegment: 0xa000
[   163.792] 	WinBSegment: 0x0
[   163.792] 	WinFuncPtr: 0xc0004d11
[   163.792] 	BytesPerScanline: 2560
[   163.792] 	XResolution: 640
[   163.792] 	YResolution: 480
[   163.792] 	XCharSize: 8
[   163.792] 	YCharSize: 16
[   163.792] 	NumberOfPlanes: 1
[   163.792] 	BitsPerPixel: 32
[   163.792] 	NumberOfBanks: 1
[   163.792] 	MemoryModel: 6
[   163.792] 	BankSize: 0
[   163.792] 	NumberOfImages: 12
[   163.792] 	RedMaskSize: 8
[   163.792] 	RedFieldPosition: 16
[   163.792] 	GreenMaskSize: 8
[   163.792] 	GreenFieldPosition: 8
[   163.792] 	BlueMaskSize: 8
[   163.792] 	BlueFieldPosition: 0
[   163.792] 	RsvdMaskSize: 0
[   163.792] 	RsvdFieldPosition: 0
[   163.792] 	DirectColorModeInfo: 0
[   163.792] 	PhysBasePtr: 0xd0000000
[   163.792] 	LinBytesPerScanLine: 2560
[   163.792] 	BnkNumberOfImagePages: 12
[   163.792] 	LinNumberOfImagePages: 12
[   163.792] 	LinRedMaskSize: 8
[   163.792] 	LinRedFieldPosition: 16
[   163.792] 	LinGreenMaskSize: 8
[   163.792] 	LinGreenFieldPosition: 8
[   163.792] 	LinBlueMaskSize: 8
[   163.792] 	LinBlueFieldPosition: 0
[   163.792] 	LinRsvdMaskSize: 0
[   163.792] 	LinRsvdFieldPosition: 0
[   163.792] 	MaxPixelClock: 400000000
[   163.793] *Mode: 122 (800x600)
[   163.793] 	ModeAttributes: 0xbb
[   163.793] 	WinAAttributes: 0x7
[   163.793] 	WinBAttributes: 0x0
[   163.793] 	WinGranularity: 64
[   163.793] 	WinSize: 64
[   163.793] 	WinASegment: 0xa000
[   163.793] 	WinBSegment: 0x0
[   163.793] 	WinFuncPtr: 0xc0004d11
[   163.793] 	BytesPerScanline: 3200
[   163.793] 	XResolution: 800
[   163.793] 	YResolution: 600
[   163.793] 	XCharSize: 8
[   163.793] 	YCharSize: 14
[   163.793] 	NumberOfPlanes: 1
[   163.793] 	BitsPerPixel: 32
[   163.793] 	NumberOfBanks: 1
[   163.793] 	MemoryModel: 6
[   163.793] 	BankSize: 0
[   163.793] 	NumberOfImages: 7
[   163.793] 	RedMaskSize: 8
[   163.793] 	RedFieldPosition: 16
[   163.793] 	GreenMaskSize: 8
[   163.793] 	GreenFieldPosition: 8
[   163.793] 	BlueMaskSize: 8
[   163.793] 	BlueFieldPosition: 0
[   163.793] 	RsvdMaskSize: 0
[   163.793] 	RsvdFieldPosition: 0
[   163.793] 	DirectColorModeInfo: 0
[   163.793] 	PhysBasePtr: 0xd0000000
[   163.793] 	LinBytesPerScanLine: 3200
[   163.793] 	BnkNumberOfImagePages: 7
[   163.793] 	LinNumberOfImagePages: 7
[   163.793] 	LinRedMaskSize: 8
[   163.793] 	LinRedFieldPosition: 16
[   163.793] 	LinGreenMaskSize: 8
[   163.793] 	LinGreenFieldPosition: 8
[   163.793] 	LinBlueMaskSize: 8
[   163.793] 	LinBlueFieldPosition: 0
[   163.793] 	LinRsvdMaskSize: 0
[   163.793] 	LinRsvdFieldPosition: 0
[   163.793] 	MaxPixelClock: 400000000
[   163.793] *Mode: 123 (1024x768)
[   163.793] 	ModeAttributes: 0xbb
[   163.793] 	WinAAttributes: 0x7
[   163.793] 	WinBAttributes: 0x0
[   163.793] 	WinGranularity: 64
[   163.793] 	WinSize: 64
[   163.793] 	WinASegment: 0xa000
[   163.793] 	WinBSegment: 0x0
[   163.793] 	WinFuncPtr: 0xc0004d11
[   163.793] 	BytesPerScanline: 4096
[   163.793] 	XResolution: 1024
[   163.793] 	YResolution: 768
[   163.793] 	XCharSize: 8
[   163.793] 	YCharSize: 16
[   163.793] 	NumberOfPlanes: 1
[   163.793] 	BitsPerPixel: 32
[   163.793] 	NumberOfBanks: 1
[   163.793] 	MemoryModel: 6
[   163.793] 	BankSize: 0
[   163.793] 	NumberOfImages: 4
[   163.793] 	RedMaskSize: 8
[   163.793] 	RedFieldPosition: 16
[   163.793] 	GreenMaskSize: 8
[   163.793] 	GreenFieldPosition: 8
[   163.793] 	BlueMaskSize: 8
[   163.793] 	BlueFieldPosition: 0
[   163.793] 	RsvdMaskSize: 0
[   163.793] 	RsvdFieldPosition: 0
[   163.793] 	DirectColorModeInfo: 0
[   163.794] 	PhysBasePtr: 0xd0000000
[   163.794] 	LinBytesPerScanLine: 4096
[   163.794] 	BnkNumberOfImagePages: 4
[   163.794] 	LinNumberOfImagePages: 4
[   163.794] 	LinRedMaskSize: 8
[   163.794] 	LinRedFieldPosition: 16
[   163.794] 	LinGreenMaskSize: 8
[   163.794] 	LinGreenFieldPosition: 8
[   163.794] 	LinBlueMaskSize: 8
[   163.794] 	LinBlueFieldPosition: 0
[   163.794] 	LinRsvdMaskSize: 0
[   163.794] 	LinRsvdFieldPosition: 0
[   163.794] 	MaxPixelClock: 400000000
[   163.794] *Mode: 124 (1280x1024)
[   163.794] 	ModeAttributes: 0xbb
[   163.794] 	WinAAttributes: 0x7
[   163.794] 	WinBAttributes: 0x0
[   163.794] 	WinGranularity: 64
[   163.794] 	WinSize: 64
[   163.794] 	WinASegment: 0xa000
[   163.794] 	WinBSegment: 0x0
[   163.794] 	WinFuncPtr: 0xc0004d11
[   163.794] 	BytesPerScanline: 5120
[   163.794] 	XResolution: 1280
[   163.794] 	YResolution: 1024
[   163.794] 	XCharSize: 8
[   163.794] 	YCharSize: 16
[   163.794] 	NumberOfPlanes: 1
[   163.794] 	BitsPerPixel: 32
[   163.794] 	NumberOfBanks: 1
[   163.794] 	MemoryModel: 6
[   163.794] 	BankSize: 0
[   163.794] 	NumberOfImages: 2
[   163.794] 	RedMaskSize: 8
[   163.794] 	RedFieldPosition: 16
[   163.794] 	GreenMaskSize: 8
[   163.794] 	GreenFieldPosition: 8
[   163.794] 	BlueMaskSize: 8
[   163.794] 	BlueFieldPosition: 0
[   163.794] 	RsvdMaskSize: 0
[   163.794] 	RsvdFieldPosition: 0
[   163.794] 	DirectColorModeInfo: 0
[   163.794] 	PhysBasePtr: 0xd0000000
[   163.794] 	LinBytesPerScanLine: 5120
[   163.794] 	BnkNumberOfImagePages: 2
[   163.794] 	LinNumberOfImagePages: 2
[   163.794] 	LinRedMaskSize: 8
[   163.794] 	LinRedFieldPosition: 16
[   163.794] 	LinGreenMaskSize: 8
[   163.794] 	LinGreenFieldPosition: 8
[   163.794] 	LinBlueMaskSize: 8
[   163.794] 	LinBlueFieldPosition: 0
[   163.794] 	LinRsvdMaskSize: 0
[   163.794] 	LinRsvdFieldPosition: 0
[   163.794] 	MaxPixelClock: 400000000
[   163.795] Mode: 143 (1400x1050)
[   163.795] 	ModeAttributes: 0xbb
[   163.795] 	WinAAttributes: 0x7
[   163.795] 	WinBAttributes: 0x0
[   163.795] 	WinGranularity: 64
[   163.795] 	WinSize: 64
[   163.795] 	WinASegment: 0xa000
[   163.795] 	WinBSegment: 0x0
[   163.795] 	WinFuncPtr: 0xc0004d11
[   163.795] 	BytesPerScanline: 1408
[   163.795] 	XResolution: 1400
[   163.795] 	YResolution: 1050
[   163.795] 	XCharSize: 8
[   163.795] 	YCharSize: 16
[   163.795] 	NumberOfPlanes: 1
[   163.795] 	BitsPerPixel: 8
[   163.795] 	NumberOfBanks: 1
[   163.795] 	MemoryModel: 4
[   163.795] 	BankSize: 0
[   163.795] 	NumberOfImages: 10
[   163.795] 	RedMaskSize: 0
[   163.795] 	RedFieldPosition: 0
[   163.795] 	GreenMaskSize: 0
[   163.795] 	GreenFieldPosition: 0
[   163.795] 	BlueMaskSize: 0
[   163.795] 	BlueFieldPosition: 0
[   163.795] 	RsvdMaskSize: 0
[   163.795] 	RsvdFieldPosition: 0
[   163.795] 	DirectColorModeInfo: 0
[   163.795] 	PhysBasePtr: 0xd0000000
[   163.795] 	LinBytesPerScanLine: 1408
[   163.795] 	BnkNumberOfImagePages: 10
[   163.795] 	LinNumberOfImagePages: 10
[   163.795] 	LinRedMaskSize: 0
[   163.795] 	LinRedFieldPosition: 0
[   163.795] 	LinGreenMaskSize: 0
[   163.795] 	LinGreenFieldPosition: 0
[   163.795] 	LinBlueMaskSize: 0
[   163.795] 	LinBlueFieldPosition: 0
[   163.795] 	LinRsvdMaskSize: 0
[   163.795] 	LinRsvdFieldPosition: 0
[   163.795] 	MaxPixelClock: 400000000
[   163.795] Mode: 144 (1400x1050)
[   163.795] 	ModeAttributes: 0xbb
[   163.795] 	WinAAttributes: 0x7
[   163.795] 	WinBAttributes: 0x0
[   163.795] 	WinGranularity: 64
[   163.795] 	WinSize: 64
[   163.795] 	WinASegment: 0xa000
[   163.795] 	WinBSegment: 0x0
[   163.795] 	WinFuncPtr: 0xc0004d11
[   163.795] 	BytesPerScanline: 2816
[   163.795] 	XResolution: 1400
[   163.795] 	YResolution: 1050
[   163.795] 	XCharSize: 8
[   163.795] 	YCharSize: 16
[   163.795] 	NumberOfPlanes: 1
[   163.795] 	BitsPerPixel: 16
[   163.795] 	NumberOfBanks: 1
[   163.795] 	MemoryModel: 6
[   163.795] 	BankSize: 0
[   163.795] 	NumberOfImages: 4
[   163.795] 	RedMaskSize: 5
[   163.795] 	RedFieldPosition: 10
[   163.795] 	GreenMaskSize: 5
[   163.795] 	GreenFieldPosition: 5
[   163.795] 	BlueMaskSize: 5
[   163.795] 	BlueFieldPosition: 0
[   163.795] 	RsvdMaskSize: 0
[   163.796] 	RsvdFieldPosition: 0
[   163.796] 	DirectColorModeInfo: 0
[   163.796] 	PhysBasePtr: 0xd0000000
[   163.796] 	LinBytesPerScanLine: 2816
[   163.796] 	BnkNumberOfImagePages: 4
[   163.796] 	LinNumberOfImagePages: 4
[   163.796] 	LinRedMaskSize: 5
[   163.796] 	LinRedFieldPosition: 10
[   163.796] 	LinGreenMaskSize: 5
[   163.796] 	LinGreenFieldPosition: 5
[   163.796] 	LinBlueMaskSize: 5
[   163.796] 	LinBlueFieldPosition: 0
[   163.796] 	LinRsvdMaskSize: 0
[   163.796] 	LinRsvdFieldPosition: 0
[   163.796] 	MaxPixelClock: 400000000
[   163.796] Mode: 145 (1400x1050)
[   163.796] 	ModeAttributes: 0xbb
[   163.796] 	WinAAttributes: 0x7
[   163.796] 	WinBAttributes: 0x0
[   163.796] 	WinGranularity: 64
[   163.796] 	WinSize: 64
[   163.796] 	WinASegment: 0xa000
[   163.796] 	WinBSegment: 0x0
[   163.796] 	WinFuncPtr: 0xc0004d11
[   163.796] 	BytesPerScanline: 2816
[   163.796] 	XResolution: 1400
[   163.796] 	YResolution: 1050
[   163.796] 	XCharSize: 8
[   163.796] 	YCharSize: 16
[   163.796] 	NumberOfPlanes: 1
[   163.796] 	BitsPerPixel: 16
[   163.796] 	NumberOfBanks: 1
[   163.796] 	MemoryModel: 6
[   163.796] 	BankSize: 0
[   163.796] 	NumberOfImages: 4
[   163.796] 	RedMaskSize: 5
[   163.796] 	RedFieldPosition: 11
[   163.796] 	GreenMaskSize: 6
[   163.796] 	GreenFieldPosition: 5
[   163.796] 	BlueMaskSize: 5
[   163.796] 	BlueFieldPosition: 0
[   163.796] 	RsvdMaskSize: 0
[   163.796] 	RsvdFieldPosition: 0
[   163.796] 	DirectColorModeInfo: 0
[   163.796] 	PhysBasePtr: 0xd0000000
[   163.796] 	LinBytesPerScanLine: 2816
[   163.796] 	BnkNumberOfImagePages: 4
[   163.796] 	LinNumberOfImagePages: 4
[   163.796] 	LinRedMaskSize: 5
[   163.796] 	LinRedFieldPosition: 11
[   163.796] 	LinGreenMaskSize: 6
[   163.796] 	LinGreenFieldPosition: 5
[   163.796] 	LinBlueMaskSize: 5
[   163.796] 	LinBlueFieldPosition: 0
[   163.796] 	LinRsvdMaskSize: 0
[   163.796] 	LinRsvdFieldPosition: 0
[   163.796] 	MaxPixelClock: 400000000
[   163.797] *Mode: 146 (1400x1050)
[   163.797] 	ModeAttributes: 0xbb
[   163.797] 	WinAAttributes: 0x7
[   163.797] 	WinBAttributes: 0x0
[   163.797] 	WinGranularity: 64
[   163.797] 	WinSize: 64
[   163.797] 	WinASegment: 0xa000
[   163.797] 	WinBSegment: 0x0
[   163.797] 	WinFuncPtr: 0xc0004d11
[   163.797] 	BytesPerScanline: 5632
[   163.797] 	XResolution: 1400
[   163.797] 	YResolution: 1050
[   163.797] 	XCharSize: 8
[   163.797] 	YCharSize: 16
[   163.797] 	NumberOfPlanes: 1
[   163.797] 	BitsPerPixel: 32
[   163.797] 	NumberOfBanks: 1
[   163.797] 	MemoryModel: 6
[   163.797] 	BankSize: 0
[   163.797] 	NumberOfImages: 1
[   163.797] 	RedMaskSize: 8
[   163.797] 	RedFieldPosition: 16
[   163.797] 	GreenMaskSize: 8
[   163.797] 	GreenFieldPosition: 8
[   163.797] 	BlueMaskSize: 8
[   163.797] 	BlueFieldPosition: 0
[   163.797] 	RsvdMaskSize: 0
[   163.797] 	RsvdFieldPosition: 0
[   163.797] 	DirectColorModeInfo: 0
[   163.797] 	PhysBasePtr: 0xd0000000
[   163.797] 	LinBytesPerScanLine: 5632
[   163.797] 	BnkNumberOfImagePages: 1
[   163.797] 	LinNumberOfImagePages: 1
[   163.797] 	LinRedMaskSize: 8
[   163.797] 	LinRedFieldPosition: 16
[   163.797] 	LinGreenMaskSize: 8
[   163.797] 	LinGreenFieldPosition: 8
[   163.797] 	LinBlueMaskSize: 8
[   163.797] 	LinBlueFieldPosition: 0
[   163.797] 	LinRsvdMaskSize: 0
[   163.797] 	LinRsvdFieldPosition: 0
[   163.797] 	MaxPixelClock: 400000000
[   163.797] Mode: 173 (1600x1200)
[   163.797] 	ModeAttributes: 0xbb
[   163.797] 	WinAAttributes: 0x7
[   163.797] 	WinBAttributes: 0x0
[   163.797] 	WinGranularity: 64
[   163.797] 	WinSize: 64
[   163.797] 	WinASegment: 0xa000
[   163.797] 	WinBSegment: 0x0
[   163.797] 	WinFuncPtr: 0xc0004d11
[   163.797] 	BytesPerScanline: 1600
[   163.797] 	XResolution: 1600
[   163.797] 	YResolution: 1200
[   163.797] 	XCharSize: 8
[   163.797] 	YCharSize: 16
[   163.797] 	NumberOfPlanes: 1
[   163.797] 	BitsPerPixel: 8
[   163.797] 	NumberOfBanks: 1
[   163.797] 	MemoryModel: 4
[   163.797] 	BankSize: 0
[   163.797] 	NumberOfImages: 7
[   163.797] 	RedMaskSize: 0
[   163.798] 	RedFieldPosition: 0
[   163.798] 	GreenMaskSize: 0
[   163.798] 	GreenFieldPosition: 0
[   163.798] 	BlueMaskSize: 0
[   163.798] 	BlueFieldPosition: 0
[   163.798] 	RsvdMaskSize: 0
[   163.798] 	RsvdFieldPosition: 0
[   163.798] 	DirectColorModeInfo: 0
[   163.798] 	PhysBasePtr: 0xd0000000
[   163.798] 	LinBytesPerScanLine: 1600
[   163.798] 	BnkNumberOfImagePages: 7
[   163.798] 	LinNumberOfImagePages: 7
[   163.798] 	LinRedMaskSize: 0
[   163.798] 	LinRedFieldPosition: 0
[   163.798] 	LinGreenMaskSize: 0
[   163.798] 	LinGreenFieldPosition: 0
[   163.798] 	LinBlueMaskSize: 0
[   163.798] 	LinBlueFieldPosition: 0
[   163.798] 	LinRsvdMaskSize: 0
[   163.798] 	LinRsvdFieldPosition: 0
[   163.798] 	MaxPixelClock: 400000000
[   163.798] Mode: 174 (1600x1200)
[   163.798] 	ModeAttributes: 0xbb
[   163.798] 	WinAAttributes: 0x7
[   163.798] 	WinBAttributes: 0x0
[   163.798] 	WinGranularity: 64
[   163.798] 	WinSize: 64
[   163.798] 	WinASegment: 0xa000
[   163.798] 	WinBSegment: 0x0
[   163.798] 	WinFuncPtr: 0xc0004d11
[   163.798] 	BytesPerScanline: 3200
[   163.798] 	XResolution: 1600
[   163.798] 	YResolution: 1200
[   163.798] 	XCharSize: 8
[   163.798] 	YCharSize: 16
[   163.798] 	NumberOfPlanes: 1
[   163.798] 	BitsPerPixel: 16
[   163.798] 	NumberOfBanks: 1
[   163.798] 	MemoryModel: 6
[   163.798] 	BankSize: 0
[   163.798] 	NumberOfImages: 3
[   163.798] 	RedMaskSize: 5
[   163.798] 	RedFieldPosition: 10
[   163.798] 	GreenMaskSize: 5
[   163.798] 	GreenFieldPosition: 5
[   163.798] 	BlueMaskSize: 5
[   163.798] 	BlueFieldPosition: 0
[   163.798] 	RsvdMaskSize: 0
[   163.798] 	RsvdFieldPosition: 0
[   163.798] 	DirectColorModeInfo: 0
[   163.798] 	PhysBasePtr: 0xd0000000
[   163.798] 	LinBytesPerScanLine: 3200
[   163.798] 	BnkNumberOfImagePages: 3
[   163.798] 	LinNumberOfImagePages: 3
[   163.798] 	LinRedMaskSize: 5
[   163.798] 	LinRedFieldPosition: 10
[   163.798] 	LinGreenMaskSize: 5
[   163.798] 	LinGreenFieldPosition: 5
[   163.798] 	LinBlueMaskSize: 5
[   163.798] 	LinBlueFieldPosition: 0
[   163.798] 	LinRsvdMaskSize: 0
[   163.798] 	LinRsvdFieldPosition: 0
[   163.798] 	MaxPixelClock: 400000000
[   163.799] Mode: 175 (1600x1200)
[   163.799] 	ModeAttributes: 0xbb
[   163.799] 	WinAAttributes: 0x7
[   163.799] 	WinBAttributes: 0x0
[   163.799] 	WinGranularity: 64
[   163.799] 	WinSize: 64
[   163.799] 	WinASegment: 0xa000
[   163.799] 	WinBSegment: 0x0
[   163.799] 	WinFuncPtr: 0xc0004d11
[   163.799] 	BytesPerScanline: 3200
[   163.799] 	XResolution: 1600
[   163.799] 	YResolution: 1200
[   163.799] 	XCharSize: 8
[   163.799] 	YCharSize: 16
[   163.799] 	NumberOfPlanes: 1
[   163.799] 	BitsPerPixel: 16
[   163.799] 	NumberOfBanks: 1
[   163.799] 	MemoryModel: 6
[   163.799] 	BankSize: 0
[   163.799] 	NumberOfImages: 3
[   163.799] 	RedMaskSize: 5
[   163.799] 	RedFieldPosition: 11
[   163.799] 	GreenMaskSize: 6
[   163.799] 	GreenFieldPosition: 5
[   163.799] 	BlueMaskSize: 5
[   163.799] 	BlueFieldPosition: 0
[   163.799] 	RsvdMaskSize: 0
[   163.799] 	RsvdFieldPosition: 0
[   163.799] 	DirectColorModeInfo: 0
[   163.799] 	PhysBasePtr: 0xd0000000
[   163.799] 	LinBytesPerScanLine: 3200
[   163.799] 	BnkNumberOfImagePages: 3
[   163.799] 	LinNumberOfImagePages: 3
[   163.799] 	LinRedMaskSize: 5
[   163.799] 	LinRedFieldPosition: 11
[   163.799] 	LinGreenMaskSize: 6
[   163.799] 	LinGreenFieldPosition: 5
[   163.799] 	LinBlueMaskSize: 5
[   163.799] 	LinBlueFieldPosition: 0
[   163.799] 	LinRsvdMaskSize: 0
[   163.799] 	LinRsvdFieldPosition: 0
[   163.799] 	MaxPixelClock: 400000000
[   163.799] *Mode: 176 (1600x1200)
[   163.799] 	ModeAttributes: 0xbb
[   163.799] 	WinAAttributes: 0x7
[   163.799] 	WinBAttributes: 0x0
[   163.799] 	WinGranularity: 64
[   163.799] 	WinSize: 64
[   163.799] 	WinASegment: 0xa000
[   163.799] 	WinBSegment: 0x0
[   163.799] 	WinFuncPtr: 0xc0004d11
[   163.799] 	BytesPerScanline: 6400
[   163.799] 	XResolution: 1600
[   163.799] 	YResolution: 1200
[   163.799] 	XCharSize: 8
[   163.799] 	YCharSize: 16
[   163.799] 	NumberOfPlanes: 1
[   163.799] 	BitsPerPixel: 32
[   163.799] 	NumberOfBanks: 1
[   163.799] 	MemoryModel: 6
[   163.800] 	BankSize: 0
[   163.800] 	NumberOfImages: 1
[   163.800] 	RedMaskSize: 8
[   163.800] 	RedFieldPosition: 16
[   163.800] 	GreenMaskSize: 8
[   163.800] 	GreenFieldPosition: 8
[   163.800] 	BlueMaskSize: 8
[   163.800] 	BlueFieldPosition: 0
[   163.800] 	RsvdMaskSize: 0
[   163.800] 	RsvdFieldPosition: 0
[   163.800] 	DirectColorModeInfo: 0
[   163.800] 	PhysBasePtr: 0xd0000000
[   163.800] 	LinBytesPerScanLine: 6400
[   163.800] 	BnkNumberOfImagePages: 1
[   163.800] 	LinNumberOfImagePages: 1
[   163.800] 	LinRedMaskSize: 8
[   163.800] 	LinRedFieldPosition: 16
[   163.800] 	LinGreenMaskSize: 8
[   163.800] 	LinGreenFieldPosition: 8
[   163.800] 	LinBlueMaskSize: 8
[   163.800] 	LinBlueFieldPosition: 0
[   163.800] 	LinRsvdMaskSize: 0
[   163.800] 	LinRsvdFieldPosition: 0
[   163.800] 	MaxPixelClock: 400000000
[   163.800] Mode: 183 (640x400)
[   163.800] 	ModeAttributes: 0xbb
[   163.800] 	WinAAttributes: 0x7
[   163.800] 	WinBAttributes: 0x0
[   163.800] 	WinGranularity: 64
[   163.800] 	WinSize: 64
[   163.800] 	WinASegment: 0xa000
[   163.800] 	WinBSegment: 0x0
[   163.800] 	WinFuncPtr: 0xc0004d11
[   163.800] 	BytesPerScanline: 640
[   163.800] 	XResolution: 640
[   163.800] 	YResolution: 400
[   163.800] 	XCharSize: 8
[   163.800] 	YCharSize: 16
[   163.800] 	NumberOfPlanes: 1
[   163.800] 	BitsPerPixel: 8
[   163.800] 	NumberOfBanks: 1
[   163.800] 	MemoryModel: 4
[   163.800] 	BankSize: 0
[   163.800] 	NumberOfImages: 63
[   163.800] 	RedMaskSize: 0
[   163.800] 	RedFieldPosition: 0
[   163.800] 	GreenMaskSize: 0
[   163.800] 	GreenFieldPosition: 0
[   163.800] 	BlueMaskSize: 0
[   163.800] 	BlueFieldPosition: 0
[   163.800] 	RsvdMaskSize: 0
[   163.800] 	RsvdFieldPosition: 0
[   163.800] 	DirectColorModeInfo: 0
[   163.800] 	PhysBasePtr: 0xd0000000
[   163.800] 	LinBytesPerScanLine: 640
[   163.800] 	BnkNumberOfImagePages: 63
[   163.800] 	LinNumberOfImagePages: 63
[   163.800] 	LinRedMaskSize: 0
[   163.800] 	LinRedFieldPosition: 0
[   163.800] 	LinGreenMaskSize: 0
[   163.800] 	LinGreenFieldPosition: 0
[   163.800] 	LinBlueMaskSize: 0
[   163.800] 	LinBlueFieldPosition: 0
[   163.800] 	LinRsvdMaskSize: 0
[   163.800] 	LinRsvdFieldPosition: 0
[   163.800] 	MaxPixelClock: 400000000
[   163.801] Mode: 184 (640x400)
[   163.801] 	ModeAttributes: 0xbb
[   163.801] 	WinAAttributes: 0x7
[   163.801] 	WinBAttributes: 0x0
[   163.801] 	WinGranularity: 64
[   163.801] 	WinSize: 64
[   163.801] 	WinASegment: 0xa000
[   163.801] 	WinBSegment: 0x0
[   163.801] 	WinFuncPtr: 0xc0004d11
[   163.801] 	BytesPerScanline: 1280
[   163.801] 	XResolution: 640
[   163.801] 	YResolution: 400
[   163.801] 	XCharSize: 8
[   163.801] 	YCharSize: 16
[   163.801] 	NumberOfPlanes: 1
[   163.801] 	BitsPerPixel: 16
[   163.801] 	NumberOfBanks: 1
[   163.801] 	MemoryModel: 6
[   163.801] 	BankSize: 0
[   163.801] 	NumberOfImages: 31
[   163.801] 	RedMaskSize: 5
[   163.801] 	RedFieldPosition: 10
[   163.801] 	GreenMaskSize: 5
[   163.801] 	GreenFieldPosition: 5
[   163.801] 	BlueMaskSize: 5
[   163.801] 	BlueFieldPosition: 0
[   163.801] 	RsvdMaskSize: 0
[   163.801] 	RsvdFieldPosition: 0
[   163.801] 	DirectColorModeInfo: 0
[   163.801] 	PhysBasePtr: 0xd0000000
[   163.801] 	LinBytesPerScanLine: 1280
[   163.801] 	BnkNumberOfImagePages: 31
[   163.801] 	LinNumberOfImagePages: 31
[   163.801] 	LinRedMaskSize: 5
[   163.801] 	LinRedFieldPosition: 10
[   163.801] 	LinGreenMaskSize: 5
[   163.801] 	LinGreenFieldPosition: 5
[   163.801] 	LinBlueMaskSize: 5
[   163.801] 	LinBlueFieldPosition: 0
[   163.801] 	LinRsvdMaskSize: 0
[   163.801] 	LinRsvdFieldPosition: 0
[   163.801] 	MaxPixelClock: 400000000
[   163.801] Mode: 185 (640x400)
[   163.801] 	ModeAttributes: 0xbb
[   163.801] 	WinAAttributes: 0x7
[   163.801] 	WinBAttributes: 0x0
[   163.801] 	WinGranularity: 64
[   163.801] 	WinSize: 64
[   163.801] 	WinASegment: 0xa000
[   163.801] 	WinBSegment: 0x0
[   163.801] 	WinFuncPtr: 0xc0004d11
[   163.801] 	BytesPerScanline: 1280
[   163.801] 	XResolution: 640
[   163.801] 	YResolution: 400
[   163.801] 	XCharSize: 8
[   163.801] 	YCharSize: 16
[   163.801] 	NumberOfPlanes: 1
[   163.801] 	BitsPerPixel: 16
[   163.801] 	NumberOfBanks: 1
[   163.801] 	MemoryModel: 6
[   163.801] 	BankSize: 0
[   163.801] 	NumberOfImages: 31
[   163.801] 	RedMaskSize: 5
[   163.801] 	RedFieldPosition: 11
[   163.801] 	GreenMaskSize: 6
[   163.801] 	GreenFieldPosition: 5
[   163.802] 	BlueMaskSize: 5
[   163.802] 	BlueFieldPosition: 0
[   163.802] 	RsvdMaskSize: 0
[   163.802] 	RsvdFieldPosition: 0
[   163.802] 	DirectColorModeInfo: 0
[   163.802] 	PhysBasePtr: 0xd0000000
[   163.802] 	LinBytesPerScanLine: 1280
[   163.802] 	BnkNumberOfImagePages: 31
[   163.802] 	LinNumberOfImagePages: 31
[   163.802] 	LinRedMaskSize: 5
[   163.802] 	LinRedFieldPosition: 11
[   163.802] 	LinGreenMaskSize: 6
[   163.802] 	LinGreenFieldPosition: 5
[   163.802] 	LinBlueMaskSize: 5
[   163.802] 	LinBlueFieldPosition: 0
[   163.802] 	LinRsvdMaskSize: 0
[   163.802] 	LinRsvdFieldPosition: 0
[   163.802] 	MaxPixelClock: 400000000
[   163.802] *Mode: 186 (640x400)
[   163.802] 	ModeAttributes: 0xbb
[   163.802] 	WinAAttributes: 0x7
[   163.802] 	WinBAttributes: 0x0
[   163.802] 	WinGranularity: 64
[   163.802] 	WinSize: 64
[   163.802] 	WinASegment: 0xa000
[   163.802] 	WinBSegment: 0x0
[   163.802] 	WinFuncPtr: 0xc0004d11
[   163.802] 	BytesPerScanline: 2560
[   163.802] 	XResolution: 640
[   163.802] 	YResolution: 400
[   163.802] 	XCharSize: 8
[   163.802] 	YCharSize: 16
[   163.802] 	NumberOfPlanes: 1
[   163.802] 	BitsPerPixel: 32
[   163.802] 	NumberOfBanks: 1
[   163.802] 	MemoryModel: 6
[   163.802] 	BankSize: 0
[   163.802] 	NumberOfImages: 15
[   163.802] 	RedMaskSize: 8
[   163.802] 	RedFieldPosition: 16
[   163.802] 	GreenMaskSize: 8
[   163.802] 	GreenFieldPosition: 8
[   163.802] 	BlueMaskSize: 8
[   163.802] 	BlueFieldPosition: 0
[   163.802] 	RsvdMaskSize: 0
[   163.802] 	RsvdFieldPosition: 0
[   163.802] 	DirectColorModeInfo: 0
[   163.802] 	PhysBasePtr: 0xd0000000
[   163.802] 	LinBytesPerScanLine: 2560
[   163.802] 	BnkNumberOfImagePages: 15
[   163.802] 	LinNumberOfImagePages: 15
[   163.802] 	LinRedMaskSize: 8
[   163.802] 	LinRedFieldPosition: 16
[   163.802] 	LinGreenMaskSize: 8
[   163.802] 	LinGreenFieldPosition: 8
[   163.802] 	LinBlueMaskSize: 8
[   163.802] 	LinBlueFieldPosition: 0
[   163.802] 	LinRsvdMaskSize: 0
[   163.802] 	LinRsvdFieldPosition: 0
[   163.802] 	MaxPixelClock: 400000000
[   163.803] Mode: 1d3 (1856x1392)
[   163.803] 	ModeAttributes: 0xbb
[   163.803] 	WinAAttributes: 0x7
[   163.803] 	WinBAttributes: 0x0
[   163.803] 	WinGranularity: 64
[   163.803] 	WinSize: 64
[   163.803] 	WinASegment: 0xa000
[   163.803] 	WinBSegment: 0x0
[   163.803] 	WinFuncPtr: 0xc0004d11
[   163.803] 	BytesPerScanline: 1856
[   163.803] 	XResolution: 1856
[   163.803] 	YResolution: 1392
[   163.803] 	XCharSize: 8
[   163.803] 	YCharSize: 16
[   163.803] 	NumberOfPlanes: 1
[   163.803] 	BitsPerPixel: 8
[   163.803] 	NumberOfBanks: 1
[   163.803] 	MemoryModel: 4
[   163.803] 	BankSize: 0
[   163.803] 	NumberOfImages: 5
[   163.803] 	RedMaskSize: 0
[   163.803] 	RedFieldPosition: 0
[   163.803] 	GreenMaskSize: 0
[   163.803] 	GreenFieldPosition: 0
[   163.803] 	BlueMaskSize: 0
[   163.803] 	BlueFieldPosition: 0
[   163.803] 	RsvdMaskSize: 0
[   163.803] 	RsvdFieldPosition: 0
[   163.803] 	DirectColorModeInfo: 0
[   163.803] 	PhysBasePtr: 0xd0000000
[   163.803] 	LinBytesPerScanLine: 1856
[   163.803] 	BnkNumberOfImagePages: 5
[   163.803] 	LinNumberOfImagePages: 5
[   163.803] 	LinRedMaskSize: 0
[   163.803] 	LinRedFieldPosition: 0
[   163.803] 	LinGreenMaskSize: 0
[   163.803] 	LinGreenFieldPosition: 0
[   163.803] 	LinBlueMaskSize: 0
[   163.803] 	LinBlueFieldPosition: 0
[   163.803] 	LinRsvdMaskSize: 0
[   163.803] 	LinRsvdFieldPosition: 0
[   163.803] 	MaxPixelClock: 400000000
[   163.803] Mode: 1d4 (1856x1392)
[   163.803] 	ModeAttributes: 0xbb
[   163.803] 	WinAAttributes: 0x7
[   163.803] 	WinBAttributes: 0x0
[   163.803] 	WinGranularity: 64
[   163.803] 	WinSize: 64
[   163.803] 	WinASegment: 0xa000
[   163.803] 	WinBSegment: 0x0
[   163.803] 	WinFuncPtr: 0xc0004d11
[   163.803] 	BytesPerScanline: 3712
[   163.803] 	XResolution: 1856
[   163.803] 	YResolution: 1392
[   163.803] 	XCharSize: 8
[   163.803] 	YCharSize: 16
[   163.803] 	NumberOfPlanes: 1
[   163.803] 	BitsPerPixel: 16
[   163.803] 	NumberOfBanks: 1
[   163.803] 	MemoryModel: 6
[   163.803] 	BankSize: 0
[   163.803] 	NumberOfImages: 2
[   163.804] 	RedMaskSize: 5
[   163.804] 	RedFieldPosition: 10
[   163.804] 	GreenMaskSize: 5
[   163.804] 	GreenFieldPosition: 5
[   163.804] 	BlueMaskSize: 5
[   163.804] 	BlueFieldPosition: 0
[   163.804] 	RsvdMaskSize: 0
[   163.804] 	RsvdFieldPosition: 0
[   163.804] 	DirectColorModeInfo: 0
[   163.804] 	PhysBasePtr: 0xd0000000
[   163.804] 	LinBytesPerScanLine: 3712
[   163.804] 	BnkNumberOfImagePages: 2
[   163.804] 	LinNumberOfImagePages: 2
[   163.804] 	LinRedMaskSize: 5
[   163.804] 	LinRedFieldPosition: 10
[   163.804] 	LinGreenMaskSize: 5
[   163.804] 	LinGreenFieldPosition: 5
[   163.804] 	LinBlueMaskSize: 5
[   163.804] 	LinBlueFieldPosition: 0
[   163.804] 	LinRsvdMaskSize: 0
[   163.804] 	LinRsvdFieldPosition: 0
[   163.804] 	MaxPixelClock: 400000000
[   163.804] Mode: 1d5 (1856x1392)
[   163.804] 	ModeAttributes: 0xbb
[   163.804] 	WinAAttributes: 0x7
[   163.804] 	WinBAttributes: 0x0
[   163.804] 	WinGranularity: 64
[   163.804] 	WinSize: 64
[   163.804] 	WinASegment: 0xa000
[   163.804] 	WinBSegment: 0x0
[   163.804] 	WinFuncPtr: 0xc0004d11
[   163.804] 	BytesPerScanline: 3712
[   163.804] 	XResolution: 1856
[   163.804] 	YResolution: 1392
[   163.804] 	XCharSize: 8
[   163.804] 	YCharSize: 16
[   163.804] 	NumberOfPlanes: 1
[   163.804] 	BitsPerPixel: 16
[   163.804] 	NumberOfBanks: 1
[   163.804] 	MemoryModel: 6
[   163.804] 	BankSize: 0
[   163.804] 	NumberOfImages: 2
[   163.804] 	RedMaskSize: 5
[   163.804] 	RedFieldPosition: 11
[   163.804] 	GreenMaskSize: 6
[   163.804] 	GreenFieldPosition: 5
[   163.804] 	BlueMaskSize: 5
[   163.804] 	BlueFieldPosition: 0
[   163.804] 	RsvdMaskSize: 0
[   163.804] 	RsvdFieldPosition: 0
[   163.804] 	DirectColorModeInfo: 0
[   163.804] 	PhysBasePtr: 0xd0000000
[   163.804] 	LinBytesPerScanLine: 3712
[   163.804] 	BnkNumberOfImagePages: 2
[   163.804] 	LinNumberOfImagePages: 2
[   163.804] 	LinRedMaskSize: 5
[   163.804] 	LinRedFieldPosition: 11
[   163.804] 	LinGreenMaskSize: 6
[   163.804] 	LinGreenFieldPosition: 5
[   163.804] 	LinBlueMaskSize: 5
[   163.804] 	LinBlueFieldPosition: 0
[   163.804] 	LinRsvdMaskSize: 0
[   163.804] 	LinRsvdFieldPosition: 0
[   163.804] 	MaxPixelClock: 400000000
[   163.805] *Mode: 1d6 (1856x1392)
[   163.805] 	ModeAttributes: 0xbb
[   163.805] 	WinAAttributes: 0x7
[   163.805] 	WinBAttributes: 0x0
[   163.805] 	WinGranularity: 64
[   163.805] 	WinSize: 64
[   163.805] 	WinASegment: 0xa000
[   163.805] 	WinBSegment: 0x0
[   163.805] 	WinFuncPtr: 0xc0004d11
[   163.805] 	BytesPerScanline: 7424
[   163.805] 	XResolution: 1856
[   163.805] 	YResolution: 1392
[   163.805] 	XCharSize: 8
[   163.805] 	YCharSize: 16
[   163.805] 	NumberOfPlanes: 1
[   163.805] 	BitsPerPixel: 32
[   163.805] 	NumberOfBanks: 1
[   163.805] 	MemoryModel: 6
[   163.805] 	BankSize: 0
[   163.805] 	NumberOfImages: 1
[   163.805] 	RedMaskSize: 8
[   163.805] 	RedFieldPosition: 16
[   163.805] 	GreenMaskSize: 8
[   163.805] 	GreenFieldPosition: 8
[   163.805] 	BlueMaskSize: 8
[   163.805] 	BlueFieldPosition: 0
[   163.805] 	RsvdMaskSize: 0
[   163.805] 	RsvdFieldPosition: 0
[   163.805] 	DirectColorModeInfo: 0
[   163.805] 	PhysBasePtr: 0xd0000000
[   163.805] 	LinBytesPerScanLine: 7424
[   163.805] 	BnkNumberOfImagePages: 1
[   163.805] 	LinNumberOfImagePages: 1
[   163.805] 	LinRedMaskSize: 8
[   163.805] 	LinRedFieldPosition: 16
[   163.805] 	LinGreenMaskSize: 8
[   163.805] 	LinGreenFieldPosition: 8
[   163.805] 	LinBlueMaskSize: 8
[   163.805] 	LinBlueFieldPosition: 0
[   163.805] 	LinRsvdMaskSize: 0
[   163.805] 	LinRsvdFieldPosition: 0
[   163.805] 	MaxPixelClock: 400000000
[   163.805] Mode: 1e3 (1920x1440)
[   163.805] 	ModeAttributes: 0xbb
[   163.805] 	WinAAttributes: 0x7
[   163.805] 	WinBAttributes: 0x0
[   163.805] 	WinGranularity: 64
[   163.805] 	WinSize: 64
[   163.805] 	WinASegment: 0xa000
[   163.805] 	WinBSegment: 0x0
[   163.805] 	WinFuncPtr: 0xc0004d11
[   163.805] 	BytesPerScanline: 1920
[   163.805] 	XResolution: 1920
[   163.805] 	YResolution: 1440
[   163.806] 	XCharSize: 8
[   163.806] 	YCharSize: 16
[   163.806] 	NumberOfPlanes: 1
[   163.806] 	BitsPerPixel: 8
[   163.806] 	NumberOfBanks: 1
[   163.806] 	MemoryModel: 4
[   163.806] 	BankSize: 0
[   163.806] 	NumberOfImages: 4
[   163.806] 	RedMaskSize: 0
[   163.806] 	RedFieldPosition: 0
[   163.806] 	GreenMaskSize: 0
[   163.806] 	GreenFieldPosition: 0
[   163.806] 	BlueMaskSize: 0
[   163.806] 	BlueFieldPosition: 0
[   163.806] 	RsvdMaskSize: 0
[   163.806] 	RsvdFieldPosition: 0
[   163.806] 	DirectColorModeInfo: 0
[   163.806] 	PhysBasePtr: 0xd0000000
[   163.806] 	LinBytesPerScanLine: 1920
[   163.806] 	BnkNumberOfImagePages: 4
[   163.806] 	LinNumberOfImagePages: 4
[   163.806] 	LinRedMaskSize: 0
[   163.806] 	LinRedFieldPosition: 0
[   163.806] 	LinGreenMaskSize: 0
[   163.806] 	LinGreenFieldPosition: 0
[   163.806] 	LinBlueMaskSize: 0
[   163.806] 	LinBlueFieldPosition: 0
[   163.806] 	LinRsvdMaskSize: 0
[   163.806] 	LinRsvdFieldPosition: 0
[   163.806] 	MaxPixelClock: 400000000
[   163.806] Mode: 1e4 (1920x1440)
[   163.806] 	ModeAttributes: 0xbb
[   163.806] 	WinAAttributes: 0x7
[   163.806] 	WinBAttributes: 0x0
[   163.806] 	WinGranularity: 64
[   163.806] 	WinSize: 64
[   163.806] 	WinASegment: 0xa000
[   163.806] 	WinBSegment: 0x0
[   163.806] 	WinFuncPtr: 0xc0004d11
[   163.806] 	BytesPerScanline: 3840
[   163.806] 	XResolution: 1920
[   163.806] 	YResolution: 1440
[   163.806] 	XCharSize: 8
[   163.806] 	YCharSize: 16
[   163.806] 	NumberOfPlanes: 1
[   163.806] 	BitsPerPixel: 16
[   163.806] 	NumberOfBanks: 1
[   163.806] 	MemoryModel: 6
[   163.806] 	BankSize: 0
[   163.806] 	NumberOfImages: 2
[   163.806] 	RedMaskSize: 5
[   163.806] 	RedFieldPosition: 10
[   163.806] 	GreenMaskSize: 5
[   163.806] 	GreenFieldPosition: 5
[   163.806] 	BlueMaskSize: 5
[   163.806] 	BlueFieldPosition: 0
[   163.806] 	RsvdMaskSize: 0
[   163.806] 	RsvdFieldPosition: 0
[   163.806] 	DirectColorModeInfo: 0
[   163.806] 	PhysBasePtr: 0xd0000000
[   163.806] 	LinBytesPerScanLine: 3840
[   163.806] 	BnkNumberOfImagePages: 2
[   163.806] 	LinNumberOfImagePages: 2
[   163.806] 	LinRedMaskSize: 5
[   163.806] 	LinRedFieldPosition: 10
[   163.806] 	LinGreenMaskSize: 5
[   163.806] 	LinGreenFieldPosition: 5
[   163.806] 	LinBlueMaskSize: 5
[   163.806] 	LinBlueFieldPosition: 0
[   163.806] 	LinRsvdMaskSize: 0
[   163.806] 	LinRsvdFieldPosition: 0
[   163.806] 	MaxPixelClock: 400000000
[   163.807] Mode: 1e5 (1920x1440)
[   163.807] 	ModeAttributes: 0xbb
[   163.807] 	WinAAttributes: 0x7
[   163.807] 	WinBAttributes: 0x0
[   163.807] 	WinGranularity: 64
[   163.807] 	WinSize: 64
[   163.807] 	WinASegment: 0xa000
[   163.807] 	WinBSegment: 0x0
[   163.807] 	WinFuncPtr: 0xc0004d11
[   163.807] 	BytesPerScanline: 3840
[   163.807] 	XResolution: 1920
[   163.807] 	YResolution: 1440
[   163.807] 	XCharSize: 8
[   163.807] 	YCharSize: 16
[   163.807] 	NumberOfPlanes: 1
[   163.807] 	BitsPerPixel: 16
[   163.807] 	NumberOfBanks: 1
[   163.807] 	MemoryModel: 6
[   163.807] 	BankSize: 0
[   163.807] 	NumberOfImages: 2
[   163.807] 	RedMaskSize: 5
[   163.807] 	RedFieldPosition: 11
[   163.807] 	GreenMaskSize: 6
[   163.807] 	GreenFieldPosition: 5
[   163.807] 	BlueMaskSize: 5
[   163.807] 	BlueFieldPosition: 0
[   163.807] 	RsvdMaskSize: 0
[   163.807] 	RsvdFieldPosition: 0
[   163.807] 	DirectColorModeInfo: 0
[   163.807] 	PhysBasePtr: 0xd0000000
[   163.807] 	LinBytesPerScanLine: 3840
[   163.807] 	BnkNumberOfImagePages: 2
[   163.807] 	LinNumberOfImagePages: 2
[   163.807] 	LinRedMaskSize: 5
[   163.807] 	LinRedFieldPosition: 11
[   163.807] 	LinGreenMaskSize: 6
[   163.807] 	LinGreenFieldPosition: 5
[   163.807] 	LinBlueMaskSize: 5
[   163.807] 	LinBlueFieldPosition: 0
[   163.807] 	LinRsvdMaskSize: 0
[   163.807] 	LinRsvdFieldPosition: 0
[   163.807] 	MaxPixelClock: 400000000
[   163.807] *Mode: 1e6 (1920x1440)
[   163.807] 	ModeAttributes: 0xbb
[   163.807] 	WinAAttributes: 0x7
[   163.808] 	WinBAttributes: 0x0
[   163.808] 	WinGranularity: 64
[   163.808] 	WinSize: 64
[   163.808] 	WinASegment: 0xa000
[   163.808] 	WinBSegment: 0x0
[   163.808] 	WinFuncPtr: 0xc0004d11
[   163.808] 	BytesPerScanline: 7680
[   163.808] 	XResolution: 1920
[   163.808] 	YResolution: 1440
[   163.808] 	XCharSize: 8
[   163.808] 	YCharSize: 16
[   163.808] 	NumberOfPlanes: 1
[   163.808] 	BitsPerPixel: 32
[   163.808] 	NumberOfBanks: 1
[   163.808] 	MemoryModel: 6
[   163.808] 	BankSize: 0
[   163.808] 	NumberOfImages: 1
[   163.808] 	RedMaskSize: 8
[   163.808] 	RedFieldPosition: 16
[   163.808] 	GreenMaskSize: 8
[   163.808] 	GreenFieldPosition: 8
[   163.808] 	BlueMaskSize: 8
[   163.808] 	BlueFieldPosition: 0
[   163.808] 	RsvdMaskSize: 0
[   163.808] 	RsvdFieldPosition: 0
[   163.808] 	DirectColorModeInfo: 0
[   163.808] 	PhysBasePtr: 0xd0000000
[   163.808] 	LinBytesPerScanLine: 7680
[   163.808] 	BnkNumberOfImagePages: 1
[   163.808] 	LinNumberOfImagePages: 1
[   163.808] 	LinRedMaskSize: 8
[   163.808] 	LinRedFieldPosition: 16
[   163.808] 	LinGreenMaskSize: 8
[   163.808] 	LinGreenFieldPosition: 8
[   163.808] 	LinBlueMaskSize: 8
[   163.808] 	LinBlueFieldPosition: 0
[   163.808] 	LinRsvdMaskSize: 0
[   163.808] 	LinRsvdFieldPosition: 0
[   163.808] 	MaxPixelClock: 400000000
[   163.808] 
[   163.808] (II) VESA(0): Total Memory: 256 64KB banks (16384kB)
[   163.808] (II) VESA(0): <default monitor>: Using hsync range of 31.00-84.00 kHz
[   163.808] (II) VESA(0): <default monitor>: Using vrefresh range of 56.00-76.00 Hz
[   163.808] (II) VESA(0): <default monitor>: Using maximum pixel clock of 145.00 MHz
[   163.808] (WW) VESA(0): Unable to estimate virtual size
[   163.808] (II) VESA(0): Not using built-in mode "1920x1440" (no mode of this name)
[   163.808] (II) VESA(0): Not using built-in mode "1856x1392" (no mode of this name)
[   163.808] (II) VESA(0): Not using built-in mode "1600x1200" (no mode of this name)
[   163.808] (II) VESA(0): Not using built-in mode "1400x1050" (no mode of this name)
[   163.809] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[   163.809] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[   163.809] (II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
[   163.809] (II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
[   163.809] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[   163.809] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[   163.809] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[   163.809] (--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
[   163.809] (**) VESA(0): *Built-in mode "1280x1024"
[   163.809] (**) VESA(0): *Built-in mode "1280x1024"
[   163.809] (**) VESA(0): *Built-in mode "1280x1024"
[   163.809] (**) VESA(0): *Built-in mode "1152x864"
[   163.809] (**) VESA(0): *Built-in mode "1024x768"
[   163.809] (**) VESA(0): *Built-in mode "1024x768"
[   163.809] (**) VESA(0): *Built-in mode "800x600"
[   163.810] (**) VESA(0): *Built-in mode "800x600"
[   163.810] (**) VESA(0): *Built-in mode "640x480"
[   163.810] (**) VESA(0): *Built-in mode "640x480"
[   163.810] (**) VESA(0): *Built-in mode "720x400"
[   163.810] (**) VESA(0): Display dimensions: (410, 260) mm
[   163.810] (**) VESA(0): DPI set to (79, 100)
[   163.810] (**) VESA(0): Using "Shadow Framebuffer"
[   163.810] (II) Loading sub module "shadow"
[   163.810] (II) LoadModule: "shadow"
[   163.810] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   163.810] (II) Module shadow: vendor="X.Org Foundation"
[   163.810] 	compiled for 1.13.0, module version = 1.1.0
[   163.810] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   163.810] (II) Loading sub module "fb"
[   163.810] (II) LoadModule: "fb"
[   163.811] (II) Loading /usr/lib/xorg/modules/libfb.so
[   163.814] (II) Module fb: vendor="X.Org Foundation"
[   163.814] 	compiled for 1.13.0, module version = 1.0.0
[   163.814] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   163.814] (II) UnloadModule: "radeon"
[   163.814] (II) UnloadModule: "modesetting"
[   163.814] (II) Unloading modesetting
[   163.814] (II) UnloadModule: "fbdev"
[   163.814] (II) Unloading fbdev
[   163.814] (II) UnloadSubModule: "fbdevhw"
[   163.814] (II) Unloading fbdevhw
[   163.814] (==) Depth 24 pixmap format is 32 bpp
[   163.814] (II) Loading sub module "int10"
[   163.814] (II) LoadModule: "int10"
[   163.815] (II) Loading /usr/lib/xorg/modules/libint10.so
[   163.815] (II) Module int10: vendor="X.Org Foundation"
[   163.815] 	compiled for 1.13.0, module version = 1.0.0
[   163.815] 	ABI class: X.Org Video Driver, version 13.0
[   163.815] (II) VESA(0): initializing int10
[   163.974] (II) VESA(0): VESA BIOS detected
[   163.974] (II) VESA(0): VESA VBE Version 3.0
[   163.974] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[   163.974] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[   163.974] (II) VESA(0): VESA VBE OEM Software Rev: 9.12
[   163.974] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[   163.974] (II) VESA(0): VESA VBE OEM Product: RV516
[   163.974] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[   163.975] (II) VESA(0): virtual address = 0xb5dc2000,
	physical address = 0xd0000000, size = 16777216
[   163.988] (II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)
[   163.988] (II) VESA(0): VBESetVBEMode failed, mode set without customized refresh.
[   164.042] (==) VESA(0): Default visual is TrueColor
[   164.048] (==) VESA(0): Backing store disabled
[   164.049] (==) VESA(0): DPMS enabled
[   164.049] (==) RandR enabled
[   164.060] (II) AIGLX: Screen 0 is not DRI2 capable
[   164.061] (II) AIGLX: Screen 0 is not DRI capable
[   165.370] (II) AIGLX: Loaded and initialized swrast
[   165.370] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   165.482] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   165.681] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   165.681] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   165.681] (II) LoadModule: "evdev"
[   165.682] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   165.702] (II) Module evdev: vendor="X.Org Foundation"
[   165.702] 	compiled for 1.13.0, module version = 2.7.3
[   165.702] 	Module class: X.Org XInput Driver
[   165.702] 	ABI class: X.Org XInput driver, version 18.0
[   165.702] (II) Using input driver 'evdev' for 'Power Button'
[   165.702] (**) Power Button: always reports core events
[   165.702] (**) evdev: Power Button: Device: "/dev/input/event1"
[   165.702] (--) evdev: Power Button: Vendor 0 Product 0x1
[   165.702] (--) evdev: Power Button: Found keys
[   165.702] (II) evdev: Power Button: Configuring as keyboard
[   165.702] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   165.702] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   165.702] (**) Option "xkb_rules" "evdev"
[   165.702] (**) Option "xkb_model" "pc105"
[   165.702] (**) Option "xkb_layout" "us"
[   165.703] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   165.703] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   165.703] (II) Using input driver 'evdev' for 'Power Button'
[   165.703] (**) Power Button: always reports core events
[   165.703] (**) evdev: Power Button: Device: "/dev/input/event0"
[   165.703] (--) evdev: Power Button: Vendor 0 Product 0x1
[   165.703] (--) evdev: Power Button: Found keys
[   165.703] (II) evdev: Power Button: Configuring as keyboard
[   165.703] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   165.703] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   165.703] (**) Option "xkb_rules" "evdev"
[   165.703] (**) Option "xkb_model" "pc105"
[   165.703] (**) Option "xkb_layout" "us"
[   165.704] (II) config/udev: Adding drm device (/dev/dri/card0)
[   165.704] (II) config/udev: Adding input device Chicony USB Keyboard (/dev/input/event2)
[   165.704] (**) Chicony USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   165.704] (II) Using input driver 'evdev' for 'Chicony USB Keyboard'
[   165.704] (**) Chicony USB Keyboard: always reports core events
[   165.704] (**) evdev: Chicony USB Keyboard: Device: "/dev/input/event2"
[   165.704] (--) evdev: Chicony USB Keyboard: Vendor 0x4f2 Product 0x111
[   165.704] (--) evdev: Chicony USB Keyboard: Found keys
[   165.704] (II) evdev: Chicony USB Keyboard: Configuring as keyboard
[   165.704] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.0/input/input2/event2"
[   165.704] (II) XINPUT: Adding extended input device "Chicony USB Keyboard" (type: KEYBOARD, id 8)
[   165.704] (**) Option "xkb_rules" "evdev"
[   165.705] (**) Option "xkb_model" "pc105"
[   165.705] (**) Option "xkb_layout" "us"
[   165.705] (II) config/udev: Adding input device Chicony USB Keyboard (/dev/input/event3)
[   165.705] (**) Chicony USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   165.706] (II) Using input driver 'evdev' for 'Chicony USB Keyboard'
[   165.706] (**) Chicony USB Keyboard: always reports core events
[   165.706] (**) evdev: Chicony USB Keyboard: Device: "/dev/input/event3"
[   165.706] (--) evdev: Chicony USB Keyboard: Vendor 0x4f2 Product 0x111
[   165.706] (--) evdev: Chicony USB Keyboard: Found keys
[   165.706] (II) evdev: Chicony USB Keyboard: Configuring as keyboard
[   165.706] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.1/input/input3/event3"
[   165.706] (II) XINPUT: Adding extended input device "Chicony USB Keyboard" (type: KEYBOARD, id 9)
[   165.706] (**) Option "xkb_rules" "evdev"
[   165.706] (**) Option "xkb_model" "pc105"
[   165.706] (**) Option "xkb_layout" "us"
[   165.706] (II) config/udev: Adding input device HDA SIS966 Line Out Surround (/dev/input/event10)
[   165.707] (II) No input driver specified, ignoring this device.
[   165.707] (II) This device may have been added with another device file.
[   165.707] (II) config/udev: Adding input device HDA SIS966 Line Out Front (/dev/input/event11)
[   165.707] (II) No input driver specified, ignoring this device.
[   165.707] (II) This device may have been added with another device file.
[   165.707] (II) config/udev: Adding input device HDA SIS966 Line (/dev/input/event4)
[   165.707] (II) No input driver specified, ignoring this device.
[   165.707] (II) This device may have been added with another device file.
[   165.708] (II) config/udev: Adding input device HDA SIS966 Front Mic (/dev/input/event5)
[   165.708] (II) No input driver specified, ignoring this device.
[   165.708] (II) This device may have been added with another device file.
[   165.708] (II) config/udev: Adding input device HDA SIS966 Rear Mic (/dev/input/event6)
[   165.708] (II) No input driver specified, ignoring this device.
[   165.708] (II) This device may have been added with another device file.
[   165.709] (II) config/udev: Adding input device HDA SIS966 Front Headphone (/dev/input/event7)
[   165.709] (II) No input driver specified, ignoring this device.
[   165.709] (II) This device may have been added with another device file.
[   165.709] (II) config/udev: Adding input device HDA SIS966 Line Out Side (/dev/input/event8)
[   165.709] (II) No input driver specified, ignoring this device.
[   165.709] (II) This device may have been added with another device file.
[   165.709] (II) config/udev: Adding input device HDA SIS966 Line Out CLFE (/dev/input/event9)
[   165.709] (II) No input driver specified, ignoring this device.
[   165.709] (II) This device may have been added with another device file.
[   165.710] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event12)
[   165.710] (**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
[   165.710] (II) Using input driver 'evdev' for 'ImPS/2 Generic Wheel Mouse'
[   165.710] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[   165.710] (**) evdev: ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event12"
[   165.710] (--) evdev: ImPS/2 Generic Wheel Mouse: Vendor 0x2 Product 0x5
[   165.710] (--) evdev: ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[   165.710] (--) evdev: ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
[   165.710] (--) evdev: ImPS/2 Generic Wheel Mouse: Found relative axes
[   165.710] (--) evdev: ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[   165.710] (II) evdev: ImPS/2 Generic Wheel Mouse: Configuring as mouse
[   165.710] (II) evdev: ImPS/2 Generic Wheel Mouse: Adding scrollwheel support
[   165.710] (**) evdev: ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[   165.710] (**) evdev: ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   165.710] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input12/event12"
[   165.710] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE, id 10)
[   165.710] (II) evdev: ImPS/2 Generic Wheel Mouse: initialized for relative axes.
[   165.711] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[   165.711] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration profile 0
[   165.711] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration factor: 2.000
[   165.711] (**) ImPS/2 Generic Wheel Mouse: (accel) acceleration threshold: 4
[   165.711] (II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse0)
[   165.711] (II) No input driver specified, ignoring this device.
[   165.711] (II) This device may have been added with another device file.
[   251.340] (II) XKB: generating xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[   466.085] (II) VESA(0): Setting up VESA Mode 0x156 (1152x864)
[   466.085] (II) VESA(0): VBESetVBEMode failed, mode set without customized refresh.

```

The result from 'xrandr -q':
```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 400, current 1152 x 864, maximum 1280 x 1024
default connected 1152x864+0+0 0mm x 0mm
   1280x1024       0.0  
   1152x864        0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  
   720x400         0.0

```

The resolution I want to get is 1440x900, which is what I get automatically on 12.04. 12.10 starts up with 1280x1024 as the default and then I changed it in System Settings to 1152x854. Sorry, I still haven't been able to find the thread that said XOrg had come out with a new version of S Server; perhaps it wasn't on Ubuntuforums. I don't find the search function in Firfox History congenial.

By the way, thank you for your help. I feel a little bad about taking up so much of your time.

---

### Post by kurt18947 on 2013-02-01
> **Acharn said:**
> This seems like an intriguing possibility. There's a graphics connector on the MoBo which doesn't seem to do anything. The graphics card shows up under the 'pci' section when I check 'lshw', but the output doesn't show an onboard graphics processor. The motherboard is an Acer F672CR, and the chipsets used all seem to be SiS. Can you point me to a tutorial on how to disable/enable the onboard graphics chip? Just to play around with. I think I'm going to go for a new graphics card anyway. I was able to find the spec sheet and it says my power supply is 250 Watts, so I suppose I need to spring for that too, but they're only about $10 here in Thailand. Also, I've been pretty happy with the open source Radeon driver. And that's probably what I would prefer to use with the new card. As I said earlier, I'm not into games, or any other applications, that are heavy on graphics.

There should be settings in BIOS to enable/disable onboard graphics and mine also has field to select which to try first.  I disabled integrated graphics and selected "PCI slot" to use first.  I believe even entry level video cards recommend a 300 watt power supply.  The heavy duty graphics cards require a direct connection from the power supply.  Neither of mine do.

---

### Post by Acharn on 2013-02-16
OK, got my income tax refund, so I bought a HIS Radeon HD 6670 yesterday. I really don't know if it was necessary, but I haven't been able to change my settings to 1440x900 in Quantal (12.10) when booting from a USB stick. The best resolution I can get is 1154x768, which isn't terrible. I don't know if I could have done better if I had 12.10 completely installed on my hard drive, and there's teally no pressing reason for me to upgrade to 12.10. I don't care about not having the proprietary driver -- I have never had it. When I bought the box five years ago the Radeon x1550 was already legacy and the Catalyst installer said it wouldn't work with my kernel. So I guess I'll mark this thread [solved].

---

