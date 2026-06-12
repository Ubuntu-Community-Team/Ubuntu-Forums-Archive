---
title: "Cannot get DVDs to play"
date: 2012-05-01
forum: Multimedia Software
---

### Post by Germanunkol on 2012-05-01
Edit: This should be marked [ubuntu], not [lubuntu]. Sorry about that. But I can't change it now from what I can tell.


I have an (almost fresh) install of 12.04, 64bit and cannot find the answer to this problem, after lots and lots of google-ing.

I believe to have installed everything needed for DVD playback.
I have added medibuntu to the sources, I have installed libdvdread4, I have installed libdvdcss2 and ubuntu-restricted-extras. I also installed w64codecs and ran
sudo /usr/share/doc/libdvdread4/install-css.sh

Still, I cannot play DVDs. In VLC, I get:
```
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdnav: DVD Title: THE_BANG_BANG_CLUB
libdvdnav: DVD Serial Number: 3f4c7308
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/peter/.dvdnav/THE_BANG_BANG_CLUB.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000c248
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0000c248)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000e611
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000e6be
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x0000e6be)!!
libdvdread: Elapsed time 2
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002c61c3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002d1b7c
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x002d1b7c)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002d9dd4
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x002d9dd4)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x002e195b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x002e97fe
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_1.VOB (0x002e97fe)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x002f409c
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x002f409c)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x002feac8
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_1.VOB (0x002feac8)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0031266d
libdvdread: Elapsed time 0
libdvdread: Found 10 VTS's
libdvdread: Elapsed time 3
libdvdnav: Language 'en' not found, using 'de' instead
libdvdnav: Menu Languages available: de 
libdvdnav: Language 'en' not found, using 'de' instead
libdvdnav: Menu Languages available: de 
libdvdnav: Language 'en' not found, using 'de' instead
libdvdnav: Menu Languages available: de 
libdvdnav: Language 'en' not found, using 'de' instead
libdvdnav: Menu Languages available: de 
[0x7fb0b4000b78] main input error: ES_OUT_RESET_PCR called
[0x7fb0b4000b78] main input error: ES_OUT_RESET_PCR called

```In Totem, I get this:
```

(totem:2763): GLib-GObject-CRITICAL **: Read/writable property 'object' on class 'ZeitgeistDpPlugin' has type 'TotemObject' which is not exactly equal to the type 'GObject' of the property on the interface 'PeasActivatable'

libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/THE_BANG_BANG_CLUB for CSS authentication
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdread: Attempting to use device /dev/sr0 mounted on /media/THE_BANG_BANG_CLUB for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/peter/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000014b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000c248
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x0000c248)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x0000e611
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000e6be
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x0000e6be)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002c61c3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002d1b7c
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x002d1b7c)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002d9dd4
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_05_1.VOB (0x002d9dd4)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x002e195b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x002e97fe
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_07_1.VOB (0x002e97fe)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x002f409c
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_08_1.VOB (0x002f409c)!!
libdvdread: Elapsed time 1
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x002feac8
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_09_1.VOB (0x002feac8)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0031266d
libdvdread: Elapsed time 0
libdvdread: Found 10 VTS's
libdvdread: Elapsed time 3
** Message: Error: DVD konnten nicht gelesen werden. Dies könnte daran liegen, dass die DVD verschlüsselt ist und eine Bibliothek zur DVD-Entschlüsselung nicht installiert ist.
resindvdsrc.c(1143): rsn_dvdsrc_step (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/RsnDvdBin:source/resinDvdSrc:dvdsrc:
Failed to read next DVD block. Error: Error reading NAV packet.

```The German error near the end roughly translates to: "DVD could not be read. This could be because it is encrypted and the library for decrypting is not installed."

