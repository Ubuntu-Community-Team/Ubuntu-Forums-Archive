---
title: "Problems with VLC ( closed after insert DVD)"
date: 2008-07-01
forum: Multimedia Software
---

### Post by elegua on 2008-07-01
Hi Guys,

I just install ubuntu 8.04 2 days ago and so far i like it so much.

My problems is with VLC Media Player, i installed it and put it as a default to open DVD's following these steps:

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_make_VLC_open_when_you_insert_a_DVD)

Everything is working good, when i inserted a DVD in my Laptop VLC started but after few seconds it closed by itself and cannot see any DVD.

My questions is, how can i fix this problem?,

Thanks in Advance.

---

### Post by rainwalker on 2008-07-01
Do you have libdvdcss, libdvdread, and libnav?
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by mc4man on 2008-07-01
> following these steps:
 i don't think that's the best way to set vlc as a default choice, but what's done is done. (that's not to say it won't work) Go back to where you set the Exec=vlc %f and change it to Exec=vlc %m (or set it back to %U)
 Also go edit menus -> click sound and video -> on the right side - right click vlc -> properties and change launch command to  vlc %m.

note there is a space between vlc and %m
And as noted above you must have libdvdcss2 (medibuntu)

---

### Post by elegua on 2008-07-02
> **rainwalker said:**
> Do you have libdvdcss, libdvdread, and libnav?
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Thanks rainwalker, yes i do have installed those lib's, i followed your link from top to bottom, i installed ubuntu from scratch and then all the applications (libs, plugins, etc) in that link and still my vlc crash after few second after started.

Is any other way to fix this?

---

### Post by elegua on 2008-07-02
> **mc4man said:**
> i don't think that's the best way to set vlc as a default choice, but what's done is done. (that's not to say it won't work) Go back to where you set the Exec=vlc %f and change it to Exec=vlc %m (or set it back to %U)
 Also go edit menus -> click sound and video -> on the right side - right click vlc -> properties and change launch command to  vlc %m.

note there is a space between vlc and %m
And as noted above you must have libdvdcss2 (medibuntu)

Thanks mc4man for you replay, i installed ubuntu from scratch and followed the link posted by rainwalker and did the steps to use vlc as a default and still vlc crash after few seconds of opened, i installed all the lib's i need to pay dvd's.

Is any other way to do this?.

---

