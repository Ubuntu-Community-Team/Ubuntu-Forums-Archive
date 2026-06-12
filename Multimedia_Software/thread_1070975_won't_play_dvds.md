---
title: "won't play dvds"
date: 2009-02-15
forum: Multimedia Software
---

### Post by systemshock869 on 2009-02-15
Totem says "Could not open location; you might not have permission to open the file."

In VLC a blank movie window pops up, then disappears.

Mplayer freezes for a while, then says "Fatal Error! | Error opening/initializing the selected video_out (-vo) device."

The computer does recognize that it's a dvd.  The correct codecs are installed, and it shows youtube videos fine.

---

### Post by mc4man on 2009-02-15
The 'usual' suspects are,

do you libdvdcss2 installed?

you may need to change video output from 'default' (usually Xv) to X11

some drives and disc combo's will require a region to set set on the drive, do you know if one is? (if commercial dvd's were ever played on windows then it would have been.

For 8.10
Try starting vlc from a terminal -> media -> open disc to ck. errors

this will give extra (maybe too much) info

```
vlc -vv
```

or to get libdvdcss2 info included (2 separate commands, look in home folder for text file vlc_output

```
export DVDCSS_VERBOSE=2
```
followed by one of the below

```
 vlc > vlc_output 2>&1
```

or an 'all in one'

```
vlc -vv > vlc_output 2>&1
```

---

### Post by systemshock869 on 2009-02-16
ok i typed vlc -vv ..here's the output i get when i to open a disc:
```
[00000405] qt4 interface debug: New item: dvd:///dev/scd0
[00000371] main playlist debug: adding item `dvd:///dev/scd0' ( dvd:///dev/scd0 )
[00000371] main playlist debug: rebuilding array of current - root Playlist
[00000371] main playlist debug: rebuild done - 1 items, index -1
[00000371] main playlist debug: starting new item
[00000371] main playlist debug: processing request item dvd:///dev/scd0 node null skip 0
[00000371] main playlist debug: resyncing on dvd:///dev/scd0
[00000371] main playlist debug: dvd:///dev/scd0 is at 0
[00000371] main playlist debug: creating new input thread
[00000409] main input debug: Creating an input for 'dvd:///dev/scd0'
[00000409] main input debug: thread started
[00000409] main input debug: waiting for thread initialization
[00000409] main input debug: `dvd:///dev/scd0' gives access `dvd' demux `' path `/dev/scd0'
[00000409] main input debug: creating demux: access='dvd' demux='' path='/dev/scd0'
[00000410] main demux debug: looking for access_demux module: 2 candidates
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
[00000409] main input debug: thread 2957998992 (input) created at priority 10 (input/input.c:370)
[00000405] qt4 interface debug: Updating the stream status: 3
libdvdnav: DVD Title: SPEED_RACER
libdvdnav: DVD Serial Number: 38E25AFB
libdvdnav: DVD Title (Alternative): SPEED_RACER
libdvdnav: Unable to find map file '/home/chris/.dvdnav/SPEED_RACER.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4
libdvdnav: Suspected RCE Region Protection!!!
```

then the computer slows WAY down.. the mouse jumps around and is really laggy.. this lasts like a minute or so.. seems like forever, then it prints this:

```
[00000410] dvdnav demux debug: trying to go to dvd menu
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
libdvdnav: Language 'en' not found, using '&#65533;&#65533;' instead
libdvdnav: Menu Languages available: &#65533;&#65533; 
[00000412] main generic debug: thread started
[00000412] main generic debug: thread 2949307280 (dvdnav event thread handler) created at priority 0 (dvdnav.c:351)
[00000410] main demux debug: using access_demux module "dvdnav"
[00000410] main demux debug: TIMER module_Need() : 167713.833 ms - Total 167713.833 ms / 1 intvls (Avg 167713.825 ms)
[00000409] main input debug: `dvd:///dev/scd0' successfully opened
[00000410] dvdnav demux debug: DVDNAV_HOP_CHANNEL
[00000409] main input debug: control type=1
[00000410] dvdnav demux debug: DVDNAV_VTS_CHANGE
[00000410] dvdnav demux debug:      - vtsN=1
[00000410] dvdnav demux debug:      - domain=8
[00000410] dvdnav demux debug: DVDNAV_CELL_CHANGE
[00000410] dvdnav demux debug:      - cellN=1
[00000410] dvdnav demux debug:      - pgN=1
[00000410] dvdnav demux debug:      - cell_length=3399000
[00000410] dvdnav demux debug:      - pg_length=3399000
[00000410] dvdnav demux debug:      - pgc_length=3399000
[00000410] dvdnav demux debug:      - cell_start=0
[00000410] dvdnav demux debug:      - pg_start=0
[00000410] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE
[00000410] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE
[00000410] dvdnav demux debug:      - physical_wide=0
[00000410] dvdnav demux debug:      - physical_letterbox=0
[00000410] dvdnav demux debug:      - physical_pan_scan=1
[00000410] dvdnav demux debug: buttonUpdate not done b=1 t=0
[00000409] main input debug: selecting program id=0
[00000413] main decoder debug: looking for decoder module: 30 candidates
[00000405] qt4 interface debug: New Event: type 1103
[00000405] qt4 interface debug: Updating the stream status: 3
[00000405] qt4 interface debug: New Event: type 1108
[00000413] main decoder debug: using decoder module "spudec"
[00000413] main decoder debug: TIMER module_Need() : 5301.445 ms - Total 5301.445 ms / 1 intvls (Avg 5301.445 ms)
[00000413] main decoder debug: thread started
[00000413] main decoder debug: thread 2929810320 (decoder) created at priority 0 (input/decoder.c:217)
[00000410] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE
[00000410] dvdnav demux debug:      - physical=0
[00000410] dvdnav demux warning: cannot get next block (Error reading NAV packet.)
[00000410] dvdnav demux debug: jumping to first title
[00000410] dvdnav demux debug: DVDNAV_HOP_CHANNEL
[00000410] dvdnav demux debug: DVDNAV_VTS_CHANGE
[00000410] dvdnav demux debug:      - vtsN=1
[00000410] dvdnav demux debug:      - domain=2
[00000413] main decoder debug: removing module "spudec"
[00000413] main decoder debug: thread ended
[00000413] main decoder debug: thread 2929810320 joined (input/decoder.c:248)
[00000413] main decoder debug: killing decoder fourcc `spu ', 0 PES in FIFO
[00000409] main input debug: Program doesn't contain anymore ES
[00000410] dvdnav demux debug: DVDNAV_CELL_CHANGE
[00000410] dvdnav demux debug:      - cellN=1
[00000410] dvdnav demux debug:      - pgN=1
[00000410] dvdnav demux debug:      - cell_length=36000
[00000410] dvdnav demux debug:      - pg_length=24105000
[00000410] dvdnav demux debug:      - pgc_length=728691000
[00000410] dvdnav demux debug:      - cell_start=0
[00000410] dvdnav demux debug:      - pg_start=0
[00000410] dvdnav demux debug: DVDNAV_SPU_CLUT_CHANGE
[00000410] dvdnav demux debug: DVDNAV_SPU_STREAM_CHANGE
[00000410] dvdnav demux debug:      - physical_wide=128
[00000410] dvdnav demux debug:      - physical_letterbox=129
[00000410] dvdnav demux debug:      - physical_pan_scan=128
[00000410] dvdnav demux debug: buttonUpdate not done b=1 t=1
[00000410] dvdnav demux debug: DVDNAV_AUDIO_STREAM_CHANGE
[00000410] dvdnav demux debug:      - physical=0
[00000410] dvdnav demux warning: cannot get next block (Error reading NAV packet.)
[00000371] main playlist debug: finished input
[00000371] main playlist debug: dying input
[00000405] qt4 interface debug: Updating the stream status: 8
[00000371] main playlist debug: dying input
[00000371] main playlist debug: dying input
[00000412] main generic debug: thread ended
[00000412] main generic debug: thread 2949307280 joined (dvdnav.c:367)
[00000409] main input debug: Program doesn't contain anymore ES
[00000410] main demux debug: removing module "dvdnav"
[00000409] main input debug: thread ended
[00000371] main playlist debug: dead input
[00000409] main input debug: thread 2957998992 joined (playlist/engine.c:244)
[00000409] main input debug: TIMER input launching for 'dvd:///dev/scd0' : 168447.435 ms - Total 168447.435 ms / 1 intvls (Avg 168447.427 ms)
[00000371] main playlist debug: starting new item
[00000371] main playlist debug: changing item without a request (current 0/1)
[00000371] main playlist debug: nothing to play
```

then i accidentally hit ctrl-c to copy the code and it exited the program and outputted a bunch more crap.. still getting used to linux haha

---

### Post by mc4man on 2009-02-16
The new vlc and libdvdnav combo certainly out put more than's needed for error's. Do you know whether a region has been set on the drive?
If not sure about region setting install regionset and with a **dvd in the drive** run regionset from the terminal
Ex. of set drive

> doug@doug-desktop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET [COLOR="Red"]<-[/COLOR]
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:n 

If type:none then answer y and set to **your region**

Try the libdvdcss output command to text file also

1st.
```
export DVDCSS_VERBOSE=2

```

Then ( then look in home folder for file
```
 vlc > vlc_output 2>&1

```

---

### Post by systemshock869 on 2009-02-17
region is set to region 1..
here are the contents of vlc_output:
```
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: DVD Title: SPEED_RACER
libdvdnav: DVD Serial Number: 38E25AFB
libdvdnav: DVD Title (Alternative): SPEED_RACER
libdvdnav: Unable to find map file '/home/chris/.dvdnav/SPEED_RACER.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Language 'en' not found, using 'ÿÿ' instead
libdvdnav: Menu Languages available: ÿÿ 
libdvdnav: Language 'en' not found, using 'ÿÿ' instead
libdvdnav: Menu Languages available: ÿÿ 
libdvdnav: Language 'en' not found, using 'ÿÿ' instead
libdvdnav: Menu Languages available: ÿÿ 
```

I have no idea what all that means.

Thanks alot by the way guys

---

### Post by systemshock869 on 2009-02-18
bump!

---

### Post by Bablefish on 2009-02-18
Since I have been through this, I guess I am the best one to help. But I have a couple of questions.

Do you have Medibuntu installed?

Do you have restricted extras installed?

Do have any of the GStreamer packages installed?

Have you opened the DVD and clicked on one of the VOB files and do they play on VLC?

If you done these and still nothing works try installing Automatrix, that should do the trick.

---

### Post by systemshock869 on 2009-02-18
hey it works great now! thanks alot man.  i think the medibuntu did the trick.

seems like that was a lot of work to just do a simple task like play a dvd though.

---

### Post by systemshock869 on 2009-02-18
totem and mplayer still don't work.. vlc works though.  i'll just get rid of the other ones.

---

