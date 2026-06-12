---
title: "Can't play video"
date: 2009-04-19
forum: Multimedia Software
---

### Post by simcalame on 2009-04-19
Hi,

I'm 1 week into the ubuntu experience and mostly things have worked really well...

I've loaded VLC and I can play audio files (MP4 etc..) but I can't play .avi or dvd.  The issue is when I select a video file the VLC application opens, then closes really quickly and doesn't play the file.  The same issue is encoutered when I try opening a video file using MPLAYER, TOTEM.  The output when I run VLC is:  

simon@laptop:~$ vlc
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3.1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"

hope someone can help. 

Cheers, S

---

### Post by inobe on 2009-04-19
welcome to the ubuntu forums.

we can try one of two things or both.

first open terminal and type

```
sudo apt-get install ubuntu-restricted-extras
```

hit enter, this will install various codecs and flash.

if your dvd playback still ends up not working or it only works with certain dvd's, you will need to add medibuntu repository to synaptic.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

check the laws in your country, patent laws operate differently depending on the country you live in.

---

### Post by simcalame on 2009-04-19
Thanks for the info...have tried both solutions but still no luck.

---

### Post by inobe on 2009-04-19
see if it works with movie player/ totem.

honestly i use xine player, in fact i have it setup as a system backend so basically it's the only player i use, that and the mozzilla plugin are exceptional tools.


you will even be able to watch streaming video from firefox.

---

### Post by simcalame on 2009-04-19
Thanks Inobe - I'll give xine a try as neither totem or mplayer seem to work!   Cheers - S

---

### Post by simcalame on 2009-04-19
I must be missing something here!  As soon as I open xine from applications-> it opens and closes just like vlc and mplayer, totem etc...

I'm using ubuntu 8.10 should i be re-installing the operating system?

---

### Post by simcalame on 2009-04-19
Here's the output from terminal 

This is xine (X11 gui) - a free video player v0.99.6cvs.
(c) 2000-2007 The xine Team.
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  2539
  Current serial number in output stream:  2540

---

### Post by inobe on 2009-04-19
looks as if there is major corruption or possibly a lot of broken packages.

try opening synaptic and clicking **edit** then selecting **fix broken packages.**

---

### Post by simcalame on 2009-04-19
i tried that but no packages seem to be repaired - the process finished in about half a second...:)

---

### Post by inobe on 2009-04-19
then it must be some sort of video rendering issue.

what graphics card do you have and is the driver enabled in "hardware drivers"

include your system specs.

---

### Post by simcalame on 2009-04-19
I don't appear to be able to activate the hardware driver ati/amd proporietary fglrx graphics card

I'm using a Dell 6400 inspiron intel core duo 1.83gHz (T2400), 100G HDD, with 1024mb DDR2 SDRAM,256 ATI mobility Radeon x1400

Thanks for your help with this...

---

### Post by simcalame on 2009-04-19
in the end I got VLC working by installing xorg.driver.fglrx

thanks Inobe I appreciate all your help with this!

Cheers - S ;)

---

