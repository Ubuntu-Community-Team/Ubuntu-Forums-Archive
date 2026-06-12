---
title: "Mission Encrypted DVD playback impossible"
date: 2008-12-25
forum: Multimedia Software
---

### Post by carbonic on 2008-12-25
I can't play encrypted dvd's!

**I've installed:**
-libdvdread3 libdvdcss2 libdvdcss ubuntu-restricted-extras libdvdnav4
**I've tried to:**
-Set the correct dvd region
-Have the medibuntu rep in my source.list and updated the system.
-Tried playing it in VLC, Movie Player (standard and xine), ogle
-The sudo/usr/share/doc/libdvdread3/install-css.sh routine

Everything works in Windows. nd I've got it to work in 8.04 and below. What could be wrong?
Using 8.10 now.

VLC crashes with:
[00000488] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
Segmentation fault

---

### Post by xc3RnbFO8P on 2008-12-25
Can you give us the long version, like this:
> rob@rob-desktop:~$ vlc
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '[COLOR="SeaGreen"]**--enable-a52**[/COLOR]' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: GARFIELD_2
libdvdnav: DVD Serial Number: 48C50254___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/rob/.dvdnav/GARFIELD_2.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000468] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[00000470] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:384000

---

### Post by carbonic on 2008-12-25
sure thing, I actually got a  slightly different output this along with actually watching some distorted parts of the begging of the dvd before it crashed:

$ vlc
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: SCRUBS_D1_S1_PAL
libdvdnav: DVD Serial Number: 32c6aa63
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/carbonic/.dvdnav/SCRUBS_D1_S1_PAL.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
[00000465] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000488] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
QPainter::begin: Paint device returned engine == 0, type: 1
[00000487] main decoder error: decoder is leaking pictures, resetting the heap
[00000493] main video output error: picture to date 0xb50496bc has invalid status 6
[00000493] main video output error: picture to display 0xb50496bc has invalid status 6
Segmentation fault

---

### Post by flyingcadet on 2008-12-25
I'm using Xubuntu, so ymmv.

To play DVDs, I had to use the instructions from [Medibuntu]("https://help.ubuntu.com/community/Medibuntu").  After that, I removed totem-gstreamer and replaced it with totem-xine.

Now, I can watch any DVD under Totem.

Good luck and Merry Christmas,

flyingcadet

---

### Post by carbonic on 2008-12-25
Well, Media Player and Totem is one and the same and have tried the Xine variant so no luck there. And I have tried everything from the site there - all to no avail.

---

### Post by flyingcadet on 2008-12-25
sorry, I'm not trying to sound redundant or insulting, but did you make sure to remove the totem-gstreamer package before installing the totem-xine package?  I had both installed at some point and still couldn't get DVD playback to work.

flyingcadet

---

### Post by xc3RnbFO8P on 2008-12-25
Do have Visual Effects enable? (Compiz)
If you have did you try to disable it.

---

### Post by carbonic on 2008-12-25
Disabled all compiz and am running with no affects
result: no effect

Uninstalled totem-gstreamer and totem-xine and reinstalled totem-xine
result: no effect
Still get the "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?" error in totem-xine even though libdvdcss IS installed.

---

### Post by mc4man on 2008-12-25
Do you know if a region has been set on the drive? If not install regionset and with a disk in the drive run from a terminal, 
regionset.

Around line 4 it will say set or none on the type line. If not set, set it to your region (2 or 4 ..?)
If it wasn't set after setting also go into home folder, and delete the .dvdcss folder. (hidden folder

Xine based players also need libxine1-ffmpeg installed, check.

---

### Post by carbonic on 2008-12-26
As mentioned in the first post, I have checked the region and it's correct.

libxine1-ffmpeg was also already installed.

---

### Post by xc3RnbFO8P on 2008-12-26
How did you install **libdvdread3**?

---

### Post by carbonic on 2008-12-26
Yes I do have libdvdread3 installed as also mentioned in the first post. But here's a check for you

