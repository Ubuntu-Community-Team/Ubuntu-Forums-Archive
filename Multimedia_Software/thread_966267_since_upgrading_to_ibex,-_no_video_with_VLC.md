---
title: "since upgrading to ibex,- no video with VLC"
date: 2008-11-01
forum: Multimedia Software
---

### Post by daverich on 2008-11-01
this is a pain.

Just upgraded to Ibex, which is great- other than now VLC shows no video.

I get no video screen open, nor any video in the actual VLC window (not sure where it's supposed to be).

Mplayer works so does totem, so I'm pretty sure it's not a codec problem.

Any ideas?

Kind regards

Dave Rich

---

### Post by lexen on 2008-11-01
I am having the same problem, but with totem.  What video codec does the video use?  Almost all of mine use Xvid, so I think that is the problem with me.

   Have you installed any codecs onto your computer?


Best of luck,
Lexen

---

### Post by daverich on 2008-11-01
not recently,- but all the codecs seems to work with the other players.

What is odd,- is it seems like even stuff that should play anyway - like DV video, it's not showing.

Kind regards

Dave Rich

---

### Post by whoelse on 2008-11-01
Idiotic questions but someone has to ask them:

Have you activated video in the config?
What kind of output are you using?

I had some different problems with videos, deactivating all visual effects helped.

---

### Post by daverich on 2008-11-01
heya.

Not idiotic at all :)

Yes video output is activated.

I've tried

X11 output

Open GL output

with/without compositing

ubuntu/kubuntu

video acceleration on/off

nothing works.

I've got an intel GMA750 video chipset on board, which is normally pretty happy to play with anything.

Kind regards

Dave Rich

---

### Post by CPtAJ on 2008-11-03
I have the same problem. Everything was working fine until I finished all the software updates. I was using the previous vlc version that came with hardy heron in intrepid ibex and it worked fine. When it updated it to 0.9.4 in ibex the video stopped working. No output modules work.

Running on an nvidia 5700LE with no special effects enabled if that helps. Any ideas?

In the meantime, where can I find the previous packaged version of vlc? I went to their site and it just instructs you to use synaptic. I'm confident that downgrading will be a working temporary solution until someone figures out whats going on here.

---

### Post by CPtAJ on 2008-11-04
Scratch that. Try this:

```
vlc --reset-plugins-cache --reset-config
```

It should work after that. It did for me.
Source: [http://forum.videolan.org/viewtopic.php?f=13&t=49434](http://forum.videolan.org/viewtopic.php?f=13&t=49434)

---

### Post by directcharitycontribution on 2008-11-10
> **daverich said:**
> heya.

Not idiotic at all :)

Yes video output is activated.

I've tried

X11 output

Open GL output

with/without compositing

ubuntu/kubuntu

video acceleration on/off

nothing works.

I've got an intel GMA750 video chipset on board, which is normally pretty happy to play with anything.

Kind regards

Dave Rich

that's quick solution

---

### Post by daverich on 2008-11-10
> **CPtAJ said:**
> Scratch that. Try this:

```
vlc --reset-plugins-cache --reset-config
```

It should work after that. It did for me.
Source: [http://forum.videolan.org/viewtopic.php?f=13&t=49434](http://forum.videolan.org/viewtopic.php?f=13&t=49434)

YES!

beautiful - thanks :)

Kind regards

Dave Rich

---

### Post by Randy Winchester on 2008-12-08
> **CPtAJ said:**
> Scratch that. Try this:

```
vlc --reset-plugins-cache --reset-config
```

It should work after that. It did for me.
Source: [http://forum.videolan.org/viewtopic.php?f=13&t=49434](http://forum.videolan.org/viewtopic.php?f=13&t=49434)

Woohoo!  Works for me too!  

After upgrading, I couldn't even get a VLC window!  I could only run it from the command line, and then, I couldn't get video that way either, only audio.  Nice fix.

---

### Post by Badly Overdrawn Boy on 2008-12-08
Doesn't work for me. Since upgrading to Intrepid, neither VLC nor Totem will play any DVDs whatsoever :(

Here's what Terminal outputs as I've tried a few disks and the reset procedure above from CPtAJ

```
richard@prometheus:~$ vlc --reset-plugins-cache --reset-config
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "en_GB"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: DVD Title: THE_COMMITMENTS
libdvdnav: DVD Serial Number: 28A492F4
libdvdnav: DVD Title (Alternative): THE_COMMITMENTS
libdvdnav: Unable to find map file '/home/richard/.dvdnav/THE_COMMITMENTS.map'
libdvdread: Invalid main menu IFO (VIDEO_TS.IFO).
libdvdnav: vm: failed to read VIDEO_TS.IFO
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
[00000381] dvdread demux error: read failed for -1/4 blocks at 0x01
richard@prometheus:~$ vlc --reset-plugins-cache --reset-config
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "en_GB"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 4503DABF (GEAR):
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/richard/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: DVD Title: 
libdvdnav: DVD Serial Number: 4503DABF (GEAR):
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/richard/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[00000399] main decoder error: decoder is leaking pictures, resetting the heap
[00000400] main video output error: picture to date 0x9643a6c has invalid status 6
[00000400] main video output error: picture to display 0x9643a6c has invalid status 6
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
libdvdnav: Using dvdnav version 4.1.2 from http://dvd.sf.net
libdvdnav: DVD Title: SIN_CITY
libdvdnav: DVD Serial Number: 33038867
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/richard/.dvdnav/SIN_CITY.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1678 ***
*** for info_length % sizeof(uint32_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1678 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: ifoRead_TITLE_VOBU_ADMAP vtsi failed
[00000411] dvdnav demux error: cannot set title (can't decrypt DVD?)

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1678 ***
*** for info_length % sizeof(uint32_t) == 0 ***

[00000411] dvdread demux error: read failed for block 0
richard@prometheus:~$ 


```

EDIT: After following the instructions here-[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu") I am now able to watch DVDs using VLC, but not Totem. I'm not sure Totem warrants the title of 'movie player', I've never yet managed to play a movie with it!

---

### Post by euriconeto on 2009-04-09
Hi there,
I recently installed Jaunty and VLC doesn't go through DVD menus. The report is:
"main decoder error: decoder is leaking pictures, resetting heap"

Have been to all sorts of threads and tried fairly any solution for similar cases... nothing sorted so far.

Any help?

Cheers,
Eurico

---

