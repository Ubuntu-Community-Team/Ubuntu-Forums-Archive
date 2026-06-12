---
title: "Acidrip and Handbrake will not decode DVD"
date: 2014-11-08
forum: Multimedia Software
---

### Post by Tyler_Whitlock on 2014-11-08
I currently have VLC, libdvdcss2, Acidrip, and Handbrake all installed. Only VLC will read my DVD. Acidrip and Handbrake will not. The following is the log from Acidrip:

```

[00:51:49] gtkgui: HandBrake rev5474 (2014032499) - Linux x86_64 - http://handbrake.fr
[00:51:49] hb_init: starting libhb thread
[00:51:49] hb_init: starting libhb thread
[00:52:03] hb_scan: path=/media/tyler/LES_MISERABLES_DOM/AACS, title_index=0
libbluray/bdnav/index_parse.c:162: indx_parse(): error opening /media/tyler/LES_MISERABLES_DOM/AACS/BDMV/index.bdmv
libbluray/bdnav/index_parse.c:162: indx_parse(): error opening /media/tyler/LES_MISERABLES_DOM/AACS/BDMV/BACKUP/index.bdmv
libbluray/bluray.c:2182: nav_get_title_list(/media/tyler/LES_MISERABLES_DOM/AACS) failed
[00:52:03] bd: not a bd - trying as a stream/file instead
libdvdnav: Using dvdnav version 4.2.1
libdvdread: Couldn't find device name.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[00:52:03] dvd: not a dvd - trying as a stream/file instead
[00:52:03] batch: scanning /media/tyler/LES_MISERABLES_DOM/AACS/MKB_RO.inf
[mp3 @ 0x7f8020005ee0] Header missing
[mp3 @ 0x7f8020005ee0] Header missing
[mp3 @ 0x7f8020005ee0] Header missing
[mp3 @ 0x7f8020005ee0] Header missing
[mp3 @ 0x7f8020005ee0] Header missing
[mp3 @ 0x7f8020005ee0] Header missing
[00:52:03] hb_stream_open: open /media/tyler/LES_MISERABLES_DOM/AACS/MKB_RO.inf failed
[00:52:03] batch: scanning /media/tyler/LES_MISERABLES_DOM/AACS/MKB_RW.inf
[00:52:04] hb_stream_open: open /media/tyler/LES_MISERABLES_DOM/AACS/MKB_RW.inf failed
[00:52:04] batch: scanning /media/tyler/LES_MISERABLES_DOM/AACS/ContentRevocation.lst
[00:52:04] hb_stream_open: open /media/tyler/LES_MISERABLES_DOM/AACS/ContentRevocation.lst failed
[00:52:04] batch: scanning /media/tyler/LES_MISERABLES_DOM/AACS/Unit_Key_RO.inf
[00:52:04] hb_stream_open: open /media/tyler/LES_MISERABLES_DOM/AACS/Unit_Key_RO.inf failed
[00:52:04] batch: scanning /media/tyler/LES_MISERABLES_DOM/AACS/Content000.cer
[00:52:04] hb_stream_open: open /media/tyler/LES_MISERABLES_DOM/AACS/Content000.cer failed
[00:52:04] batch: scanning /media/tyler/LES_MISERABLES_DOM/AACS/Content001.cer
[mp3 @ 0x7f8020005dc0] Header missing
[00:52:04] hb_stream_open: open /media/tyler/LES_MISERABLES_DOM/AACS/Content001.cer failed
[00:52:04] batch: scanning /media/tyler/LES_MISERABLES_DOM/AACS/CPSUnit00001.cci
[00:52:04] hb_stream_open: open /media/tyler/LES_MISERABLES_DOM/AACS/CPSUnit00001.cci failed
[00:52:04] batch: scanning /media/tyler/LES_MISERABLES_DOM/AACS/CPSUnit00002.cci
[00:52:04] hb_stream_open: open /media/tyler/LES_MISERABLES_DOM/AACS/CPSUnit00002.cci failed
[00:52:04] batch: scanning /media/tyler/LES_MISERABLES_DOM/AACS/CPSUnit00003.cci
[00:52:04] hb_stream_open: open /media/tyler/LES_MISERABLES_DOM/AACS/CPSUnit00003.cci failed
[00:52:04] batch: scanning /media/tyler/LES_MISERABLES_DOM/AACS/CPSUnit00004.cci
[00:52:04] hb_stream_open: open /media/tyler/LES_MISERABLES_DOM/AACS/CPSUnit00004.cci failed
[00:52:04] batch: scanning /media/tyler/LES_MISERABLES_DOM/AACS/CPSUnit00005.cci
[00:52:04] hb_stream_open: open /media/tyler/LES_MISERABLES_DOM/AACS/CPSUnit00005.cci failed
[00:52:04] batch: scanning /media/tyler/LES_MISERABLES_DOM/AACS/CPSUnit00006.cci
[00:52:04] hb_stream_open: open /media/tyler/LES_MISERABLES_DOM/AACS/CPSUnit00006.cci failed
[00:52:04] batch: scanning /media/tyler/LES_MISERABLES_DOM/AACS/CPSUnit00007.cci
[00:52:04] hb_stream_open: open /media/tyler/LES_MISERABLES_DOM/AACS/CPSUnit00007.cci failed
[00:52:04] batch: scanning /media/tyler/LES_MISERABLES_DOM/AACS/mcmf.xml
[00:52:04] hb_stream_open: open /media/tyler/LES_MISERABLES_DOM/AACS/mcmf.xml failed
[00:52:04] batch: scanning /media/tyler/LES_MISERABLES_DOM/AACS/ContentHash001.tbl
[00:52:04] hb_stream_open: open /media/tyler/LES_MISERABLES_DOM/AACS/ContentHash001.tbl failed
[00:52:04] batch: scanning /media/tyler/LES_MISERABLES_DOM/AACS/ContentHash000.tbl
[00:52:05] hb_stream_open: open /media/tyler/LES_MISERABLES_DOM/AACS/ContentHash000.tbl failed
[00:52:05] libhb: scan thread found 0 valid title(s)

```

