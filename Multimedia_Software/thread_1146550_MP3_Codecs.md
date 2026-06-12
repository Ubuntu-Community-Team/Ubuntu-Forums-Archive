---
title: "MP3 Codecs"
date: 2009-05-02
forum: Multimedia Software
---

### Post by GreenBowlPacker_3 on 2009-05-02
I don't always have a high speed connection, and I can't use dial up on Ubuntu, is there any way to download the codecs needed to play MP3's in Windows and install them later?  If so where can I find them?

---

### Post by balloooza on 2009-05-02
The problem here is not that you can't get the codecs, it is that you can't dial up in ubuntu! (What I mean is you should have titeled the thread "Modem in Ubuntu")

i have the feeing it might be esier (and more benificial) to install the modem driver, rather than chasing around dependencys for the mp3 codecs.

using dial up in ubuntu will also expand what you can do with it, and give you the ability to use free software to do everything, even the web.

Would you like to try to install the modem, or continue with this thread (I recomend the modem)

---

### Post by GreenBowlPacker_3 on 2009-05-02
Installing the modem would be nice too, but I use AOL for dial up and I'm not sure how that will work with Ubuntu either.

---

### Post by balloooza on 2009-05-02
Let us try the modem first, if we have success installing the modem, then we can go on, if the modem will not work, then we will procede installing the codecs from the windows.

can you anwser these questions

Laptop / Desktop


Modem, is is In your computer

Wiat do you get when you type
```
sudo lspci
```
into a terminal (CONTROLL - C will not copy, it is CONTROL - SHIFT -C, and past is CONTROL - SHIFT - V, these shortcuts only apply to the terminal.)
And to clarify these steps need to be done in ubuntu, so you might need to switch to annother computer to continue on the forum,
Subscribe to this thread, then log on somwhere else. If this is your only computer, anwser the questions and tell me that.

---

### Post by golusweet on 2009-05-02
[http://archive.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/ubuntu-restricted-extras_31_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/ubuntu-restricted-extras_31_i386.deb)

Download the deb package, and Install it.

---

### Post by balloooza on 2009-05-02
I am afraid that solution will not work golusweet, golusweetubuntu-resticted-extera is a meta package, meaning that it just containes instructions for apt (or synaptic) to install the codecs witch all lie in different packages. For instance, when I select to install this packege, ubuntu requests to install all these other packages, so ubuntu resrticted exteras, will not work
```
The following NEW packages will be installed:
  cabextract firefox firefox-3.0 flashplugin-nonfree gstreamer0.10-ffmpeg
  gstreamer0.10-pitfdll gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly
  gstreamer0.10-plugins-ugly-multiverse java-common liba52-0.7.4 libasound2
  libavc1394-0 libavcodec1d libavformat1d libavutil1d libcdaudio1
  libdbus-glib-1-2 libdc1394-13 libdirectfb-1.0-0 libdv4 libdvdread3
  libexempi3 libfaac0 libfaad0 libflac8 libfontenc1 libfreebob0 libgmyth0
  libgsm1 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libhunspell-1.1-0
  libid3tag0 libiec61883-0 libiptcdata0 libjack0 liblame0 libmad0
  libmjpegtools0c2a libmms0 libmpcdec3 libmpeg2-4 libmusicbrainz4c2a libneon27
  libnspr4-0d libnss3-1d libogg0 liboil0.3 libopenspc0 libpostproc1d
  libquicktime1 libraw1394-8 libsidplay1 libsndfile1 libsoundtouch1c2
  libsoup2.4-1 libstartup-notification0 libtheora0 libvorbis0a libvorbisenc2
  libvorbisfile3 libwildmidi0 libx264-57 libxfont1 libxp6 libxtst6
  libxvidcore4 msttcorefonts sun-java6-bin sun-java6-jre sun-java6-plugin
  ubuntu-restricted-extras unrar xfonts-encodings xfonts-utils xulrunner-1.9
0 upgraded, 78 newly installed, 0 to remove and 2 not upgraded.
Need to get 54.3MB of archives.
After this operation, 157MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```

---

### Post by GreenBowlPacker_3 on 2009-05-02
Ok,

It's a laptop:  Dell Inspiron 1501
The modem is internal, it's a Conexant HDA D110 MDC V.92 Modem

and when I typed what you told me to I got:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)

I only have access to one computer at the moment, but I'm working on getting a second up and running Ubuntu.

---

### Post by balloooza on 2009-05-02
@GreenBowlPacker_3 installing the modem will not work either, after looking around, the best word anyone had to describe aol as is crap, so seeing that we will not get anywhere with that, forget what I have said, and post so I can make sure you are still here, at that time, i will build all the packages neccecary into a compressed file, and let you download it and put it on your hard drive. This process will take ~15 minuts.

---

### Post by GreenBowlPacker_3 on 2009-05-02
I'll still be here in 15 mins.

---