> $ sudo apt-get install libdvdread3 libdvdcss2 ubuntu-restricted-extras libdvdnav4
[sudo] password for carbonic: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread3 is already the newest version.
libdvdcss2 is already the newest version.
ubuntu-restricted-extras is already the newest version.
libdvdnav4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by xc3RnbFO8P on 2008-12-26
I do this:
Ubuntu 8.10 (i386)

    *

      Install the libdvdread3 package (no need to add third party repositories) via Synaptic or command line: 

 > sudo apt-get install libdvdread3 gstreamer0.10-plugins-ugly

    * Then open a terminal window and execute: 

 > sudo /usr/share/doc/libdvdread3/install-css.sh
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by HousieMousie2 on 2008-12-26
> **flyingcadet said:**
> [Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Thanks!  Apparently I had failed to bookmark this page the first time I used it and was having hell finding it again after reinstalling.

---

### Post by mc4man on 2008-12-26
You should try switching video and maybe audio output modules.

In vlc go tools -> preferences, click on video and in the drop down for 'Output' change from default to something, try X11

Maybe also do the same for audio, try pulse, or alsa

Running vlc from the terminal with vlc-vv will provide info (too much actually, some error messages are normal

Vlc 0.9.x is broken in several ways, if the output module changes don't help then try in preferences -> interface -> disable 'show controller in interface' and or 'show a controller in fullscreen'

I read somewhere that getdeb has 0.9.8a packaged for 8.10, you may want to install it if that's true. (site is down right now, can't ck.
There have been a few bug fixes and if your going to use vlc might as well use the latest stable version.

---

### Post by carbonic on 2008-12-26
> **Ringi said:**
> How did you install **libdvdread3**?
Sudo apt-get, so shouldn't be any combability problems with ubuntu.

> You should try switching video and maybe audio output modules.

In vlc go tools -> preferences, click on video and in the drop down for 'Output' change from default to something, try X11

Maybe also do the same for audio, try pulse, or alsa

Running vlc from the terminal with vlc-vv will provide info (too much actually, some error messages are normal

Vlc 0.9.x is broken in several ways, if the output module changes don't help then try in preferences -> interface -> disable 'show controller in interface' and or 'show a controller in fullscreen'

I read somewhere that getdeb has 0.9.8a packaged for 8.10, you may want to install it if that's true. (site is down right now, can't ck.
There have been a few bug fixes and if your going to use vlc might as well use the latest stable version. 
I tried changing output, didn't make any difference. Also, considering this is not a VLC issue, but a general issue with encrypted dvd's nomatter what the program, I don't think installing a newer version of VLC will help.

---

### Post by carbonic on 2008-12-27
Just so people don't think it's a VLC only problem, here's a totem-xine run that ended brutally:
> $ totem-xine
** (totem-xine:11925): DEBUG: Init of Python module
** (totem-xine:11925): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem-xine:11925): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem-xine:11925): DEBUG: Creating Python plugin instance
** (totem-xine:11925): DEBUG: Init of Python module
** (totem-xine:11925): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem-xine:11925): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem-xine:11925): DEBUG: Creating Python plugin instance
** Message: no file info
libdvdnav: Using dvdnav version 1.1.15 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: SCRUBS_D1_S1_PAL
libdvdnav: DVD Serial Number: 32c6aa63
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/carbonic/.dvdnav/SCRUBS_D1_S1_PAL.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001f0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00066331
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00372b97
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00372b9d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00373e34
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00373e3a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003741cb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003741d1
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.
libdvdnav: Using dvdnav version 1.1.15 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: SCRUBS_D1_S1_PAL
libdvdnav: DVD Serial Number: 32c6aa63
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/carbonic/.dvdnav/SCRUBS_D1_S1_PAL.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000013f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001f0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00066331
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00372b97
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00372b9d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x00373e34
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x00373e3a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003741cb
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003741d1
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.


---