I've followed the tutorial in the documentiation provided by the Ubuntu community here [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) 

The following is proof that the software mentioned is installed, as well as listing the versions.

```

tyler@REPUS:~$ dpkg -s libdvdcss2
Package: libdvdcss2
Status: install ok installed
Priority: extra
Section: libs
Installed-Size: 85
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Architecture: amd64
Source: libdvdcss
Version: 1.2.13-0
Depends: libc6 (>= 2.7)
Description: library designed for accessing DVDs
 libdvdcss is a simple library designed for accessing DVDs like a
 block device without having to bother about the decryption.
Homepage: http://download.videolan.org/
Original-Maintainer: Jonathan Riddell <jriddell@ubuntu.com>
tyler@REPUS:~$ dpkg -s acidrip
Package: acidrip
Status: install ok installed
Priority: optional
Section: graphics
Installed-Size: 255
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: mailto:marillat@debian.org
Architecture: all
Version: 0.14-0.2ubuntu7
Depends: perl, libgtk2-perl, lsdvd (>= 0.10), mplayer, mencoder
Description: ripping and encoding DVD tool using mplayer and mencoder
 A DVD ripper and encoder, with a simple interface, based on MPlayer
 and MEncoder.
 .
 Also provides advanced features and automates the process in a number
 of ways:
  * Parses DVD into contents tree
  * Finds longest title
  * Calculates video bitrate for given filesize
  * Finds black bands and crops them
  * Gives suggestions for improved performance
Homepage: http://untrepid.com/acidrip/
Original-Maintainer: Christian Marillat <marillat@debian.org>
tyler@REPUS:~$ dpkg -s handbreak-gtk
dpkg-query: package 'handbreak-gtk' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
tyler@REPUS:~$ dpkg -s handbrake
Package: handbrake
Status: install ok installed
Priority: optional
Section: graphics
Installed-Size: 2607
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 0.9.9+dfsg-2~2.gbpa4c3e9build1
Replaces: handbrake-gtk
Depends: liba52-0.7.4, libass4 (>= 0.9.7), libavcodec54 (>= 6:9.1-1) | libavcodec-extra-54 (>= 6:9.11), libavformat54 (>= 6:9.1-1), libavresample1 (>= 6:9.1-1), libavutil52 (>= 6:9.1-1), libbluray1 (>= 1:0.2.2), libc6 (>= 2.14), libcairo2 (>= 1.2.4), libdbus-glib-1-2 (>= 0.78), libdvdnav4 (>= 4.2.1-3), libdvdread4 (>= 4.1.3), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.37.3), libgstreamer-plugins-base1.0-0 (>= 1.0.0), libgstreamer1.0-0 (>= 1.0.0), libgtk2.0-0 (>= 2.24.0), libgudev-1.0-0 (>= 146), libmkv0 (>= 0.6.5.1), libmp3lame0, libmpeg2-4, libnotify4 (>= 0.7.3), libpango-1.0-0 (>= 1.14.0), libsamplerate0 (>= 0.1.7), libswscale2 (>= 6:9.1-1), libtheora0 (>= 1.0), libvorbis0a (>= 1.1.2), libvorbisenc2 (>= 1.1.2), libwebkitgtk-1.0-0 (>= 1.3.10), libx264-142
Pre-Depends: dpkg (>= 1.15.6~)
Recommends: gstreamer1.0-libav, gstreamer1.0-pulseaudio | gstreamer1.0-alsa, gstreamer1.0-x
Breaks: libdvdread4 (<< 4.2.0+20120521-3)
Conflicts: handbrake-gtk
Description: versatile DVD ripper and video transcoder (GTK GUI)
 HandBrake is a versatile, easy-to-use tool for converting DVDs and other
 videos into H.264, XViD, or OGG formatted media. It's particularly useful
 for making videos that are compatible with portable video devices such as
 the Apple iPod/iPhone or Sony PSP.
 .
 This version of handbrake has been modified for inclusion in Debian.
 It does neither support audio encoding to AAC via faac nor MP4 format
 muxing via libmp4v2, it falls back to the MKV format instead.
 .
 This package contains the graphical variant, ghb.
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Homepage: http://www.handbrake.fr/
tyler@REPUS:~$ dpkg -s vlc
Package: vlc
Status: install ok installed
Priority: optional
Section: video
Installed-Size: 3765
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 2.1.4-0ubuntu14.04.1
Replaces: vlc-data (<< 1.1.5), vlc-nox (<< 2.0.2)
Provides: mp3-decoder
Depends: fonts-freefont-ttf, vlc-nox (= 2.1.4-0ubuntu14.04.1), libaa1 (>= 1.4p5), libc6 (>= 2.15), libcaca0 (>= 0.99.beta17-1), libfreetype6 (>= 2.2.1), libfribidi0 (>= 0.19.2), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libqtcore4 (>= 4:4.8.0), libqtgui4 (>= 4:4.8.0), libsdl-image1.2 (>= 1.2.10), libsdl1.2debian (>= 1.2.11), libstdc++6 (>= 4.6), libtar0, libva-x11-1 (>> 1.3.0~), libva1 (>> 1.3.0~), libvlccore7 (>= 2.1.0), libx11-6, libxcb-composite0, libxcb-keysyms1 (>= 0.3.9), libxcb-randr0 (>= 1.1), libxcb-shm0, libxcb-xv0 (>= 1.2), libxcb1 (>= 1.6), libxext6, libxinerama1, libxpm4, zlib1g (>= 1:1.2.3.3)
Pre-Depends: dpkg (>= 1.15.6~)
Recommends: vlc-plugin-notify (= 2.1.4-0ubuntu14.04.1), vlc-plugin-pulse (= 2.1.4-0ubuntu14.04.1), xdg-utils
Suggests: videolan-doc
Breaks: vlc-data (<< 1.1.5), vlc-nox (<< 2.0.2)
Description: multimedia player and streamer
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG-2, MPEG-4,
 DivX, MOV, WMV, QuickTime, WebM, FLAC, MP3, Ogg/Vorbis files, DVDs, VCDs,
 podcasts, and multimedia streams from various network sources.
 .
 VLC can also be used as a streaming server that duplicates the stream it
 reads and multicasts them through the network to other clients, or serves
 them through HTTP.
 .
 VLC has support for on-the-fly transcoding of audio and video formats, either
 for broadcasting purposes or for movie format transformations. Support for
 most output methods is provided by this package, but features can be added
 by installing additional audio plugins (vlc-plugin-pulse, vlc-plugin-sdl)
 or video plugins (vlc-plugin-sdl).
Homepage: http://www.videolan.org/vlc/
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
tyler@REPUS:~$ 



```

