---
title: "DVD Playback"
date: 2009-09-05
forum: Multimedia Software
---

### Post by cynicalcylon on 2009-09-05
I have trawled through the threads, installed a couple of extra packages, but still I can't seem to find a solution to my problem.

My DVDs aren't playing from any of my players.

It is set to auto play from Totem (which is my preffered player), but that just shuts straight down when I try to play DVD.
In VLC, it won't even open when I tell it to open with VLC.
Neither of these programs have problems playing media files from my PC, just the DVDs.

The DVD is showing as available (the icon appears on my Desktop) and when I double-click it it opens into a file no problems, so it is recognising it as available, just not playing it.

I have just had to reinstall (I'm using 8.10 currently) and now I can't play DVDs.
I admit that I'm a bit of a baby when it comes to Ubuntu, and a friend set it up first time, but I'm really not even sure what the heck the problem is.

---

### Post by cronholio on 2009-09-05
Did you install libdvdcss2?

---

### Post by cynicalcylon on 2009-09-05
> **cronholio said:**
> Did you install libdvdcss2?

Yes indeed

---

### Post by cronholio on 2009-09-05
Open the VLC messages window (Ctrl-M) before you try to play the DVD and see what it says.

---

### Post by cynicalcylon on 2009-09-05
p, li { white-space: pre-wrap; }  > [COLOR=#00008B]*main*[/COLOR][COLOR=#0000FF]* info: *[/COLOR][COLOR=#000000]Running vlc with the default interface. Use 'cvlc' to use vlc without interface.[/COLOR][COLOR=#000000][/COLOR]

---

### Post by cronholio on 2009-09-05
Umm, is that all? I mean, you should open VLC, open the messages window, try to play the DVD and **then** check the messages.

---

### Post by mc4man on 2009-09-05
It wouldn't hurt to ck. what libdvdcss2 is doing.

To check, first put a dvd in the drive, let whatever happens, happen, and then go into home folder and delete **.dvdcss** (a hidden folder, if it's not there then you don't have libdvdcss2 installed

Then in terminal go 
```
export DVDCSS_VERBOSE=2
```
followed by either 
if you're using the default drive 

```
vlc dvd:// > css_output 2>&1

```

Otherwise do this and then open the disk from media -> open disc
```
vlc  > css_output 2>&1

```

After whatever happens look in home for a file - css_output and see what it says

(make sure you have deleted the .dvdcss folder before running above commands(s)


For a vlc debug go 
```
vlc -vv
```

---

### Post by cynicalcylon on 2009-09-05
> **cronholio said:**
> Umm, is that all? I mean, you should open VLC, open the messages window, try to play the DVD and **then** check the messages.

Ah right, sorry.

Well, VLC just closes itself down when I try to play the DVD in drive.

---

### Post by cynicalcylon on 2009-09-05
> **mc4man said:**
> It wouldn't hurt to ck. what libdvdcss2 is doing.

To check, first put a dvd in the drive, let whatever happens, happen, and then go into home folder and delete **.dvdcss** (a hidden folder, if it's not there then you don't have libdvdcss2 installed

Well, it appears that libdvdcss2 wasn't installed.
How odd, as I tried to do it earlier this morning.

> **mc4man said:**
> Then in terminal go 
```
export DVDCSS_VERBOSE=2
```followed by either 
if you're using the default drive 

```
vlc dvd:// > css_output 2>&1

```Otherwise do this and then open the disk from media -> open disc
```
vlc  > css_output 2>&1

```After whatever happens look in home for a file - css_output and see what it says

(make sure you have deleted the .dvdcss folder before running above commands(s)

I got the following:

> VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3.2' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "en_GB"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
vlc: /build/buildd/libdvdnav-4.1.2/src/vm/vm.c:1485: process_command: Assertion `0' failed.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: TWILIGHT_DISC1
libdvdnav: DVD Serial Number: 499C6EF9___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/taz/.dvdnav/TWILIGHT_DISC1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2
libdvdnav: ifoOpenVTSI failed

---

### Post by SunnyRabbiera on 2009-09-05
Hmm, i suggest you try totem xine, and remove totem-gstreamer.

---

### Post by rockstarrem on 2009-09-05
This may be stupid, but I'd try installing mplayer just to see what happens. You probably already did, but if not...

```

sudo apt-get install mplayer

```

---

### Post by mc4man on 2009-09-05
Totem-xine would be a good comparison choice as it uses it's own version of dvdnav.

Your css output showed no use of libdvdcss2 , if totem-xine fails then maybe check and see if the drive has a region set, in your case 2.

( sudo apt-get install regionset
With a disc in drive run regionset from terminal and check the line Type:
it should say 'set'

---

### Post by cynicalcylon on 2009-09-05
> **mc4man said:**
> Totem-xine would be a good comparison choice as it uses it's own version of dvdnav.

Your css output showed no use of libdvdcss2 , if totem-xine fails then maybe check and see if the drive has a region set, in your case 2.

( sudo apt-get install regionset
With a disc in drive run regionset from terminal and check the line Type:
it should say 'set'

I get the following:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
regionset is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Also, now when I try to open DVD with totem (either version) I get the following:

> The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

---

### Post by cynicalcylon on 2009-10-02
*Bump*

I haven't had internet access the past couple of weeks, so haven't been able to get online to sort this problem.

I don't have libdvdcss installed as it won't let me install it.

Any help?

---

