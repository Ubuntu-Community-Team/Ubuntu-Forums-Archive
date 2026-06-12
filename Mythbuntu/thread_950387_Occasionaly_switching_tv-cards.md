---
title: "Occasionaly switching tv-cards"
date: 2008-10-17
forum: Mythbuntu
---

### Post by pjw1965 on 2008-10-17
Hallo all

My new Mythbuntu is finally up and running with 2 TV Cards.
- PVR-150 (driver ivtv)
- WIN TV  (driver bt878 )

Normally the MPG-Card (PVR-150) is on video0 and the older on video1. Then everything works fine.

Occasionaly they are mapped video0 for bt878 and video1 for ivtv. Then nothing works.

1st try)
I tried to define it with udev-rules, but after a while I had the same problem again. 
One of my tries was in /etc/udev/rules.d/55-custom.rules:
> KERNEL=="video[0-9]", SYSFS{name}=="BT878 video (Hauppauge (bt878))", NAME="video1", ATTRS{subsystem_device}=="0x13eb", SYMLINK+="BT878"
KERNEL=="video[0-9]", SYSFS{name}=="ivtv[0-1] encoder MPEG", NAME="video0", ATTRS{subsystem_device}=="0x8003", SYMLINK+="PVR150"


2nd try)
I tried to add 
> /etc/modprobe.d/aliases: 
alias char-major-81   videodev
alias char-major-81-0 ivtv
alias char-major-81-1 bt878
/etc/modules:
ivtv
bt878

But after a while, same problem again.

3rd try)
Today I tried a workaround in /etc/default/mythtv-backend:
> grep ivtv /sys/class/video4linux/video0/name >/dev/null 2>&1 || {
  for i in ivtv bt878 bttv; do
    rmmod $i;
  done
  sleep 5
  for i in ivtv bttv bt878; do
    modprobe $i
  done
} > /dev/null 2>&1


Is there a better solution?

--- Symstem ---
> $ uname -a
Linux frodo 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux
$ lspci -nnv
01:00.0 Multimedia video controller [0400]: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder [4444:0016] (rev 01)
        Subsystem: Hauppauge computer works Inc. Unknown device [0070:37f3]
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [44] Power Management version 2

01:02.0 Multimedia video controller [0400]: Brooktree Corporation Bt878 Video Capture [109e:036e] (rev 11)
        Subsystem: Hauppauge computer works Inc. WinTV Series [0070:13eb]
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at e6afe000 (32-bit, prefetchable) [size=4K]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2

01:02.1 Multimedia controller [0480]: Brooktree Corporation Bt878 Audio Capture [109e:0878] (rev 11)
        Subsystem: Hauppauge computer works Inc. WinTV Series [0070:13eb]
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at e6aff000 (32-bit, prefetchable) [size=4K]
        Capabilities: [44] Vital Product Data
        Capabilities: [4c] Power Management version 2
