---
title: "Media players closing when started"
date: 2009-04-01
forum: Multimedia Software
---

### Post by Mehashi on 2009-04-01
[COLOR=Magenta]Hey Guys[/COLOR]!

I have encountered a problem on my second system when attempting to play media. 
It goes like this:

I double click 'robot_chicken_01.avi' (as standard I use the movie player).
Movie player opens.
Movie player closes.

OR

I right click and 'open with vlc media player'
Vlc opens and I hear the first second or so of sound but no picture.
Vlc then closes.

I have never had problems in any ubuntu before with media playback (on many systems) so I am a little suprised and confused! I realise I have probably overlooked something setting it up, although I have downloaded all appropriate drivers. I tried moving the files off my NTFS drive onto my desktop but still no luck (thought it may have been an NTFS issue I have had before).

Any help would be appreciated as the sticky I read was hard to follow and did not seem to cover this issue!

[COLOR=Magenta]Thanks guys[/COLOR]!
^_^

---

### Post by aeiah on 2009-04-01
open a terminal and navigate to where your video is then do 
```
mplayer robot_chicken_01.avi
```

the output should tell you what's wrong

---

### Post by Mehashi on 2009-04-01
[COLOR=Magenta]Ok[/COLOR]! 
Sorry I had to attend a class, but I now have the output from terminal.

```
mehashi@mehashi-noxious:~/RobotChicken_2$ vlc RCS2E4.avi
VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3.1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  84
  Current serial number in output stream:  85
mehashi@mehashi-noxious:~/RobotChicken_2$ desu ka?
 
```This computer has 1.5G of ram so resources should not be a problem?
(It is ubuntu 8.10 - also on my main computer with no problems)

[COLOR=Magenta]Thank you for help[/COLOR]!

-Edit-
I guess this is to do with x-org? If it is I have never edited it before so may need a pointer.

---

### Post by andrew.46 on 2009-04-01
Hi,

I am not much of a vlc user but I suspect you could address this error:

```
[????????] **[COLOR="Red"]x11 video output error:[/COLOR]** X11 request 140.19 failed with error code 11:

```

by altering the video output settings under Tools ---> Preferences ----> Video to something like 'Xvideo Extension video output'. I add a screenshot to show what I mean.

All the best,

Andrew

---

### Post by Mehashi on 2009-04-01
Thanks, I will try that when I get home, I am at work at the moment!

---