### Post by xc3RnbFO8P on 2008-12-27
I can't play this Garfield DVD in Totem and Elisa, but it plays in:
xine, gxine, vlc and kaffeine. 
```
rob@rob-desktop:~$ totem
** (totem:7163): DEBUG: Init of Python module
** (totem:7163): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:7163): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:7163): DEBUG: Creating Python plugin instance
** (totem:7163): DEBUG: Init of Python module
** (totem:7163): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:7163): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:7163): DEBUG: Creating Python plugin instance
** Message: no file info
** Message: no file info
** Message: no file info
** Message: no file info
** Message: no file info
** Message: no file info
** Message: no file info
** Message: no file info
** Message: no file info
** Message: no file info
** Message: no file info
Device is now /dev/scd0
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: DVD Title: GARFIELD_2
libdvdnav: DVD Serial Number: 48C50254___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/rob/.dvdnav/GARFIELD_2.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2
VTS change
cur audio stream change
NAV packet discont: cur_end_ts 99:99:99.999999999 !=  vobu_start_ptm: 0:00:00.280000000 base 0:00:00.000000000
seek completed. New start TS 0:00:00.280000000 pos 0:00:00.000000000
Pushing stream event
Pushing clut event
Pushing spu_select event
Pushing audio_select event
Discont packet
Pushing highlight event with TS 99:99:99.999999999

(totem:7163): GStreamer-CRITICAL **: Padname audio is not unique in element source, not adding
demux: got segment update 0 start 280000000 stop -1 time 0
sending new segment: update 0 rate 1 format 3, start: 10000000000, stop: -1, time: 0 scr_adjust: 874800(0:00:09.720000000)
VTS change
cur audio stream change
NAV packet discont: cur_end_ts 0:00:00.560000000 !=  vobu_start_ptm: 0:00:00.280000000 base 0:00:00.000000000
Pushing stream event
First audio after flush has TS 0:00:10.000000000
Pushing spu_select event
seek completed. New start TS 0:00:00.280000000 pos 0:00:00.000000000
demux: got segment update 1 start 280000000 stop 560000000 time 0
sending new segment: update 1 rate 1 format 3, start: 10000000000, stop: 10280000000, time: 0 scr_adjust: 874800(0:00:09.720000000)
demux: got segment update 0 start 280000000 stop -1 time 0
sending new segment: update 0 rate 1 format 3, start: 10280000000, stop: -1, time: 0 scr_adjust: 900000(0:00:10.000000000)

(totem:7163): GLib-GObject-WARNING **: IA__g_object_get_valist: object class `GstPlayBin' has no property named `current-subpicture'
** Message: Error: Internal data flow error.
rsnbasesrc.c(1905): rsn_base_src_loop (): /GstPlayBin:play/RsnDvdBin:source/resinDvdSrc:dvdsrc:
streaming task paused, reason not-negotiated (-4)

