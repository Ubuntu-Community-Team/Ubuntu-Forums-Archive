---
title: "Permissions error for watching DVD!!"
date: 2010-08-12
forum: Multimedia Software
---

### Post by Bondy_uk on 2010-08-12
Hi,

Can someone help me please.

For some reason ive just started getting a permissions error while trying to watch a shop bought DVD (granted I havent watched any for a while on my PC). So is this a bug with a later kernel or something?

Ive searched + searched, ive followed some previous advice given, yet nothing seems to work. The error messages have changed (all based around permissions) and its gone from not playing at all to playing the first few minutes then throwing up the error.

I cant remember half the pages/advice I have previously tried following, so here are a few links to give you an idea.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[http://ubuntuforums.org/showthread.php?t=845995](http://ubuntuforums.org/showthread.php?t=845995)
[http://ubuntuforums.org/showpost.php?p=7197110&postcount=5](http://ubuntuforums.org/showpost.php?p=7197110&postcount=5)
[http://ubuntuforums.org/showthread.php?t=1142055](http://ubuntuforums.org/showthread.php?t=1142055)

etc, etc.

Im running (Ubuntu) 9.04 64bit, VLC & Xine.


Please can someone help, its driving me crazy!!

Thanks :)

---

### Post by mouths on 2010-08-12
libdvdread4 ?

---

### Post by Bondy_uk on 2010-08-12
Thanks for the reply.

Yes thats installed. In fact I completely removed it and installed it again to see if it made a difference.


Anything else I can try?

---

### Post by cchhrriiss121212 on 2010-08-13
Firstly have you tried just one DVD or lots of them?
Try opening vlc in a terminal and playing the DVD, then post any output you are getting.

---

### Post by Bondy_uk on 2010-08-13
Ok that didnt occur to me :-\"

So I decided to try the other DVD's in the box-set (its a 6 DVD TV series box-set). Every other DVD works fine, except the first one!!
I cant change episodes or anything.

I then tried opening vlc in terminal and it didnt work. This is what I got if it helps...

```
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "en_GB"
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title: SG1_VOL32_D1
libdvdnav: DVD Serial Number: 2f4d5b00
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/ian/.dvdnav/SG1_VOL32_D1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012e
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00000745
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x0000f5f4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x002dfcbe
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002eae4a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002ec119
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
libdvdnav: RANDOM or SHUFFLE titles are NOT handled yet.
[00000470] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:224000
[00000496] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000

```

---

### Post by cchhrriiss121212 on 2010-08-14
Is that all the output you get? I ask because it doesn't seem to show any clear error messages.
You could try using regionset to set your region, linux systems will disregard any region restrictions but sometimes you get problems when your region is left unspecified.

---

### Post by Bondy_uk on 2010-08-14
> **cchhrriiss121212 said:**
> Is that all the output you get? I ask because it doesn't seem to show any clear error messages.
You could try using regionset to set your region, linux systems will disregard any region restrictions but sometimes you get problems when your region is left unspecified.

Yes thats all the output I get.

I am going to look up how to use regionset.

Isnt it strange though that its only the 1st dvd and all others from the same boxset play fine?

---

### Post by Bondy_uk on 2010-08-14
Ok so regionset outputs this:

> regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
user controlled changes resets available: 4
drive plays discs from region(s): 2, mask=0xFD

Would you like to change the region setting of your drive? [y/n]:


Im in region 2 so surely I dont want to be messing with this?

---

### Post by cchhrriiss121212 on 2010-08-14
Your regionset looks fine so you can scratch that idea. Does the problem disc play in a regular dvd player or windows pc? 
Your first post mentions a permissions error, what did that say?

---

