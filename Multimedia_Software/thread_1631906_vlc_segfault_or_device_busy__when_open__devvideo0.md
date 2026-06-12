---
title: "vlc segfault or device busy??  when open  /dev/video0"
date: 2010-11-27
forum: Multimedia Software
---

### Post by sdowney717 on 2010-11-27
I used to be able to open my video capture card and for some reason now, it wont work.
```
scott@scott-desktop:~$ vlc
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x9990914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb74590d4, 0xb7459048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1291784200)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:24293): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
/usr/share/themes/aquadreams/gtk-2.0/gtkrc:85: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/aquadreams/gtk-2.0/gtkrc:89: Murrine configuration option "gradients" is no longer supported and will be ignored.
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()
Segmentation fault
scott@scott-desktop:~$ vlc

```

also here
```
scott@scott-desktop:~$ vlc /dev/video0
VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x83ed914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb65fe0d4, 0xb65fe048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1290876274)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:24474): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
/usr/share/themes/aquadreams/gtk-2.0/gtkrc:85: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/aquadreams/gtk-2.0/gtkrc:89: Murrine configuration option "gradients" is no longer supported and will be ignored.
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
libdvdnav: Using dvdnav version 0.2.1cvs from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: Can't seek to block 32
libdvdnav: Unable to find map file '/home/scott/.dvdnav/.map'
libdvdread: UDFFindFile(/VIDEO_TS/VIDEO_TS.IFO)
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdread: UDFFindFile(/VIDEO_TS/VIDEO_TS.BUP)
libdvdread: Can't seek to block 256
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[0x87110bc] main access error: Read error: Device or resource busy
[0x87110bc] filesystem access error: failed to read (Device or resource busy)
[0x871935c] main stream error: cannot pre fill buffer
Warning: call to rand()
Warning: call to rand()
scott@scott-desktop:~$ 

```

here is the pci card.
```
05:01.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
05:03.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
scott@scott-desktop:~$ 

```

> scott@scott-desktop:~$ ls -l /dev/video*
crw-rw----+ 1 root video 81, 0 2010-11-19 14:47 /dev/video0
crw-rw----+ 1 root video 81, 3 2010-11-19 14:47 /dev/video24
crw-rw----+ 1 root video 81, 1 2010-11-19 14:47 /dev/video32
scott@scott-desktop:~$ 


---

### Post by sdowney717 on 2010-11-27
[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/438211](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/438211)

this was a bug that was fixed and now when I try it much later with even mplayer I have a problem. 

```
scott@scott-desktop:~$ mplayer dev/video0
mplayer: error while loading shared libraries: libmpcdec.so.3: cannot open shared object file: No such file or directory
scott@scott-desktop:~$ 


```

---

### Post by sdowney717 on 2010-11-27
solved it by rebooting and reinstalling video driver.
It was saying it needed to restart after some updates went thru.
restart dumped me at command prompt, so I knew I had to reinstall the nvidia driver.

---

