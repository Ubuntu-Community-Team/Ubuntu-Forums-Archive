---
title: "Cannot Configure Xorg, Matrox"
date: 2013-08-22
forum: Multimedia Software
---

### Post by sawbona on 2013-08-22
Good morning:

I'm an old time MS user, way back from DOS 6.0.
Through the years, I've tried many times to hop on to the Linux wagon but it's been frustrating, finally giving up each time.

I am now trying again, this time with Ububtu 11.10, which I finally managed to get installed after hours of no-gos.
I then applied all the updates to the 11.10 release with the Synaptic package manager. 

The main problem now is my video card and monitors: a 32Mb Matrox Graphics MGA G40/450 (rev 85). with two Samsung SyncMaster 940Ns.

Via system tools --> system settings --> displays, only one monitor is identified as 'unknown', running at 1280*1024.
The output is the same in each one of them and nothing happens when I hit 'detect displays'.

Via system tools --> system settings --> additional drivers I get that there are no proprietary drivers in use in the system.

I have searched all over and seen that this problem has affected many but I have not been able to find a solution to the problem.
One post even suggested that the video card was too old and that a new one was in order, something that I would think goes against the whole idea of Linux as a desktp OS. 

Another more sensible one suggested editing the Xorg.conf file, which I was not able to find anywhere in 10.11. I then found that it is not used anymore but that using one could solve Xorg configuration problems.

So, as sugested, I attempted to generate one with - sudo X :1 -configure - but got this result:

---

```
sudo X :1 -configure

X.Org X Server 1.10.4
Release Date: 2011-08-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
Current Operating System: Linux JHM-2 3.0.0-32-generic #51-Ubuntu SMP Thu Mar 21 15:51:26 UTC 2013 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-32-generic root=UUID=fc3c1478-ad6d-4f5f-9411-43560898962a ro quiet splash vt.handoff=7
Build Date: 11 April 2013  01:34:05PM
xorg-server 2:1.10.4-1ubuntu4.5 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.22.2
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Thu Aug 22 13:12:00 2013
List of video drivers:
        sisusb
        cirrus
        tdfx
        savage
        openchrome
        intel
        neomagic
        r128
        sis
        mga                  ---> EDIT: seems that the drivers 'are' there
        vmware
        vmwlegacy
        trident
        s3
        radeon
        mach64
        ztv
        siliconmotion
        geode
        nouveau
        ati
        qxl
        fbdev
        vesa
(EE) Failed to load module "vmwgfx" (module does not exist, 0)
(EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx
(++) Using config file: "/home/groucho/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Number of created screens does not match number of detected devices.
  Configuration failed.
 ddxSigGiveUp: Closing log

---

When I open the file generated (/home/groucho/xorg.conf.new) I see that it does not have monitor info or video card info.

Seeing that I'm stuck here, I was wondering if you'd spare some of your time to have a look at the output from hwinfo lspci to point me in the right direction.

Here's the output from hwinfo and lspci

************

sudo hwinfo --framebuffer

> hal.1: read hal dataprocess 2654: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.mC7YvNpYJS7
  Hardware Class: framebuffer
  Model: "Matrox G450"
  Vendor: "Matrox"
  Device: "Matrox G450"
  SubVendor: "Matrox Graphics Inc."
  SubDevice: 
  Revision: "00"
  Memory Size: 32 MB
  Memory Range: 0xd0000000-0xd1ffffff (rw)
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0310: 640x480 (+1280), 15 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0313: 800x600 (+1600), 15 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0316: 1024x768 (+2048), 15 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x0319: 1280x1024 (+2560), 15 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

sudo hwinfo --monitor

process 3611: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files

27: None 00.0: 10000 Monitor
  [Created at monitor.95]
  Unique ID: rdCR.kW5q9fL3xa3
  Hardware Class: monitor
  Model: "SAMSUNG SyncMaster"
  Vendor: SAM "SAMSUNG"
  Device: eisa 0x01e1 "SyncMaster"
  Serial ID: "HVFP210788"
  Resolution: 720x400@70Hz
  Resolution: 640x480@60Hz
  Resolution: 640x480@67Hz
  Resolution: 640x480@72Hz
  Resolution: 640x480@75Hz
  Resolution: 800x600@56Hz
  Resolution: 800x600@60Hz
  Resolution: 800x600@72Hz
  Resolution: 800x600@75Hz
  Resolution: 832x624@75Hz
  Resolution: 1024x768@60Hz
  Resolution: 1024x768@70Hz
  Resolution: 1024x768@75Hz
  Resolution: 1280x1024@75Hz
  Resolution: 1280x1024@60Hz
  Resolution: 1280x960@60Hz
  Resolution: 1152x864@75Hz
  Size: 376x301 mm
  Detailed Timings #0:
     Resolution: 1280x1024
     Horizontal: 1280 1328 1440 1688 (+48 +160 +408) +hsync
       Vertical: 1024 1025 1028 1066 (+1 +4 +42) +vsync
    Frequencies: 108.00 MHz, 63.98 kHz, 60.02 Hz
  Driver Info #0:
    Max. Resolution: 1280x1024
    Vert. Sync Range: 56-75 Hz
    Hor. Sync Range: 30-81 kHz
    Bandwidth: 108 MHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown

28: None 00.1: 10000 Monitor
  [Created at monitor.95]
  Unique ID: jyhG.TngO+uMxeX3
  Hardware Class: monitor
  Model: "SAMSUNG SyncMaster"
  Vendor: SAM "SAMSUNG"
  Device: eisa 0x01e1 "SyncMaster"
  Serial ID: "HVFP119365"
  Resolution: 720x400@70Hz
  Resolution: 640x480@60Hz
  Resolution: 640x480@67Hz
  Resolution: 640x480@72Hz
  Resolution: 640x480@75Hz
  Resolution: 800x600@56Hz
  Resolution: 800x600@60Hz
  Resolution: 800x600@72Hz
  Resolution: 800x600@75Hz
  Resolution: 832x624@75Hz
  Resolution: 1024x768@60Hz
  Resolution: 1024x768@70Hz
  Resolution: 1024x768@75Hz
  Resolution: 1280x1024@75Hz
  Resolution: 1280x1024@60Hz
  Resolution: 1280x960@60Hz
  Resolution: 1152x864@75Hz
  Size: 376x301 mm
  Detailed Timings #0:
     Resolution: 1280x1024
     Horizontal: 1280 1328 1440 1688 (+48 +160 +408) +hsync
       Vertical: 1024 1025 1028 1066 (+1 +4 +42) +vsync
    Frequencies: 108.00 MHz, 63.98 kHz, 60.02 Hz
  Driver Info #0:
    Max. Resolution: 1280x1024
    Vert. Sync Range: 56-75 Hz
    Hor. Sync Range: 30-81 kHz
    Bandwidth: 108 MHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown

lspci -vnn | grep -i VGA
01:00.0 VGA compatible controller [0300]: Matrox Graphics, Inc. MGA G400/G450 [102b:0525] (rev 85) (prog-if 00 [VGA controller])
```