### Post by mc4man on 2008-07-03
You could try opening vlc from the terminal, trying a disk and posting the errors.
If you don't know whether a region has been set on the drive then install regionset and check. (only needs to have been set _once_)
[http://ubuntuforums.org/showthread.php?t=837701&highlight=regionset](http://ubuntuforums.org/showthread.php?t=837701&highlight=regionset)

---

### Post by elegua on 2008-07-04
> **mc4man said:**
> You could try opening vlc from the terminal, trying a disk and posting the errors.
If you don't know whether a region has been set on the drive then install regionset and check. (only needs to have been set _once_)
[http://ubuntuforums.org/showthread.php?t=837701&highlight=regionset](http://ubuntuforums.org/showthread.php?t=837701&highlight=regionset)

Thanks mc4man for taking the time to help me.

Here is what i got for regionset output

```
gabby@gabby-laptop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:n
gabby@gabby-laptop:~$ 
```

Also, when i trying to open from the terminal i don't get any error, vlc opened fine, here is a pic:

[IMG]http://img240.imageshack.us/img240/7817/vlcyf3.png[/IMG]

But when i put a DVD vlc opened but crash after few seconds, i was reading this post:

[COLOR="Red"][http://ubuntuforums.org/showthread.php?t=681408](http://ubuntuforums.org/showthread.php?t=681408)[/COLOR]

i tried this and still crash so do you have any idea why is this happening?, please let me know if you need more info.

Here's some output from terminal:

```
gabby@gabby-laptop:~$ dpkg -s vlc
Package: vlc
Status: install ok installed
Priority: optional
Section: graphics
Installed-Size: 3228
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3
Replaces: vlc-aa (<< 0.5.0), vlc-lirc (<< 0.5.0), vlc-mad (<< 0.5.0), vlc-plugin-a52 (<< 0.5.2-2), vlc-plugin-aa (<< 0.5.2-2), vlc-plugin-alsa (<< 0.8.5-test3.debian-4), vlc-plugin-dv (<< 0.5.2-2), vlc-plugin-dvb (<< 0.5.2-2), vlc-plugin-lirc (<< 0.5.2-2), vlc-plugin-mad (<< 0.5.2-2), vlc-plugin-ogg (<< 0.5.2-2), vlc-plugin-xosd (<< 0.5.2-2), wxvlc (<< 0.8.5-test3.debian-4)
Provides: mp3-decoder
Depends: libaa1 (>= 1.4p5), libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcaca0 (>= 0.99.beta13b-1), libcairo2 (>= 1.6.0), libcdio7, libcucul0 (>= 0.99.beta13b-1), libdbus-1-3 (>= 1.1.1), libdbus-glib-1-2 (>= 0.74), libfreetype6 (>= 2.3.5), libfribidi0 (>= 0.10.9), libgcc1 (>= 1:4.1.1-21), libgl1-mesa-glx | libgl1, libglib2.0-0, libglu1-mesa | libglu1, libgtk2.0-0 (>= 2.12.0), libice6 (>= 1:1.0.0), libiso9660-5, libjpeg62, libnotify1 (>= 0.4.4), libnotify1-gtk2.10, libpango1.0-0 (>= 1.20.1), libpng12-0 (>= 1.2.13-4), libsdl-image1.2 (>= 1.2.5), libsdl1.2debian (>= 1.2.10-1), libsm6, libstdc++6 (>= 4.2.1-4), libtar, libtiff4, libvcdinfo0 (>> 0.7.23), libvlc0 (>= 0.8.6.release.e+x264svn20071224+faad2.6.1), libwxbase2.6-0 (>= 2.6.3.2.2), libwxgtk2.6-0 (>= 2.6.3.2.2), libx11-6, libxext6, libxinerama1, libxosd2 (>= 2.2.13), libxv1, ttf-dejavu, vlc-nox (= 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3), vlc-plugin-pulse, zlib1g (>= 1:1.2.3.3.dfsg-1)
Recommends: videolan-doc
Suggests: mozilla-plugin-vlc
Conflicts: vlc-aa (<< 0.5.0), vlc-lirc (<< 0.5.0), vlc-mad (<< 0.5.0), vlc-plugin-a52 (<< 0.5.2-2), vlc-plugin-aa (<< 0.5.2-2), vlc-plugin-alsa (<< 0.8.5-test3.debian-4), vlc-plugin-dv (<< 0.5.2-2), vlc-plugin-dvb (<< 0.5.2-2), vlc-plugin-lirc (<< 0.5.2-2), vlc-plugin-mad (<< 0.5.2-2), vlc-plugin-ogg (<< 0.5.2-2), vlc-plugin-xosd (<< 0.5.2-2), wxvlc (<< 0.8.5-test3.debian-4)
Description: multimedia player and streamer
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.
 .
 VLC can also be used as a streaming server that duplicates the stream it
 reads and multicasts them through the network to other clients, or serves
 them through HTTP.
 .
 VLC has support for on-the-fly transcoding of audio and video formats, either
 for broadcasting purposes or for movie format transformations. Support for
 most output methods is provided by this package, but features can be added
 by installing additional audio plugins (vlc-plugin-esd, vlc-plugin-sdl,
 vlc-plugin-arts, vlc-plugin-pulse) or video plugins (vlc-plugin-sdl,
 vlc-plugin-ggi, vlc-plugin-glide, vlc-plugin-svgalib). There is also a web
 browser plugin in the mozilla-plugin-vlc package.
Original-Maintainer: Sam Hocevar (Debian packages) <sam+deb@zoy.org>
gabby@gabby-laptop:~$
```


```
gabby@gabby-laptop:~$ dpkg -L vlc
/.
/usr
/usr/bin
/usr/lib
/usr/lib/vlc
/usr/lib/vlc/access
/usr/lib/vlc/access/libscreen_plugin.so
/usr/lib/vlc/audio_filter
/usr/lib/vlc/audio_mixer
/usr/lib/vlc/audio_output
/usr/lib/vlc/codec
/usr/lib/vlc/codec/libsdl_image_plugin.so
/usr/lib/vlc/control
/usr/lib/vlc/demux
/usr/lib/vlc/gui
/usr/lib/vlc/gui/libskins2_plugin.so
/usr/lib/vlc/gui/libwxwidgets_plugin.so
/usr/lib/vlc/misc
/usr/lib/vlc/misc/libnotify_plugin.so
/usr/lib/vlc/video_chroma
/usr/lib/vlc/video_filter
/usr/lib/vlc/video_output
/usr/lib/vlc/video_output/libx11_plugin.so
/usr/lib/vlc/video_output/libxvideo_plugin.so
/usr/lib/vlc/video_output/libglx_plugin.so
/usr/lib/vlc/video_output/libaa_plugin.so
/usr/lib/vlc/video_output/libcaca_plugin.so
/usr/lib/vlc/video_output/libopengl_plugin.so
/usr/lib/vlc/visualization
/usr/lib/vlc/visualization/libxosd_plugin.so
/usr/lib/mime
/usr/lib/mime/packages
/usr/lib/mime/packages/vlc
/usr/share
/usr/share/doc
/usr/share/doc/vlc
/usr/share/applications
/usr/share/applications/vlc.desktop
/usr/share/pixmaps
/usr/share/pixmaps/vlc.png
/usr/share/vlc
/usr/share/vlc/skins2
/usr/share/vlc/skins2/fonts
/usr/share/vlc/skins2/skin.dtd
/usr/share/vlc/skins2/skin.catalog
/usr/share/vlc/skins2/winamp2.xml
/usr/share/vlc/skins2/default.vlt
/usr/share/vlc/pda-forwardb16x16.xpm
/usr/share/vlc/pda-openb16x16.xpm
/usr/share/vlc/pda-pauseb16x16.xpm
/usr/share/vlc/pda-playb16x16.xpm
/usr/share/vlc/pda-playlistb16x16.xpm
/usr/share/vlc/pda-preferencesb16x16.xpm
/usr/share/vlc/pda-rewindb16x16.xpm
/usr/share/vlc/pda-stopb16x16.xpm
/usr/share/vlc/vlc.xpm
/usr/share/vlc/vlc16x16.xpm
/usr/share/vlc/vlc48x48.ico
/usr/share/vlc/wxvlc.xpm
/usr/share/man
/usr/share/man/man1
/usr/share/menu
/usr/share/menu/vlc
/usr/bin/svlc
/usr/bin/wxvlc
/usr/share/vlc/skins2/fonts/FreeSans.ttf
/usr/share/vlc/skins2/fonts/FreeSansBold.ttf
/usr/share/man/man1/svlc.1.gz
/usr/share/man/man1/wxvlc.1.gz
gabby@gabby-laptop:~$
```

Thanks in advance.

---

### Post by Terry19 on 2008-07-04
vlc is a very tricky player and i have never recomended it alto lots of people do for some reason, I recomend GOM but it only works with windows wine becuase is made for windows. You might have trouble getting codects to install but it is possable.

---

### Post by Prefix100 on 2008-07-04
I've had a similar problem before, but installing libdvdcss2 worked for me.

Try this topic, [http://ubuntuforums.org/showthread.php?t=739636](http://ubuntuforums.org/showthread.php?t=739636)

Don't resort to wine unless you really *really* have to. ( Which you shouldn't - VLC should work fine )

EDIT: Also, did DVDs work in VLC before you followed that guide?

---

### Post by elegua on 2008-07-04
> **Prefix100 said:**
> I've had a similar problem before, but installing libdvdcss2 worked for me.

Try this topic, [http://ubuntuforums.org/showthread.php?t=739636](http://ubuntuforums.org/showthread.php?t=739636)

Don't resort to wine unless you really *really* have to. ( Which you shouldn't - VLC should work fine )

EDIT: Also, did DVDs work in VLC before you followed that guide?

Hi Prefix100,

Thanks for your link, this is what i got when use this "vlc dvd:///dev/scd0" cmd:

```

gabby@gabby-laptop:~$ vlc dvd:///dev/scd0
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: VIDEO_DVD
libdvdnav: DVD Serial Number: 486B0A0B________
libdvdnav: DVD Title (Alternative): VIDEO_DVD
libdvdnav: Unable to find map file '/home/gabby/.dvdnav/VIDEO_DVD.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
libdvdnav: *** pgci_ut handle is NULL ***
libdvdnav: *** pgci_ut handle is NULL ***

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000013b
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
[00000304] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  90
  Current serial number in output stream:  91
gabby@gabby-laptop:~$ 
```
 

**" insufficient resources for operation" ???**, I have 512MB memory and 60GB hard drive, i only have ubuntu installed, no windows here, this is Toshiba P25 507 with 32MB Nvidia video Card, intel P4 2.8 and 17 inch monitor, also i had winXP here before and i never had any problem playing DVD's, i never used VLC before but i saw a lot of movies using win media player.

For what i can see i got an error, anyone knows what that error means?


```
Error of failed request:  BadAlloc (insufficient resources for operation)
 Major opcode of failed request:  141 (XVideo)
 Minor opcode of failed request:  19 ()
 Serial number of failed request:  90
 Current serial number in output stream:  91

```

Thanks in advance.

---

### Post by mc4man on 2008-07-04
You may want to try - open vlc -> settings -> preferences -> click advanced options on bottom right -> expand video -> highlight output modules -> and in drop down on right side change from default to X11, Click save and try again. If that works you may want to see why Xv doesn't.
Did you get your autoplay squared away? (I'd be surprised if you did, but then again ....)

---

### Post by treymul on 2008-07-04
It did the same thing to me until I changed the output module.  Open vlc, click on setting, then preferences.  Click on output modules and check the box in the lower right corner that says advanced options.  Now select x11 video output and click on save.  This fixed it for me, hope it helps you.

---

### Post by elegua on 2008-07-04
Hi Guys,

That did it, i have "default" and changed to "X11" and now it's working perfect.

Thanks guys, i really appreciate all your help.

---

### Post by rainwalker on 2008-07-05
Changing the video output to X11 got DVDs to play for me, but playback (audio and video) is jumpy

---

