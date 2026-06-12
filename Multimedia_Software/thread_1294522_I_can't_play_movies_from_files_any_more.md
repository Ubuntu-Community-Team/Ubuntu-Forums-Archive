---
title: "I can't play movies from files any more"
date: 2009-10-18
forum: Multimedia Software
---

### Post by rhythmiccycle on 2009-10-18
I don't know why, but one day...

when I open a movie file, (avi, mpeg) The player opens up and then just quits with out playing anything. it did this in VLC and the defult movie player

(i'm using ubuntu 9)

i tried unstalling the movie players and then reinstalling VLC, but I still have the same problem. 

I can stream movies from webpages, but I cannot play movie files.

Everything used to work, and then one day it stopped. 

what do I do?

---

### Post by solitaire on 2009-10-18
try using the terminal to start a movie.
I'm assuming your videos are held in ~/Videos
goto: Applications / Accessories / Terminal
then type in the black window and type:```

cd ~/Videos
vlc <the-video-you-want-to-play.avi>
```

You should see any error messages.

---

### Post by issih on 2009-10-18
One possibility that I have had issues with..

Are you running lots of visual effects using a relatively weak video card, specifically in terms of vram size?

Using a 128Meg nvidia 6800 I find that I can run the blur plugin and have a usable desktop, but video players run out of vram when loading the file and close exactly as you are describing.

Can't really definitively tell from what you've said if this is your issue, but its worth checking.

try dropping into metacity by running:

```
metacity --replace
```

in a terminal and then see if the video's will play, if so, then you have a compiz issue.

```
compiz --replace
```

will turn your effects back on.

Hope that helps

---

### Post by rhythmiccycle on 2009-10-18
> **solitaire said:**
> try using the terminal to start a movie.
I'm assuming your videos are held in ~/Videos
goto: Applications / Accessories / Terminal
then type in the black window and type:```

cd ~/Videos
vlc <the-video-you-want-to-play.avi>
```

You should see any error messages.


this is what comes out

```

VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82


```

---

### Post by rhythmiccycle on 2009-10-18
> **issih said:**
> 
Are you running lots of visual effects using a relatively weak video card, specifically in terms of vram size?


no. I have no visual effects, I don't even know anything about visual effects. sometimes I run dual monitors, does that count?


I tried playing movies with everything closed (with out dual monitors), and its not working. 

Like i said, it was working before, and then it just stopped.

the only thing I can think of that happed around the time it stopped working, was that I has some resolution issues, and i was messing with that. I got the resolution to go back to normal. That might have something to do with the problem.

---

### Post by andrew.46 on 2009-10-18
Hi rhythmccycle,

> **rhythmiccycle said:**
> when I open a movie file, (avi, mpeg) The player opens up and then just quits with out playing anything. it did this in VLC and the defult movie player

This will usually happen if the default 'video out' is inappropriate for your display. Try changing the video out device under vlc to something like x11 by accessing: Tools --> Preferences --> Video --> Display --> Output.

All the best,

Andrew

---

### Post by rhythmiccycle on 2009-10-25
> **andrew.46 said:**
> 
 Try changing the video out device under vlc to something like x11 by accessing: Tools --> Preferences --> Video --> Display --> Output.


That worked, thanks alot.

simple yet effective

---

### Post by chuchi on 2009-11-22
Hello friends! First of all I want to apologize because my english is not very good. Well, I have a similar problem as rhythmiccycle. I can't play any movies (.avi, .mpg, .wmv) with any reproductor. I try with VLC "Tools --> Preferences --> Video --> Display --> Output" that saids andrew.46 and i can see movies, but with a very very bad quality and the films stopped very times. Please help!!!!!

Many thanks!!

---

### Post by rhythmiccycle on 2009-11-25
did you try all the different "video out devices"?

what one are you using now?

---