### Post by mc4man on 2009-05-02
**IF you just want mp3 playback on gstreamer players** (like rhythmbox) then this one package will suffice and you should by default have all the dependencies  (not 100% sure on liboil and libxml2, but they themselves have no deps you won't have

[http://packages.ubuntu.com/jaunty/gstreamer0.10-fluendo-mp3](http://packages.ubuntu.com/jaunty/gstreamer0.10-fluendo-mp3)


Edit: otherwise you need the bad and/or ugly gstreamer plugins and deps (I think mp3 is the ugly, not a gstreamer user per se

---

### Post by balloooza on 2009-05-02
Sorry for the wait 
(everything allways takes longer :) )
IN WINDOWS
download
[http://dl.getdropbox.com/u/644494/packs.tar.gz](http://dl.getdropbox.com/u/644494/packs.tar.gz)
then put it on somthing you can get in ubuntu.
ON UBUNTU
copy the packs.tar.gz onto your desktop, this part is inportant, it will only work on the desktop.
Then RIGHT click the packs.tar.gz, and click extract here.
Then, open a terminal (Apps > ACCESSORYS > TERMINAL)
and do this command
```
sh ./Desktop/packs/wooh
```
and that is it!!!!!!!
I am going to eat dinner now, tell me how it went!!!

mark

---

### Post by GreenBowlPacker_3 on 2009-05-02
I did exactly what you said and this is what I got.
```
sh: can't open ./desktop/packs/wooh
```

---

### Post by balloooza on 2009-05-02
oh the desktop has a capitol D as in (David instead of david)
```
sh ./Desktop/packs/wooh
```

and if I goofed up that one too, try the old command, just changing the "d" to "D"

---

### Post by GreenBowlPacker_3 on 2009-05-03
I tried it again like you said, this time I got a bunch of code but I still can't play MP3's.  Here's what I got.
```
Selecting previously deselected package cabextract.
(Reading database ... 102003 files and directories currently installed.)
Unpacking cabextract (from cabextract_1.2-3_i386.deb) ...
Selecting previously deselected package flashplugin-installer.
Unpacking flashplugin-installer (from flashplugin-installer_10.0.22.87ubuntu2_i386.deb) ...
Selecting previously deselected package flashplugin-nonfree.
Unpacking flashplugin-nonfree (from flashplugin-nonfree_10.0.22.87ubuntu2_i386.deb) ...
Selecting previously deselected package gstreamer0.10-ffmpeg.
Unpacking gstreamer0.10-ffmpeg (from gstreamer0.10-ffmpeg_0.10.6.2-1ubuntu2_i386.deb) ...
Selecting previously deselected package gstreamer0.10-pitfdll.
Unpacking gstreamer0.10-pitfdll (from gstreamer0.10-pitfdll_0.9.1.1+cvs20080215-1ubuntu1_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-bad.
Unpacking gstreamer0.10-plugins-bad (from gstreamer0.10-plugins-bad_0.10.11-2ubuntu1_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-bad-multiverse.
Unpacking gstreamer0.10-plugins-bad-multiverse (from gstreamer0.10-plugins-bad-multiverse_0.10.11-0ubuntu1_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-ugly.
Unpacking gstreamer0.10-plugins-ugly (from gstreamer0.10-plugins-ugly_0.10.10.2-1build1_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-ugly-multiverse.
Unpacking gstreamer0.10-plugins-ugly-multiverse (from gstreamer0.10-plugins-ugly-multiverse_0.10.7-2_i386.deb) ...
Selecting previously deselected package libass1.
Unpacking libass1 (from libass1_0.9.5-2_i386.deb) ...
Selecting previously deselected package libavcodec-unstripped-52.
Unpacking libavcodec-unstripped-52 (from libavcodec-unstripped-52_3%3a0.svn20090303-1ubuntu2+unstripped1_i386.deb) ...
Selecting previously deselected package libavutil-unstripped-49.
Unpacking libavutil-unstripped-49 (from libavutil-unstripped-49_3%3a0.svn20090303-1ubuntu2+unstripped1_i386.deb) ...
Selecting previously deselected package libcdaudio1.
Unpacking libcdaudio1 (from libcdaudio1_0.99.12p2-7_i386.deb) ...
Selecting previously deselected package libdca0.
Unpacking libdca0 (from libdca0_0.0.5-0.1_i386.deb) ...
Selecting previously deselected package libdvdnav4.
Unpacking libdvdnav4 (from libdvdnav4_4.1.3-3_i386.deb) ...
Selecting previously deselected package libdvdread4.
Unpacking libdvdread4 (from libdvdread4_4.1.3-4ubuntu2_i386.deb) ...
Selecting previously deselected package libenca0.
Unpacking libenca0 (from libenca0_1.9-6_i386.deb) ...
Selecting previously deselected package libfaac0.
Unpacking libfaac0 (from libfaac0_1.26-0.1ubuntu2_i386.deb) ...
Selecting previously deselected package libgmyth0.
Unpacking libgmyth0 (from libgmyth0_1%3a0.7.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libiptcdata0.
Unpacking libiptcdata0 (from libiptcdata0_1.0.2+libtool01-2ubuntu1_i386.deb) ...
Selecting previously deselected package libmjpegtools-1.9.
Unpacking libmjpegtools-1.9 (from libmjpegtools-1.9_1%3a1.9.0-0.0_i386.deb) ...
Selecting previously deselected package libmodplug0c2.
Unpacking libmodplug0c2 (from libmodplug0c2_1%3a0.8.4-3ubuntu1_i386.deb) ...
Selecting previously deselected package libmp3lame0.
Unpacking libmp3lame0 (from libmp3lame0_3.98-0.0_i386.deb) ...
Selecting previously deselected package libmpeg2-4.
Unpacking libmpeg2-4 (from libmpeg2-4_0.4.1-3_i386.deb) ...
Selecting previously deselected package libofa0.
Unpacking libofa0 (from libofa0_0.9.3-3_i386.deb) ...
Selecting previously deselected package libopenspc0.
Unpacking libopenspc0 (from libopenspc0_0.3.99a-2_i386.deb) ...
Selecting previously deselected package libsidplay1.
Unpacking libsidplay1 (from libsidplay1_1.36.59-5_i386.deb) ...
Selecting previously deselected package libwildmidi0.
Unpacking libwildmidi0 (from libwildmidi0_0.2.2-2_i386.deb) ...
Selecting previously deselected package libx264-65.
Unpacking libx264-65 (from libx264-65_1%3a0.svn20081230-0.0ubuntu1_i386.deb) ...
Selecting previously deselected package libxvidcore4.
Unpacking libxvidcore4 (from libxvidcore4_2%3a1.1.2-0.1ubuntu3_i386.deb) ...
Selecting previously deselected package ttf-liberation.
Unpacking ttf-liberation (from ttf-liberation_1.04.93-1_all.deb) ...
Selecting previously deselected package ttf-mscorefonts-installer.
Unpacking ttf-mscorefonts-installer (from ttf-mscorefonts-installer_2.6_all.deb) ...
Selecting previously deselected package ubuntu-restricted-extras.
Unpacking ubuntu-restricted-extras (from ubuntu-restricted-extras_31_i386.deb) ...
Selecting previously deselected package unrar.
Unpacking unrar (from unrar_1%3a3.8.5-1_i386.deb) ...
Setting up cabextract (1.2-3) ...
Setting up flashplugin-installer (10.0.22.87ubuntu2) ...
Downloading...
--2009-05-03 02:12:00--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.22.87.orig.tar.gz
Resolving archive.canonical.com... failed: Name or service not known.
wget: unable to resolve host address `archive.canonical.com'
download failed
The Flash plugin is NOT installed.

Setting up flashplugin-nonfree (10.0.22.87ubuntu2) ...
Setting up gstreamer0.10-pitfdll (0.9.1.1+cvs20080215-1ubuntu1) ...
Setting up libavutil-unstripped-49 (3:0.svn20090303-1ubuntu2+unstripped1) ...

Setting up libcdaudio1 (0.99.12p2-7) ...

Setting up libdca0 (0.0.5-0.1) ...

Setting up libdvdread4 (4.1.3-4ubuntu2) ...

Setting up libenca0 (1.9-6) ...

Setting up libfaac0 (1.26-0.1ubuntu2) ...

Setting up libiptcdata0 (1.0.2+libtool01-2ubuntu1) ...

Setting up libmodplug0c2 (1:0.8.4-3ubuntu1) ...

Setting up libmp3lame0 (3.98-0.0) ...

Setting up libmpeg2-4 (0.4.1-3) ...

Setting up libopenspc0 (0.3.99a-2) ...

Setting up libsidplay1 (1.36.59-5) ...

Setting up libwildmidi0 (0.2.2-2) ...

Configuration file `/etc/wildmidi/wildmidi.cfg', does not exist on system.
Installing new config file as you request.

Setting up libx264-65 (1:0.svn20081230-0.0ubuntu1) ...

Setting up libxvidcore4 (2:1.1.2-0.1ubuntu3) ...

Setting up ttf-liberation (1.04.93-1) ...

Configuration file `/etc/defoma/hints/ttf-liberation.hints', does not exist on system.
Installing new config file as you request.
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-liberation
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.

Setting up ubuntu-restricted-extras (31) ...
Setting up unrar (1:3.8.5-1) ...

Setting up gstreamer0.10-plugins-ugly-multiverse (0.10.7-2) ...
Setting up libass1 (0.9.5-2) ...

Setting up libdvdnav4 (4.1.3-3) ...

Processing triggers for man-db ...
Setting up ttf-mscorefonts-installer (2.6) ...

Configuration file `/etc/defoma/hints/ttf-mscorefonts-installer.hints', does not exist on system.
Installing new config file as you request.

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2009-05-03 02:12:22--  http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving surfnet.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `surfnet.dl.sourceforge.net'
--2009-05-03 02:12:22--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2009-05-03 02:12:22--  http://dfn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving dfn.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `dfn.dl.sourceforge.net'
--2009-05-03 02:12:22--  http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving heanet.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `heanet.dl.sourceforge.net'
--2009-05-03 02:12:22--  http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving jaist.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `jaist.dl.sourceforge.net'
--2009-05-03 02:12:22--  http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving nchc.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `nchc.dl.sourceforge.net'
--2009-05-03 02:12:22--  http://ufpr.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving ufpr.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `ufpr.dl.sourceforge.net'
--2009-05-03 02:12:22--  http://internode.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internode.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `internode.dl.sourceforge.net'
--2009-05-03 02:12:22--  http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving mesh.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `mesh.dl.sourceforge.net'
--2009-05-03 02:12:22--  http://voxel.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving voxel.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `voxel.dl.sourceforge.net'
--2009-05-03 02:12:22--  http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving kent.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `kent.dl.sourceforge.net'
--2009-05-03 02:12:22--  http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving internap.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `internap.dl.sourceforge.net'
--2009-05-03 02:12:22--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
Resolving switch.dl.sourceforge.net... failed: Name or service not known.
wget: unable to resolve host address `switch.dl.sourceforge.net'
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing ttf-mscorefonts-installer (--install):
 subprocess post-installation script returned error exit status 1
dpkg: libgmyth0: dependency problems, but configuring anyway as you request:
 libgmyth0 depends on libmysqlclient15off (>= 5.0.27-1); however:
  Package libmysqlclient15off is not installed.
Setting up libgmyth0 (1:0.7.1-1ubuntu1) ...

dpkg: libmjpegtools-1.9: dependency problems, but configuring anyway as you request:
 libmjpegtools-1.9 depends on libquicktime1 (>= 2:1.1.0+debian); however:
  Package libquicktime1 is not installed.
Setting up libmjpegtools-1.9 (1:1.9.0-0.0) ...

dpkg: libofa0: dependency problems, but configuring anyway as you request:
 libofa0 depends on libfftw3-3; however:
  Package libfftw3-3 is not installed.
Setting up libofa0 (0.9.3-3) ...

dpkg: gstreamer0.10-ffmpeg: dependency problems, but configuring anyway as you request:
 gstreamer0.10-ffmpeg depends on libavcodec52 (>= 3:0.svn20090303-1) | libavcodec-unstripped-52 (>= 3:0.svn20090303-1); however:
  Package libavcodec52 is not installed.
 gstreamer0.10-ffmpeg depends on libavformat52 (>= 3:0.svn20090303-1) | libavformat-unstripped-52 (>= 3:0.svn20090303-1); however:
  Package libavformat52 is not installed.
  Package libavformat-unstripped-52 is not installed.
 gstreamer0.10-ffmpeg depends on libpostproc51 (>= 3:0.svn20090303-1) | libpostproc-unstripped-51 (>= 3:0.svn20090303-1); however:
  Package libpostproc51 is not installed.
  Package libpostproc-unstripped-51 is not installed.
 gstreamer0.10-ffmpeg depends on libswscale0 (>= 3:0.svn20090303-1) | libswscale-unstripped-0 (>= 3:0.svn20090303-1); however:
  Package libswscale0 is not installed.
  Package libswscale-unstripped-0 is not installed.
Setting up gstreamer0.10-ffmpeg (0.10.6.2-1ubuntu2) ...
dpkg: gstreamer0.10-plugins-bad: dependency problems, but configuring anyway as you request:
 gstreamer0.10-plugins-bad depends on libcelt0 (>= 0.5.1); however:
  Package libcelt0 is not installed.
 gstreamer0.10-plugins-bad depends on libdc1394-22; however:
  Package libdc1394-22 is not installed.
 gstreamer0.10-plugins-bad depends on libfaad0 (>= 2.6.1); however:
  Package libfaad0 is not installed.
 gstreamer0.10-plugins-bad depends on libjack0 (>= 0.116.1); however:
  Package libjack0 is not installed.
 gstreamer0.10-plugins-bad depends on liblrdf0; however:
  Package liblrdf0 is not installed.
 gstreamer0.10-plugins-bad depends on libmms0 (>= 0.3-4); however:
  Package libmms0 is not installed.
 gstreamer0.10-plugins-bad depends on libmpcdec3; however:
  Package libmpcdec3 is not installed.
 gstreamer0.10-plugins-bad depends on libneon27-gnutls (>= 0.28.2); however:
  Package libneon27-gnutls is not installed.
 gstreamer0.10-plugins-bad depends on libsoundtouch1c2 (>= 1.3.1); however:
  Package libsoundtouch1c2 is not installed.
Setting up gstreamer0.10-plugins-bad (0.10.11-2ubuntu1) ...
Setting up gstreamer0.10-plugins-bad-multiverse (0.10.11-0ubuntu1) ...
dpkg: gstreamer0.10-plugins-ugly: dependency problems, but configuring anyway as you request:
 gstreamer0.10-plugins-ugly depends on liba52-0.7.4; however:
  Package liba52-0.7.4 is not installed.
 gstreamer0.10-plugins-ugly depends on libid3tag0 (>= 0.15.1b); however:
  Package libid3tag0 is not installed.
 gstreamer0.10-plugins-ugly depends on libmad0 (>= 0.15.1b-3); however:
  Package libmad0 is not installed.
 gstreamer0.10-plugins-ugly depends on libtwolame0; however:
  Package libtwolame0 is not installed.
Setting up gstreamer0.10-plugins-ugly (0.10.10.2-1build1) ...
dpkg: libavcodec-unstripped-52: dependency problems, but configuring anyway as you request:
 libavcodec-unstripped-52 depends on libfaad0 (>= 2.6.1); however:
  Package libfaad0 is not installed.
Setting up libavcodec-unstripped-52 (3:0.svn20090303-1ubuntu2+unstripped1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ttf-mscorefonts-installer


```

---

### Post by mc4man on 2009-05-03
> but I still can't play MP3's

If your going to force the install of libraries and plug-ins without all of their dependencies then obviously things may not work correctly.

If you wished to install the gstreamer plug-in's offline it would be far better to assemble all the plug-ins and dep's needed for those plug-in's themselves. (and not include ubuntu-restricted-extras 

> gstreamer0.10-plugins-ugly depends on libmad0 (>= 0.15.1b-3); however:
  Package libmad0 is not installed.


Probably why no mp3 playback

Overall what you did is a poor idea imo

---

### Post by GreenBowlPacker_3 on 2009-05-03
So what do I need to do?

---

### Post by mc4man on 2009-05-03
> So what do I need to do? 

Well you could try to fill in what's missing.

If it was me I'd remove all the forced packages and do this properly

For the 6 gstreamer plugins marked in red here are all the dep's

ubuntu@ubuntu:~/Desktop/archives$ ls *.deb
> freepats_20060219-1_all.deb
[COLOR="Red"]gstreamer0.10-ffmpeg_0.10.6.2-1ubuntu2_i386.deb
gstreamer0.10-pitfdll_0.9.1.1+cvs20080215-1ubuntu1_i386.deb
gstreamer0.10-plugins-bad_0.10.11-2ubuntu1_i386.deb
gstreamer0.10-plugins-bad-multiverse_0.10.11-0ubuntu1_i386.deb
gstreamer0.10-plugins-ugly_0.10.10.2-1build1_i386.deb
gstreamer0.10-plugins-ugly-multiverse_0.10.7-2_i386.deb[/COLOR]
liba52-0.7.4_0.7.4-11ubuntu1_i386.deb
libass1_0.9.5-2_i386.deb
[COLOR="Blue"]libavcodec52_3%3a0.svn20090303-1ubuntu6_i386.deb
libavformat52_3%3a0.svn20090303-1ubuntu6_i386.deb
libavutil49_3%3a0.svn20090303-1ubuntu6_i386.deb[/COLOR]
libcdaudio1_0.99.12p2-7_i386.deb
libcelt0_0.5.1-0ubuntu1_i386.deb
libdc1394-22_2.0.2-1_i386.deb
libdca0_0.0.5-0.1_i386.deb
libdvdnav4_4.1.3-3_i386.deb
libdvdread4_4.1.3-4ubuntu2_i386.deb
libenca0_1.9-6_i386.deb
libfaac0_1.26-0.1ubuntu2_i386.deb
libfaad0_2.6.1-3.1_i386.deb
libffado0_2.0~rc1-0ubuntu2_i386.deb
libfftw3-3_3.1.2-3.1ubuntu1_i386.deb
libfreebob0_1.0.11-0ubuntu1_i386.deb
libgmyth0_1%3a0.7.1-1ubuntu1_i386.deb
libid3tag0_0.15.1b-10_i386.deb
libiptcdata0_1.0.2+libtool01-2ubuntu1_i386.deb
libjack0_0.116.1-3ubuntu3_i386.deb
liblrdf0_0.4.0-1.1_i386.deb
libmad0_0.15.1b-4_i386.deb
libmjpegtools-1.9_1%3a1.9.0-0.0_i386.deb
libmms0_0.4-2_i386.deb
libmodplug0c2_1%3a0.8.4-3ubuntu1_i386.deb
libmp3lame0_3.98-0.0_i386.deb
libmpcdec3_1.2.2-1build1_i386.deb
libmpeg2-4_0.4.1-3_i386.deb
libmysqlclient15off_5.1.30really5.0.75-0ubuntu10_i386.deb
libneon27-gnutls_0.28.2-6.1_i386.deb
libofa0_0.9.3-3_i386.deb
libopenspc0_0.3.99a-2_i386.deb
[COLOR="Blue"]libpostproc51_3%3a0.svn20090303-1ubuntu6_i386.deb[/COLOR]
libquicktime1_2%3a1.1.0+debian-1build1_i386.deb
libraptor1_1.4.18-2_i386.deb
libsidplay1_1.36.59-5_i386.deb
libsoundtouch1c2_1.3.1-2_i386.deb
[COLOR="Blue"]libswscale0_3%3a0.svn20090303-1ubuntu6_i386.deb[/COLOR]
libtwolame0_0.3.12-1_i386.deb
libwildmidi0_0.2.2-2_i386.deb
libx264-65_1%3a0.svn20081230-0.0ubuntu1_i386.deb
libxml++2.6-2_2.24.0-1ubuntu1_i386.deb
libxvidcore4_2%3a1.1.2-0.1ubuntu3_i386.deb
mysql-common_5.1.30really5.0.75-0ubuntu10_all.deb
raptor-utils_1.4.18-2_i386.deb

I'd go into synaptic, search gstreamer and remove all the red packages
Then search ffmpeg and remove the blue packages

If you wish I have the complete package set for a jaunty i386 install, can upload and you would simply dl, tranfer to your offline and install with a dpkg -i *.deb command

Or there are some apps that can make the package sets for you (forget the names, someone will know) or you can use a jaunty live cd to do yourself

Tested on a jaunty live cd install with no Internet connection
> 
buntu@ubuntu:~$ cd ~/Desktop/archives
ubuntu@ubuntu:~/Desktop/archives$ sudo dpkg -i *.deb
Selecting previously deselected package freepats.
(Reading database ... 105940 files and directories currently installed.)
Unpacking freepats (from freepats_20060219-1_all.deb) ...
Selecting previously deselected package gstreamer0.10-ffmpeg.
Unpacking gstreamer0.10-ffmpeg (from gstreamer0.10-ffmpeg_0.10.6.2-1ubuntu2_i386.deb) ...
Selecting previously deselected package gstreamer0.10-pitfdll.
Unpacking gstreamer0.10-pitfdll (from gstreamer0.10-pitfdll_0.9.1.1+cvs20080215-1ubuntu1_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-bad.
Unpacking gstreamer0.10-plugins-bad (from gstreamer0.10-plugins-bad_0.10.11-2ubuntu1_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-bad-multiverse.
Unpacking gstreamer0.10-plugins-bad-multiverse (from gstreamer0.10-plugins-bad-multiverse_0.10.11-0ubuntu1_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-ugly.
Unpacking gstreamer0.10-plugins-ugly (from gstreamer0.10-plugins-ugly_0.10.10.2-1build1_i386.deb) ...
Selecting previously deselected package gstreamer0.10-plugins-ugly-multiverse.
Unpacking gstreamer0.10-plugins-ugly-multiverse (from gstreamer0.10-plugins-ugly-multiverse_0.10.7-2_i386.deb) ...
Selecting previously deselected package liba52-0.7.4.
Unpacking liba52-0.7.4 (from liba52-0.7.4_0.7.4-11ubuntu1_i386.deb) ...
Selecting previously deselected package libass1.
Unpacking libass1 (from libass1_0.9.5-2_i386.deb) ...
Selecting previously deselected package libavcodec52.
Unpacking libavcodec52 (from libavcodec52_3%3a0.svn20090303-1ubuntu6_i386.deb) ...
Selecting previously deselected package libavformat52.
Unpacking libavformat52 (from libavformat52_3%3a0.svn20090303-1ubuntu6_i386.deb) ...
Selecting previously deselected package libavutil49.
Unpacking libavutil49 (from libavutil49_3%3a0.svn20090303-1ubuntu6_i386.deb) ...
Selecting previously deselected package libcdaudio1.
Unpacking libcdaudio1 (from libcdaudio1_0.99.12p2-7_i386.deb) ...
Selecting previously deselected package libcelt0.
Unpacking libcelt0 (from libcelt0_0.5.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package libdc1394-22.
Unpacking libdc1394-22 (from libdc1394-22_2.0.2-1_i386.deb) ...
Selecting previously deselected package libdca0.
Unpacking libdca0 (from libdca0_0.0.5-0.1_i386.deb) ...
Selecting previously deselected package libdvdnav4.
Unpacking libdvdnav4 (from libdvdnav4_4.1.3-3_i386.deb) ...
Selecting previously deselected package libdvdread4.
Unpacking libdvdread4 (from libdvdread4_4.1.3-4ubuntu2_i386.deb) ...
Selecting previously deselected package libenca0.
Unpacking libenca0 (from libenca0_1.9-6_i386.deb) ...
Selecting previously deselected package libfaac0.
Unpacking libfaac0 (from libfaac0_1.26-0.1ubuntu2_i386.deb) ...
Selecting previously deselected package libfaad0.
Unpacking libfaad0 (from libfaad0_2.6.1-3.1_i386.deb) ...
Selecting previously deselected package libffado0.
Unpacking libffado0 (from libffado0_2.0~rc1-0ubuntu2_i386.deb) ...
Selecting previously deselected package libfftw3-3.
Unpacking libfftw3-3 (from libfftw3-3_3.1.2-3.1ubuntu1_i386.deb) ...
Selecting previously deselected package libfreebob0.
Unpacking libfreebob0 (from libfreebob0_1.0.11-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgmyth0.
Unpacking libgmyth0 (from libgmyth0_1%3a0.7.1-1ubuntu1_i386.deb) ...
Selecting previously deselected package libid3tag0.
Unpacking libid3tag0 (from libid3tag0_0.15.1b-10_i386.deb) ...
Selecting previously deselected package libiptcdata0.
Unpacking libiptcdata0 (from libiptcdata0_1.0.2+libtool01-2ubuntu1_i386.deb) ...
Selecting previously deselected package libjack0.
Unpacking libjack0 (from libjack0_0.116.1-3ubuntu3_i386.deb) ...
Selecting previously deselected package liblrdf0.
Unpacking liblrdf0 (from liblrdf0_0.4.0-1.1_i386.deb) ...
Selecting previously deselected package libmad0.
Unpacking libmad0 (from libmad0_0.15.1b-4_i386.deb) ...
Selecting previously deselected package libmjpegtools-1.9.
Unpacking libmjpegtools-1.9 (from libmjpegtools-1.9_1%3a1.9.0-0.0_i386.deb) ...
Selecting previously deselected package libmms0.
Unpacking libmms0 (from libmms0_0.4-2_i386.deb) ...
Selecting previously deselected package libmodplug0c2.
Unpacking libmodplug0c2 (from libmodplug0c2_1%3a0.8.4-3ubuntu1_i386.deb) ...
Selecting previously deselected package libmp3lame0.
Unpacking libmp3lame0 (from libmp3lame0_3.98-0.0_i386.deb) ...
Selecting previously deselected package libmpcdec3.
Unpacking libmpcdec3 (from libmpcdec3_1.2.2-1build1_i386.deb) ...
Selecting previously deselected package libmpeg2-4.
Unpacking libmpeg2-4 (from libmpeg2-4_0.4.1-3_i386.deb) ...
Selecting previously deselected package libmysqlclient15off.
Unpacking libmysqlclient15off (from libmysqlclient15off_5.1.30really5.0.75-0ubuntu10_i386.deb) ...
Selecting previously deselected package libneon27-gnutls.
Unpacking libneon27-gnutls (from libneon27-gnutls_0.28.2-6.1_i386.deb) ...
Selecting previously deselected package libofa0.
Unpacking libofa0 (from libofa0_0.9.3-3_i386.deb) ...
Selecting previously deselected package libopenspc0.
Unpacking libopenspc0 (from libopenspc0_0.3.99a-2_i386.deb) ...
Selecting previously deselected package libpostproc51.
Unpacking libpostproc51 (from libpostproc51_3%3a0.svn20090303-1ubuntu6_i386.deb) ...
Selecting previously deselected package libquicktime1.
Unpacking libquicktime1 (from libquicktime1_2%3a1.1.0+debian-1build1_i386.deb) ...
Selecting previously deselected package libraptor1.
Unpacking libraptor1 (from libraptor1_1.4.18-2_i386.deb) ...
Selecting previously deselected package libsidplay1.
Unpacking libsidplay1 (from libsidplay1_1.36.59-5_i386.deb) ...
Selecting previously deselected package libsoundtouch1c2.
Unpacking libsoundtouch1c2 (from libsoundtouch1c2_1.3.1-2_i386.deb) ...
Selecting previously deselected package libswscale0.
Unpacking libswscale0 (from libswscale0_3%3a0.svn20090303-1ubuntu6_i386.deb) ...
Selecting previously deselected package libtwolame0.
Unpacking libtwolame0 (from libtwolame0_0.3.12-1_i386.deb) ...
Selecting previously deselected package libwildmidi0.
Unpacking libwildmidi0 (from libwildmidi0_0.2.2-2_i386.deb) ...
Selecting previously deselected package libx264-65.
Unpacking libx264-65 (from libx264-65_1%3a0.svn20081230-0.0ubuntu1_i386.deb) ...
Selecting previously deselected package libxml++2.6-2.
Unpacking libxml++2.6-2 (from libxml++2.6-2_2.24.0-1ubuntu1_i386.deb) ...
Selecting previously deselected package libxvidcore4.
Unpacking libxvidcore4 (from libxvidcore4_2%3a1.1.2-0.1ubuntu3_i386.deb) ...
Selecting previously deselected package mysql-common.
Unpacking mysql-common (from mysql-common_5.1.30really5.0.75-0ubuntu10_all.deb) ...
Selecting previously deselected package raptor-utils.
Unpacking raptor-utils (from raptor-utils_1.4.18-2_i386.deb) ...
Setting up freepats (20060219-1) ...
Setting up gstreamer0.10-pitfdll (0.9.1.1+cvs20080215-1ubuntu1) ...
Setting up liba52-0.7.4 (0.7.4-11ubuntu1) ...

Setting up libavutil49 (3:0.svn20090303-1ubuntu6) ...

Setting up libcdaudio1 (0.99.12p2-7) ...

Setting up libcelt0 (0.5.1-0ubuntu1) ...

Setting up libdc1394-22 (2.0.2-1) ...

Setting up libdca0 (0.0.5-0.1) ...

Setting up libdvdread4 (4.1.3-4ubuntu2) ...

Setting up libenca0 (1.9-6) ...

Setting up libfaac0 (1.26-0.1ubuntu2) ...

Setting up libfaad0 (2.6.1-3.1) ...

Setting up libfftw3-3 (3.1.2-3.1ubuntu1) ...

Setting up libfreebob0 (1.0.11-0ubuntu1) ...

Setting up libid3tag0 (0.15.1b-10) ...

Setting up libiptcdata0 (1.0.2+libtool01-2ubuntu1) ...

Setting up libmad0 (0.15.1b-4) ...

Setting up libmms0 (0.4-2) ...

Setting up libmodplug0c2 (1:0.8.4-3ubuntu1) ...

Setting up libmp3lame0 (3.98-0.0) ...

Setting up libmpcdec3 (1.2.2-1build1) ...

Setting up libmpeg2-4 (0.4.1-3) ...

Setting up libneon27-gnutls (0.28.2-6.1) ...

Setting up libofa0 (0.9.3-3) ...

Setting up libopenspc0 (0.3.99a-2) ...

Setting up libpostproc51 (3:0.svn20090303-1ubuntu6) ...

Setting up libraptor1 (1.4.18-2) ...

Setting up libsidplay1 (1.36.59-5) ...

Setting up libsoundtouch1c2 (1.3.1-2) ...

Setting up libswscale0 (3:0.svn20090303-1ubuntu6) ...

Setting up libtwolame0 (0.3.12-1) ...

Setting up libwildmidi0 (0.2.2-2) ...

Setting up libx264-65 (1:0.svn20081230-0.0ubuntu1) ...

Setting up libxml++2.6-2 (2.24.0-1ubuntu1) ...

Setting up libxvidcore4 (2:1.1.2-0.1ubuntu3) ...

Setting up mysql-common (5.1.30really5.0.75-0ubuntu10) ...
Setting up raptor-utils (1.4.18-2) ...
Setting up gstreamer0.10-plugins-ugly (0.10.10.2-1build1) ...
Setting up gstreamer0.10-plugins-ugly-multiverse (0.10.7-2) ...
Setting up libass1 (0.9.5-2) ...

Setting up libavcodec52 (3:0.svn20090303-1ubuntu6) ...

Setting up libavformat52 (3:0.svn20090303-1ubuntu6) ...

Setting up libdvdnav4 (4.1.3-3) ...

Setting up libffado0 (2.0~rc1-0ubuntu2) ...

Setting up libjack0 (0.116.1-3ubuntu3) ...

Setting up liblrdf0 (0.4.0-1.1) ...

Setting up libmysqlclient15off (5.1.30really5.0.75-0ubuntu10) ...

Setting up libquicktime1 (2:1.1.0+debian-1build1) ...

Setting up gstreamer0.10-ffmpeg (0.10.6.2-1ubuntu2) ...
Setting up libgmyth0 (1:0.7.1-1ubuntu1) ...

Setting up libmjpegtools-1.9 (1:1.9.0-0.0) ...

Setting up gstreamer0.10-plugins-bad-multiverse (0.10.11-0ubuntu1) ...
Processing triggers for man-db ...
Setting up gstreamer0.10-plugins-bad (0.10.11-2ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
ubuntu@ubuntu:~/Desktop/archives$ 

All install properly and rhythmbox has full capabilities

(for flash I'd use the adobe ubuntu package
(if on 64 bit if needed I'll make package set, only takes 15 min or so

You should also, if on 32 bit, get and install w32codecs from medibuntu ( requires 1 add. package (libstdc++5 (>= 1:3.3.4-1)

---

### Post by GreenBowlPacker_3 on 2009-05-03
Some of that may be a little over my head, but I'm willing to give it a try.  I'll let you know how it goes.

---

### Post by mc4man on 2009-05-03
Here are 2 links for a **32 bit install**

As noted run to ck.
uname -m 

download, copy the .tar.bz's to a cd or usb drive and place either on desktop or in home folder of offline jaunty install

After the tranfer then right click on each ...tar.bz -> extract here 
Inside of the extracted folder is a readme for install command (1 if extracted to desktop, 1 if extracted to home folder (extra readme suggests 1 at a time method, do gstreamerplugs first

Note:
This will work perfectly on a 32 bit jaunty install though due to what you've previously done not 100% sure

The command to be used, (dpkg -i *.deb), if there is an issue, will cause a broken package(s)
In unlikely event of this don't freak out, can be easily fixed, *just leave the terminal open*, copy and paste complete terminal output into a reply and can be resolved

Ck pm concerning adobe flash in extra

[http://www.mediafire.com/file/dyz2ayjtzmt/gstreamerplugs.tar.gz](http://www.mediafire.com/file/dyz2ayjtzmt/gstreamerplugs.tar.gz)

[http://www.mediafire.com/file/zqxynmznmo5/extra.tar.bz2](http://www.mediafire.com/file/zqxynmznmo5/extra.tar.bz2)

---

### Post by GreenBowlPacker_3 on 2009-05-03
OK, thanks!  I'll download them and try it, I'll let you know how it works out.

---

### Post by mc4man on 2009-05-03
A small note
 I don't use gstreamer apps much and also make my own ffmpeg libraries so I've forgotten all about the stripped and unstripped versions

While it will have not effect on mp3's, for some other formats and players it's better to install the unstripped

Here is an update pack for the 4 libav codecs installed as part of gstreamer plugins

same deal as before, these must *all be updated at once with the included command*.

If I leave that gstreamerplugs dl up on mediafire I'll replace the current 'stripped' versions

[http://www.mediafire.com/file/dyuzy5z3j1g/newlibs.tar.bz2](http://www.mediafire.com/file/dyuzy5z3j1g/newlibs.tar.bz2)

---