---

### Post by SeijiSensei on 2014-11-08
Just to make sure, did you run the [required command]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu_12.04.2C_12.10.2C_13.04.2C_13.10.2C_14.04_.28i386.2C_amd64.29"):
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by Tyler_Whitlock on 2014-11-08
> **SeijiSensei said:**
> Just to make sure, did you run the [required command]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu_12.04.2C_12.10.2C_13.04.2C_13.10.2C_14.04_.28i386.2C_amd64.29"):
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```


Yes, and I ran it again just now for good measure. No change.

---

### Post by SeijiSensei on 2014-11-08
Are you using the version of Handbrake from John Stebbins's PPA?  If not, I'd give that a try.  

Try first: [https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases](https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases)

If that doesn't work, try [https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots)

---

### Post by Tyler_Whitlock on 2014-11-09
> **SeijiSensei said:**
> Are you using the version of Handbrake from John Stebbins's PPA?  If not, I'd give that a try.  

Try first: [https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases](https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-releases)

If that doesn't work, try [https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots)


First one didn't have one for Tahr

Second, didn't resolve.

---

### Post by Tyler_Whitlock on 2014-11-09
I figured out the problem. I was working with a Bluray which required a different decoder. I used the following found on this forum: [http://askubuntu.com/questions/140080/playing-blu-ray-using-vlc](http://askubuntu.com/questions/140080/playing-blu-ray-using-vlc)

sudo add-apt-repository ppa:n-muench/vlc
sudo apt-get update
sudo apt-get install libaacs0 libbluray-bdj libbluray1
sudo apt-get dist-upgrade

cd ~/
mkdir -p ~/.config/aacs/
cd ~/.config/aacs/ && wget [http://vlc-bluray.whoknowsmy.name/files/KEYDB.cfg](http://vlc-bluray.whoknowsmy.name/files/KEYDB.cfg)

---