$ lsmod | egrep '(ivtv|bt878|bttv)'
bt878                  11832  0
bttv                  175860  1 bt878
ir_common              36100  2 cx88xx,bttv
ivtv                  140352  1
compat_ioctl32          2304  2 cx8800,bttv
videobuf_dma_sg        14980  3 cx8800,cx88xx,bttv
videobuf_core          18820  4 cx8800,cx88xx,bttv,videobuf_dma_sg
btcx_risc               5896  3 cx8800,cx88xx,bttv
cx2341x                13444  1 ivtv
tveeprom               16656  3 cx88xx,bttv,ivtv
videodev               29440  4 cx8800,cx88xx,bttv,ivtv
v4l2_common            18304  10 cx8800,cx88xx,tvaudio,wm8775,cx25840,tuner,bttv,ivtv,cx2341x,videodev
v4l1_compat            15492  3 bttv,ivtv,videodev
i2c_algo_bit            7300  4 cx88xx,bttv,ivtv,i2c_i810
i2c_core               24832  16 cx88xx,lirc_i2c,tvaudio,wm8775,cx25840,tuner,tea5767,tda8290,tuner_simple,mt20xx,tea5761,bttv,ivtv,tveeprom,i2c_i810,i2c_algo_bit
$ dpkg -l | grep myth
ii  gtk2-engines-mythbuntu                     0.4-0ubuntu1                                         Mythbuntu GTK+ 2.x Theme
ii  libmyth-0.21-0                             0.21.0+fixes18207-0ubuntu4~hardy1                    Common library code for MythTV and add-on mo
ii  libmyth-perl                               0.21.0+fixes18207-0ubuntu4~hardy1                    A PERL library to access some MythTV feature
ii  libmyth-python                             0.21.0+fixes18207-0ubuntu4~hardy1                    A python library to access some MythTV featu
ii  mytharchive                                0.21.0+fixes18207-0ubuntu4~hardy1                    create and burn DVD's from MythTV - binary f
ii  mytharchive-data                           0.21.0+fixes18207-0ubuntu4~hardy1                    create and burn DVD's from MythTV - data fil
ii  mythbuntu-artwork-usplash                  0.7-0ubuntu1                                         mythbuntu artwork for usplash
ii  mythbuntu-common                           0.13-0ubuntu1                                        Mythbuntu application support functions
ii  mythbuntu-control-centre                   0.28-0ubuntu1+hardy1                                 Mythbuntu Configuration Application
ii  mythbuntu-default-settings                 0.71-0ubuntu1                                        default settings for Mythbuntu
ii  mythbuntu-desktop                          0.20                                                 The Mythbuntu standalone system
ii  mythbuntu-gdm-theme                        0.3-0ubuntu1                                         mythbuntu gdm greeter theme
ii  mythbuntu-lirc-generator                   0.20-0ubuntu1                                        Mythbuntu Lirc Configuration Generator
ii  mythcontrols                               0.21.0+fixes18207-0ubuntu4~hardy1                    External controls for MythTV
ii  mythgallery                                0.21.0+fixes18207-0ubuntu4~hardy1                    Image gallery/slideshow add-on module for My
ii  mythmusic                                  0.21.0+fixes18207-0ubuntu4~hardy1                    Music add-on module for MythTV
ii  mythstream                                 0.18.1-0ubuntu6                                      MythTV plugin for playing Internet audio and
ii  mythtv                                     0.21.0+fixes18207-0ubuntu4~hardy1                    A personal video recorder application (clien
ii  mythtv-backend                             0.21.0+fixes18207-0ubuntu4~hardy1                    A personal video recorder application (serve
ii  mythtv-backend-master                      0.21.0+fixes18207-0ubuntu4~hardy1                    Metapackage to setup and configure a "Master
ii  mythtv-common                              0.21.0+fixes18207-0ubuntu4~hardy1                    A personal video recorder application (commo
ii  mythtv-database                            0.21.0+fixes18207-0ubuntu4~hardy1                    A personal video recorder application (datab
ii  mythtv-frontend                            0.21.0+fixes18207-0ubuntu4~hardy1                    A personal video recorder application (clien
ii  mythtv-status                              0.7.3-1ubuntu1                                       Show the status of a MythTV backend
ii  mythtv-theme-blootube                      1:0.21.0-0ubuntu1                                    The Blootube MythTV theme
ii  mythtv-theme-blootube-osd                  1:0.21.0-0ubuntu2                                    The Blootube MythTV OSD
ii  mythtv-theme-blootube-wide                 1:0.21.0-0ubuntu1                                    The Blootube MythTV theme (widescreen)
ii  mythtv-theme-blootubelite-wide             1:0.21.0-0ubuntu1                                    The Blootube Lite MythTV theme (widescreen)
ii  mythtv-theme-glass-wide                    0.20071107-0ubuntu1                                  The Glass MythTV theme (widescreen)
ii  mythtv-theme-gray-osd                      0.21.0-0ubuntu2                                      The Gray-OSD MythTV Theme
ii  mythtv-theme-isthmus                       0.21.0-0ubuntu2                                      The Isthmus MythTV Theme
ii  mythtv-theme-iulius                        0.21.0-0ubuntu2                                      The Iulius MythTV Theme
ii  mythtv-theme-iulius-osd                    0.21.0-0ubuntu2                                      The Iulius-OSD MythTV Theme
ii  mythtv-theme-minimalist-wide               0.21.0-0ubuntu2                                      The Minimalist Wide MythTV Theme
ii  mythtv-theme-mythbuntu                     0.20080421                                           default MythTV theme used in Mythbuntu
ii  mythtv-theme-mythcenter                    0.21.0-0ubuntu2                                      The MythCenter MythTV Theme
ii  mythtv-theme-mythcenter-wide               0.21.0-0ubuntu2                                      The MythCenter Wide MythTV Theme
ii  mythtv-theme-neon-wide                     1:0.21.0-0ubuntu1                                    The Neon MythTV theme (widescreen)
ii  mythtv-theme-projectgrayhem                1:0.21.0-0ubuntu1                                    The Project Grayhem MythTV theme
ii  mythtv-theme-projectgrayhem-osd            1:0.21.0-0ubuntu2                                    The Project Grayhem MythTV OSD
ii  mythtv-theme-projectgrayhem-wide           1:0.21.0-0ubuntu1                                    The Project Grayhem MythTV theme (widescreen
ii  mythtv-theme-retro                         0.21.0-0ubuntu2                                      The Retro MythTV Theme
ii  mythtv-theme-retro-osd                     0.21.0-0ubuntu2                                      The Retro-OSD MythTV Theme
ii  mythtv-theme-titivillus                    0.21.0-0ubuntu2                                      The Titivillus MythTV Theme
ii  mythtv-theme-titivillus-osd                0.21.0-0ubuntu2                                      The Titivillus-OSD MythTV Theme
ii  mythtv-themes                              0.21.0-0ubuntu2                                      Additional themes metapackage for MythTV
ii  mythtv-transcode-utils                     0.21.0+fixes18207-0ubuntu4~hardy1                    Utilities used for transcoding MythTV tasks
ii  mythvideo                                  0.21.0+fixes18207-0ubuntu4~hardy1                    A generic video player frontend module for M

---

### Post by ian dobson on 2008-10-17
Hi,

I would go with the udev rules. Maybe something like:-

```
KERNEL=="video[0-9]", SYSFS{name}=="BT878 video (Hauppauge (bt87)", SYMLINK+="BT878"
KERNEL=="video[0-9]", SYSFS{name}=="ivtv[0-1] encoder MPEG", SYMLINK+="PVR150"
```

So your WIN TV will always be symlinked to BT878 and your PVR-150 is always symlinked to PVR150.

Note don't forget to update mythtv to use the new device name.
You might need to manually edit the "capturecard" table to get the "videodevice" to point to the correct symlinked device.

Heres a good source of info on udev :- [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

Regards
Ian Dobson

---

### Post by pjw1965 on 2008-10-19
Thanx Ian

I already tried the udev rules, but didn't realize, that there are actually two new devices: /dev/BT878 and /dev/PVR150

> **ian dobson said:**
> 
Note don't forget to update mythtv to use the new device name.
You might need to manually edit the "capturecard" table to get the "videodevice" to point to the correct symlinked device.


Yes, I also forgot to add the new devices in mythtv-setup replacing /dev/video0 and /dev/video1.
For /dev/vbi1 (which did'nt work either on BT878) I repeatet just /dev/BT878.

My Rules are now in /etc/udev/rules.d/55-custom.rules
> 
KERNEL=="video[0-9]", SYSFS{name}=="BT878*", SYMLINK+="BT878"
KERNEL=="video[0-9]", SYSFS{name}=="ivtv*",  SYMLINK+="PVR150"


---

### Post by linuxvacuum on 2008-11-25
Thanks you so much pjw1965!

At first I tried :
```

KERNEL=="video*", ATTRS{vendor}==""0x8086", ATTRS{device}=="0x244e", ENV{GENERATED}="1", ATTR{name}=="ivtv0 encoder MPG", ENV{GENERATED}="1", SYMLINK+="tunerhauppauge"
KERNEL=="video*", ATTRS{vendor}=="0x8086", ATTRS{device}=="0x244e", ENV{GENERATED}="1", ATTR{name}=="saa7133_0_ video _ASUS TV-FM 71", SYMLINK+="tunerasus"

```

Then I tried for testing purposes:
```

KERNEL=="video*", SUBSYSTEM=="video4linux", ATTRS{modalias}=="pci:v00001131d00007133sv00001043sd00004845bc04sc80i00", ENV{GENERATED}="1", SYMLINK+="tunerasus1"
KERNEL=="video*", SUBSYSTEM=="video4linux", ATTRS{modalias}=="pci:v00008086d0000244Esv00000000sd00000000bc06sc04i00", ENV{GENERATED}="1", SYMLINK+="tunerasus2"
KERNEL=="video*", SUBSYSTEM=="video4linux", ATTRS{modalias}=="pci:v00004444d00000016sv00000070sd000037F1bc04sc00i00", ENV{GENERATED}="1", SYMLINK+="tunerhauppauge1"
KERNEL=="video*", SUBSYSTEM=="video4linux", ATTRS{modalias}=="pci:v00008086d0000244Esv00000000sd00000000bc06sc04i00", ENV{GENERATED}="1", SYMLINK+="tunerhauppauge2"

```

Those didn't work because it linked my devices to /dev/mixer1 and /dev/video24. Yes video24, don't ask me why...



Finally the following works like a charm!
```

KERNEL=="video[0-1]", ATTR{name}=="*encoder MPG*", SYMLINK+="tunerhauppauge"
KERNEL=="video[0-1]", ATTR{name}=="*ASUS TV-FM*", SYMLINK+="tunerasus"

```

I created a file name  56-custom.rules because 55 was occupied by the HP Printer. If anyone cares to explain in more details why my first tries didn't work that would be great.

---