************

Thanks in advance,

CIV

Edited 08/31/2013 - Corrected Ubuntu version to 11.10 - line 06

---

### Post by oldos2er on 2013-08-22
Post moved to its own thread.

---

### Post by MAFoElffen on 2013-08-22
Create a generic /etc/X11/xorg.conf file that contains at least the following lines (at a minimum):
```

Section "Device"
    Identifier   "Device0"
    Driver        "mga"
EndSection

```
"mga" is the generic driver name for your GPU. Xorg will see that file and point to that driver. If you need to tweak that for your monitor or resoltions, you can do that either via the screen utility or directly by adding more to the xorg.conf file. (other sections)

If you need more info or help, feel free to PM me again and I'll jump back in. Doing 2 projects//multi-tasking... But more than happy to be of help. A really good distraction!

---

### Post by sawbona on 2013-08-23
Good evening:

Sorry for the delay in answering. Just saw your reply, did not receive the notification mail.
l'll check this out asap and get back to you.

BTW: 
I decided to take the leap and updated tp 12.04 LTS. Rather an ordeal, have to say it. 
But finally managed to get it done.

Now, with 14.02 and via system tools --> system settings --> displays, still only one monitor is identified as 'unknown' and running at 1280*1024 but it is a 'laptop'monitor.

As with 11.10, the output is the same in each one of them and nothing happens when I hit 'detect displays'.

Best part is that I was able to get rid of that obnoxious Unity thing ...   8^D

Once again, thanks a lot for your input.

Best regards,

CIV

---