```

---

### Post by xc3RnbFO8P on 2008-12-27
carbonic you are using:** libdvdnav: Using dvdnav version 1.1.15 from [http://xine.sf.net](http://xine.sf.net)**
I am using: **libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)**

---

### Post by carbonic on 2008-12-27
> **Ringi said:**
> carbonic you are using:** libdvdnav: Using dvdnav version 1.1.15 from [http://xine.sf.net](http://xine.sf.net)**
I am using: **libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)**
True, I'm apparently only using 1.1.15 in totem-xine, but as you can see in the VLC output it uses 4.1.2 as well and still doesn't work. I don't know why Totem-xine uses an old version, but it has no problems navigating dvd's as that content on the dvd aint encrypted.

I don't mind trying to run Totem-xine with the new version, but then I'll figure out how to do it as I'm currently just using the newest version from the rep's

---

### Post by mc4man on 2008-12-27
xine engine players don't use the systems libdvdnav, it's either built-in or part of a libxine*

All versions of libdvdnav > 1.1.10 can handle some structure protections that the earlier versions couldn't. (udf filesize, dvd x-protect or similar)

Though in these cases you'd see something like this

> ......
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
libdvdread: Ignored UDF provided size of file.
libdvdread: Ignored UDF provided size of file.
.......
Structure protections are always evolving, you may have one that can't be handled or handled by particular players.

I think region 2 is much more likely to receive protected titles than other regions.

A current mplayer with dvdnav support will use the latest libdvdnav (4.1.3-1) and libdvdread4, maybe try. (can be used on intrepid and hardy

If you don't want to compile, the mplayer available from rvn's ppa (smplayer) is built as a dvdnav version. (uses the latest libs.

[http://smplayer.sourceforge.net/downloads.php?tr_lang=en](http://smplayer.sourceforge.net/downloads.php?tr_lang=en)


Though I won't use mplayer in 'dvdnav mode' on some protected titles .

---

### Post by carbonic on 2008-12-27
> **mc4man said:**
> xine engine players don't use the systems libdvdnav, it's either built-in or part of a libxine*

All versions of libdvdnav > 1.1.10 can handle some structure protections that the earlier versions couldn't. (udf filesize, dvd x-protect or similar)

Though in these cases you'd see something like this


Structure protections are always evolving, you may have one that can't be handled or handled by particular players.

I think region 2 is much more likely to receive protected titles than other regions.

A current mplayer with dvdnav support will use the latest libdvdnav (4.1.3-1) and libdvdread4, maybe try. (can be used on intrepid and hardy

If you don't want to compile, the mplayer available from rvn's ppa (smplayer) is built as a dvdnav version. (uses the latest libs.

[http://smplayer.sourceforge.net/downloads.php?tr_lang=en](http://smplayer.sourceforge.net/downloads.php?tr_lang=en)


Though I won't use mplayer in 'dvdnav mode' on some protected titles .

Ok, tried with a 3rd DVD and now it worked flawlessly. So I tried more and it seems the two I tested was the only one with problems, so I'd consider it a pretty good chance that it is the current "structure protection" that can't be played with all the software I've so far tested. I tried the SM player which you mentioned might have better support and it had, it actually shows the movie although sadly greatly distorted. Thanks for that mc4man! 

I guess that narrowed down the problem a great deal.

So now I guess I just need to find some "new player" or realise that Windows is just that much easier for my entertainment needs - oh I really don't want to go there.

---

### Post by mc4man on 2008-12-27
One solution that's Not Free would be to purchase powerdvd from the canonical store, I'd assume being a licensed player it would work. (or I'd complain

The other is if possible to get R 1 versions, I've only seen 2 titles that wouldn't play, both from universal about 6 months or so ago, since then they've not used that particular protection again.

Region 2 is treated a bit more 'harshly' than others. (and often by extension, Region 4

---

### Post by carbonic on 2008-12-27
> **mc4man said:**
> One solution that's Not Free would be to purchase powerdvd from the canonical store, I'd assume being a licensed player it would work. (or I'd complain

The other is if possible to get R 1 versions, I've only seen 2 titles that wouldn't play, both from universal about 6 months or so ago, since then they've not used that particular protection again.

Region 2 is treated a bit more 'harshly' than others. (and often by extension, Region 4
I'm not gonna buy software for my Linux, would kinda defeat the point of the installation in itself.

Could you tell me how to get hold of one of these R1 versions? This dvd is from Buena Vista (damn, getting it pirated would have been soooo much easier). I tried compiling the newest VLC myself along with installing some an already made package but failed horrible as I get lost inn the dependency userunfriendly nightmare, that is getting the newest software for Ubuntu.

---

### Post by xc3RnbFO8P on 2008-12-27
> I can't play this Garfield DVD in Totem and Elisa
I can play it now, just did this again:
> sudo /usr/share/doc/libdvdread3/install-css.sh

Edit:
Played the same DVD in VLC 
and now I cant play it in Totem.

Edit 2:
Can play DVD from playlist in Totem.

---

### Post by mc4man on 2008-12-27
> Could you tell me how to get hold of one of these R1 versions
Don't know. where I live i can buy versions of dvd's from other regions, maybe there are some vendors where you live.

> I tried compiling the newest VLC myself

It's not as difficult as it initially seems, if you really want to, read and post here and I'll take a shot at showing you (the Op never returned

[http://ubuntuforums.org/showthread.php?p=6408071#post6408071](http://ubuntuforums.org/showthread.php?p=6408071#post6408071)

I will say I've used 0.9.8a and currently have a recent 1.0 on hardy and not much has been fixed.

Also because 0.9.8a is a major security fix release, hopefully it will show up in intrepid shortly.


A free solution to your playback can be found here, many places to learn how to set up and use in linux (wine) (link in post 3

[http://forum.doom9.org/showthread.php?t=143404](http://forum.doom9.org/showthread.php?t=143404)

---

### Post by carbonic on 2008-12-28
> Don't know. where I live i can buy versions of dvd's from other regions, maybe there are some vendors where you live.
Ah I thought you ment r1 releases of players, not region 1 dvds.
I'm not gonna buy the wrong region dvds just because linux have problems with playing dvds with certain protection schemes.

I guess I'll just have to use Windows for this, although I find it sad and it really annoys me that Linux cannot compare to commercial OS's here (at least until some developer gets the same problem as me). I hate I just can't toss Windows away.

> It's not as difficult as it initially seems, if you really want to, read and post here and I'll take a shot at showing you (the Op never returned

[http://ubuntuforums.org/showthread.p...71#post6408071](http://ubuntuforums.org/showthread.p...71#post6408071)
I installed "sudo apt-get build-dep vlc"
and did the ./configure successfully as mentioned in the install file in the tar
then I tried to do 
$make install
and I got this:

/usr/bin/ld: cannot find -lvlccore
collect2: ld returned 1 exit status
libtool: install: error: relink `libvlc.la' with the above command before installing it
make[5]: *** [install-libLTLIBRARIES] Error 1
make[5]: Leaving directory `/home/carbonic/Desktop/vlc-0.9.8a/src'
make[4]: *** [install-am] Error 2
make[4]: Leaving directory `/home/carbonic/Desktop/vlc-0.9.8a/src'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/carbonic/Desktop/vlc-0.9.8a/src'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/carbonic/Desktop/vlc-0.9.8a/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/carbonic/Desktop/vlc-0.9.8a'
make: *** [install] Error 2


