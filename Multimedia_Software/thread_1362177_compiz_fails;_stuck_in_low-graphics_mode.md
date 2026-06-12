---
title: "compiz fails; stuck in low-graphics mode"
date: 2009-12-22
forum: Multimedia Software
---

### Post by lasershadow on 2009-12-22
Hi,

So I recently switched to Ubuntu (I'm pretty new with linux) and I tried to install compiz yesterday. I'm running Karmic Koala with a 256 mb nvidia 8400 gt graphics card. There were no problems, but then I was trying to get the animations plugin to work, and I ran compix --replace in the terminal and all hell broke loose. That is, I got the following message:

```
samir@ubuntu:~$ compiz --replace &
[2] 2574
samir@ubuntu:~$ Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA:     Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (640x480) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
samir@ubuntu:~$ /usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
samir@ubuntu:~$ *** glibc detected *** /usr/bin/compiz.real: corrupted double-linked list: 0x00000000018e0e40 ***
======= Backtrace: =========
/lib/libc.so.6[0x7fd3cc2dadd6]
/lib/libc.so.6[0x7fd3cc2dc6f9]
/lib/libc.so.6(cfree+0x6c)[0x7fd3cc2df70c]
/usr/lib/libGL.so.1[0x7fd3ce2d2038]
======= Memory map: ========
00400000-0043c000 r-xp 00000000 07:00 7278                               /usr/bin/compiz.real
0063b000-0063c000 r--p 0003b000 07:00 7278                               /usr/bin/compiz.real
0063c000-0063d000 rw-p 0003c000 07:00 7278                               /usr/bin/compiz.real
00f2c000-02aae000 rw-p 00000000 00:00 0                                  [heap]
7fd3c0000000-7fd3c0021000 rw-p 00000000 00:00 0 
7fd3c0021000-7fd3c4000000 ---p 00000000 00:00 0 
7fd3c542b000-7fd3c5437000 r-xp 00000000 07:00 1046                       /lib/libnss_files-2.10.1.so
7fd3c5437000-7fd3c5636000 ---p 0000c000 07:00 1046                       /lib/libnss_files-2.10.1.so
7fd3c5636000-7fd3c5637000 r--p 0000b000 07:00 1046                       /lib/libnss_files-2.10.1.so
7fd3c5637000-7fd3c5638000 rw-p 0000c000 07:00 1046                       /lib/libnss_files-2.10.1.so
7fd3c5638000-7fd3c5642000 r-xp 00000000 07:00 1056                       /lib/libnss_nis-2.10.1.so
7fd3c5642000-7fd3c5841000 ---p 0000a000 07:00 1056                       /lib/libnss_nis-2.10.1.so
7fd3c5841000-7fd3c5842000 r--p 00009000 07:00 1056                       /lib/libnss_nis-2.10.1.so
7fd3c5842000-7fd3c5843000 rw-p 0000a000 07:00 1056                       /lib/libnss_nis-2.10.1.so
7fd3c5843000-7fd3c5859000 r-xp 00000000 07:00 1040                       /lib/libnsl-2.10.1.so
7fd3c5859000-7fd3c5a59000 ---p 00016000 07:00 1040                       /lib/libnsl-2.10.1.so
7fd3c5a59000-7fd3c5a5a000 r--p 00016000 07:00 1040                       /lib/libnsl-2.10.1.so
7fd3c5a5a000-7fd3c5a5b000 rw-p 00017000 07:00 1040                       /lib/libnsl-2.10.1.so
7fd3c5a5b000-7fd3c5a5d000 rw-p 00000000 00:00 0 
7fd3c5a5d000-7fd3c5a64000 r-xp 00000000 07:00 1042                       /lib/libnss_compat-2.10.1.so
7fd3c5a64000-7fd3c5c64000 ---p 00007000 07:00 1042                       /lib/libnss_compat-2.10.1.so
7fd3c5c64000-7fd3c5c65000 r--p 00007000 07:00 1042                       /lib/libnss_compat-2.10.1.so
7fd3c5c65000-7fd3c5c66000 rw-p 00008000 07:00 1042                       /lib/libnss_compat-2.10.1.so
7fd3c5c66000-7fd3c5c93000 r-xp 00000000 07:00 1072                       /lib/libpcre.so.3.12.1
7fd3c5c93000-7fd3c5e92000 ---p 0002d000 07:00 1072                       /lib/libpcre.so.3.12.1
7fd3c5e92000-7fd3c5e93000 r--p 0002c000 07:00 1072                       /lib/libpcre.so.3.12.1
7fd3c5e93000-7fd3c5e94000 rw-p 0002d000 07:00 1072                       /lib/libpcre.so.3.12.1
7fd3c5e94000-7fd3c5ed8000 r-xp 00000000 07:00 7723                       /usr/lib/libgobject-2.0.so.0.2200.3
7fd3c5ed8000-7fd3c60d8000 ---p 00044000 07:00 7723                       /usr/lib/libgobject-2.0.so.0.2200.3
7fd3c60d8000-7fd3c60d9000 r--p 00044000 07:00 7723                       /usr/lib/libgobject-2.0.so.0.2200.3
7fd3c60d9000-7fd3c60da000 rw-p 00045000 07:00 7723                       /usr/lib/libgobject-2.0.so.0.2200.3
7fd3c60da000-7fd3c60db000 rw-p 00000000 00:00 0 
7fd3c60db000-7fd3c60e2000 r-xp 00000000 07:00 1085                       /lib/librt-2.10.1.so
7fd3c60e2000-7fd3c62e1000 ---p 00007000 07:00 1085                       /lib/librt-2.10.1.so
7fd3c62e1000-7fd3c62e2000 r--p 00006000 07:00 1085                       /lib/librt-2.10.1.so
7fd3c62e2000-7fd3c62e3000 rw-p 00007000 07:00 1085                       /lib/librt-2.10.1.so
7fd3c62e3000-7fd3c6320000 r-xp 00000000 07:00 1003                       /lib/libdbus-1.so.3.4.0
7fd3c6320000-7fd3c6520000 ---p 0003d000 07:00 1003                       /lib/libdbus-1.so.3.4.0
7fd3c6520000-7fd3c6521000 r--p 0003d000 07:00 1003                       /lib/libdbus-1.so.3.4.0
7fd3c6521000-7fd3c6522000 rw-p 0003e000 07:00 1003                       /lib/libdbus-1.so.3.4.0
7fd3c6522000-7fd3c6542000 r-xp 00000000 07:00 5783                       /usr/lib/libdbus-glib-1.so.2.1.0
7fd3c6542000-7fd3c6742000 ---p 00020000 07:00 5783                       /usr/lib/libdbus-glib-1.so.2.1.0
7fd3c6742000-7fd3c6743000 r--p 00020000 07:00 5783                       /usr/lib/libdbus-glib-1.so.2.1.0
7fd3c6743000-7fd3c6744000 rw-p 00021000 07:00 5783                       /usr/lib/libdbus-glib-1.so.2.1.0
7fd3c6744000-7fd3c6748000 r-xp 00000000 07:00 7725                       /usr/lib/libgthread-2.0.so.0.2200.3
7fd3c6748000-7fd3c6947000 ---p 00004000 07:00 7725                       /usr/lib/libgthread-2.0.so.0.2200.3
7fd3c6947000-7fd3c6948000 r--p 00003000 07:00 7725                       /usr/lib/libgthread-2.0.so.0.2200.3
7fd3c6948000-7fd3c6949000 rw-p 00004000 07:00 7725                       /usr/lib/libgthread-2.0.so.0.2200.3
7fd3c6949000-7fd3c69a5000 r-xp 00000000 07:00 5558                       /usr/lib/libORBit-2.so.0.1.0
7fd3c69a5000-7fd3c6ba5000 ---p 0005c000 07:00 5558                       /usr/lib/libORBit-2.so.0.1.0
7fd3c6ba5000-7fd3c6bb4000 r--p 0005c000 07:00 5558                       /usr/lib/libORBit-2.so.0.1.0
7fd3c6bb4000-7fd3c6bb7000 rw-p 0006b000 07:00 5558                       /usr/lib/libORBit-2.so.0.1.0
7fd3c6bb7000-7fd3c6bba000 r-xp 00000000 07:00 7724                       /usr/lib/libgmodule-2.0.so.0.2200.3
7fd3c6bba000-7fd3c6db9000 ---p 00003000 07:00 7724                       /usr/lib/libgmodule-2.0.so.0.2200.3
7fd3c6db9000-7fd3c6dba000 r--p 00002000 07:00 7724                       /usr/lib/libgmodule-2.0.so.0.2200.3
7fd3c6dba000-7fd3c6dbb000 rw-p 00003000 07:00 7724                       /usr/lib/libgmodule-2.0.so.0.2200.3
7fd3c6dbb000-7fd3c6e80000 r-xp 00000000 07:00 7719                       /lib/libglib-2.0.so.0.2200.3
7fd3c6e80000-7fd3c707f000 ---p 000c5000 07:00 7719                       /lib/libglib-2.0.so.0.2200.3
7fd3c707f000-7fd3c7080000 r--p 000c4000 07:00 7719                       /lib/libglib-2.0.so.0.2200.3
7fd3c7080000-7fd3c7081000 rw-p 000c5000 07:00 7719                       /lib/libglib-2.0.so.0.2200.3
7fd3c7081000-7fd3c7082000 rw-p 00000000 00:00 0 
7fd3c7082000-7fd3c70ba000 r-xp 00000000 07:00 5897                       /usr/lib/libgconf-2.so.4.1.5
7fd3c70ba000-7fd3c72ba000 ---p 00038000 07:00 5897                       /usr/lib/libgconf-2.so.4.1.5
7fd3c72ba000-7fd3c72bc000 r--p 00038000 07:00 5897                       /usr/lib/libgconf-2.so.4.1.5Aborted

```Then my screen flashed and the computer froze, so I had to reboot.

Now I'm stuck in low-res land no matter what I do. I've reinstalled and uninstalled compiz and my nvidia drivers. I've rebooted into safe mode and tried to fix broken packages. I don't think my xorg.conf is messed up, but this is what it contains:

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
        Disable "dri2"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
EndSection

```Please help :( My computer isn't pretty any more.

---