Don't know if this will help, but I'm going to post these outputs anyway:
dpgk -s libdvdcss2:
```
Package: libdvdcss2
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 108
Maintainer: Medibuntu Packaging Team <medibuntu-maintainers@lists.launchpad.net>
Architecture: amd64
Source: libdvdcss
Version: 1.2.12-0.0medibuntu1
Replaces: libdvdcss-dev (<= 0.0.3-3), libdvdcss0 (<= 1.0.0-0.0), libdvdcss2-dev (<= 1.2.10-0.0)
Provides: libdvdcss
Depends: libc6 (>= 2.7)
Description: Simple foundation for reading DVDs - runtime libraries
 To allow applications to access some of the more advanced features
 of the DVD format.
Homepage: http://download.videolan.org/
Original-Maintainer: Christian Marillat <marillat@debian.org>

```dpkg -s w64codecs
```

Package: w64codecs
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 608
Maintainer: Medibuntu Packaging Team <admin@lists.medibuntu.org>
Architecture: amd64
Version: 20071007-0medibuntu2
Depends: libc6 (>= 2.3.2), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.1.1)
Suggests: mplayer
Description: Proprietary codec binaries, x86_64 version
 This package contains the "Win32" codec binaries for the x86_64 architectures,
 required for the decompression of video formats that have no open source
 alternative.
 .
 This is in Medibuntu due to its non-free license.
Homepage: http://www.mplayerhq.hu/

```dpkg -s libdvdread4
```
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 195
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: libdvdread
Version: 4.2.0-1ubuntu3
Depends: libc6 (>= 2.4)
Recommends: libdvdnav4
Suggests: libdvdcss2, wget, debhelper, fakeroot, build-essential
Description: library for reading DVDs
 libdvdread provides the functionality that is required to access many DVDs. It
 parses IFO files, reads NAV-blocks, and performs CSS authentication and
 descrambling.
 .
 libdvdread probes for libdvdcss at runtime and if found, will use it to
 decrypt sections of the DVD as necessary. libdvdcss needs to be installed from
 third-party repositories (see README.Debian), it's not included in Debian.
Homepage: http://dvdnav.mplayerhq.hu/
Original-Maintainer: Daniel Baumann <daniel.baumann@progress-technologies.net>

```Only weird thing I notice is that running "sudo apt-get update" takes very long and tries to connect to security.ubuntu.com, and fails at that.

Any help would be appreciated.

---

### Post by carl4926 on 2012-05-02
It's a fact that some DVD's just will not play.
Though even in those cases I have on occasion managed to rip them, strange eh.
Using k9copy

---

### Post by shantiq on 2012-05-03
**[you need]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")**:KS

usually this does it



[LIST]
[*]Install the **libdvdread4** package (**no need to add third party repositories**) via Synaptic or command line:
[/LIST]

> sudo apt-get install libdvdread4
[LIST]
[*]Then open a terminal window and execute:
[/LIST]

> sudo /usr/share/doc/libdvdread4/install-css.shRebooting may be necessary.



this is additional**[ info ]("https://help.ubuntu.com/community/RestrictedFormats/RippingDVDs?highlight=%28%28RestrictedFormats%7CPlayingDVDs%29%29")**on ripping

---

### Post by MST3Kakalina on 2012-05-18
Maybe the OP edited his post after this, but he ran install-css.sh as necessary.

Would like to know some other solutions since I'm in the same boat as the OP.

---

### Post by wilee-nilee on 2012-05-18
> **MST3Kakalina said:**
> Maybe the OP edited his post after this, but he ran install-css.sh as necessary.

Would like to know some other solutions since I'm in the same boat as the OP.

You will want to start a thread, but install this.

```
sudo apt-get install ubuntu-restricted-extras
```These are codecs needed in general, msfonts, and flash.

run this to install medibuntu.

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```Then run

```
sudo apt-get update
```Then

```
sudo apt-get install libdvdcss2 w32codecs
```The w32codecs is for 32 bit if you have a 64 bit set up, sub the 32 with 64.

I would also install vlc it has codecs that will cover most everything.

```
sudo apt-get install vlc
```Here is the medibuntu page.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

So you give no indication on what is actually installed so I have to assume here.

---

### Post by Face-Ache on 2012-07-03
> **shantiq said:**
> 

[LIST]
[*]Install the **libdvdread4** package (**no need to add third party repositories**) via Synaptic or command line:
[/LIST]
```
sudo apt-get install libdvdread4
``` 
[LIST]
[*]Then open a terminal window and execute:
[/LIST]


This totally worked for me - thanks  :)

---

### Post by CiudadanoJ on 2012-11-30
Thanks shantiq!!! you fixed my problem

---