> A free solution to your playback can be found here, many places to learn how to set up and use in linux (wine) (link in post 3

[http://forum.doom9.org/showthread.php?t=143404](http://forum.doom9.org/showthread.php?t=143404)
I don't think I'll gonne install some windows program to rip my dvd's to my harddrive when I got the original dvd that works on everything else than Linux, sorry.

---

### Post by carbonic on 2008-12-30
Oh well, guess I'll give up on trying to get my dvd's to play on Ubuntu. Guess the whole idea with "for human beings" goes out the window, but I guess I'll have to wait longer until Linux is there.

---

### Post by xc3RnbFO8P on 2008-12-30
Can you show the output of this:
> lsb_release -rd ; uname -a ; apt-cache policy ffmpeg libdvdcss2 libdvdread3 regionset

---

### Post by carbonic on 2008-12-30
Sure
> 
$ lsb_release -rd ; uname -a ; apt-cache policy ffmpeg libdvdcss2 libdvdread3 regionset
Description:    Ubuntu 8.10                                                                                      
Release:        8.10                                                                                             
Linux carbonic-laptop 2.6.27-11-generic #1 SMP Fri Dec 19 16:29:52 UTC 2008 i686 GNU/Linux                       
ffmpeg:                                                                                                          
  Installed: 3:0.svn20080206-12ubuntu3                                                                           
  Candidate: 3:0.svn20080206-12ubuntu3                                                                           
  Version table:                                                                                                 
 *** 3:0.svn20080206-12ubuntu3 0                                                                                 
        500 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/main Packages                                                  
        100 /var/lib/dpkg/status                                                                                 
libdvdcss2:                                                                                                      
  Installed: 1.2.10-0.2medibuntu1                                                                                
  Candidate: 1.2.10-0.2medibuntu1                                                                                
  Version table:                                                                                                 
 *** 1.2.10-0.2medibuntu1 0
        500 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages
        100 /var/lib/dpkg/status
libdvdread3:
  Installed: 0.9.7-11ubuntu2
  Candidate: 0.9.7-11ubuntu2
  Version table:
 *** 0.9.7-11ubuntu2 0
        500 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/universe Packages
        100 /var/lib/dpkg/status
regionset:
  Installed: 0.1-3
  Candidate: 0.1-3
  Version table:
 *** 0.1-3 0
        500 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) intrepid/universe Packages
        100 /var/lib/dpkg/status



---

