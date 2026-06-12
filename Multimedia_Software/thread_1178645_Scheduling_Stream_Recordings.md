---
title: "Scheduling Stream Recordings"
date: 2009-06-04
forum: Multimedia Software
---

### Post by mastermindg on 2009-06-04
Does anybody know of an application or batch script that allows scheduling recording of radio streams, like shoutcast or livefm? 

I could script it and put it against cron but if there's a solution out there I'd rather check that out first.

---

### Post by andrew.46 on 2009-06-04
Hi mastermindg,

> **mastermindg said:**
> Does anybody know of an application or batch script that allows scheduling recording of radio streams, like shoutcast or livefm? 

I could script it and put it against cron but if there's a solution out there I'd rather check that out first.

Well, I routinely record a live radio broadcast using cron and a script that works beautifully. Perhaps you could use some parts of:

Slackware and "For The God Who Sings"
[http://www.andrews-corner.org/ftgws.html](http://www.andrews-corner.org/ftgws.html)

Just ignore all the slackware stuff :-).

Andrew

---

### Post by g1pete on 2009-06-04
You might want to look at **StreamTuned**

[http://home.kabelfoon.nl/~moongies/streamtuned.html]("http://home.kabelfoon.nl/%7Emoongies/streamtuned.html")

this will allow you to play and record streams and podcasts.
I did not try it yet, using MythStram for myself.

Pete

---

### Post by mastermindg on 2009-06-05
I'd like to save a stream using VLC. I'm running 0.9.9a and when I try this:

vlc -ldummy --dummy-quiet [http://scfire-mtc-aa03.stream.aol.com:80/stream/1040](http://scfire-mtc-aa03.stream.aol.com:80/stream/1040) --run-time=60 --sout=#transcode{acodec=s16l,ab=128,channels=2}:duplicate{dst=display,dst=std{access=file,dst=/home/ken/test3.wav}}

I get the following output:

VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"

....and nothing else. The program gives debugging output and then ends without doing anything, no errors or anything. What am I missing?

---

### Post by mastermindg on 2009-06-05
I'm using the following command to test:

vlc -vvv -I dummy --sout '#transcode{acodec=s16l,ab=128,channels=2}:duplicate{dst=display,dst=std{access=file,dst=test2.wav}}' [http://scfire-mtc-aa03.stream.aol.com:80/stream/1040](http://scfire-mtc-aa03.stream.aol.com:80/stream/1040) --run-time=60 vlc://quit

and it's working great :p

However, I'd like to be able to record a stream without it actually playing the sound over the speakers, is this possible?

---

### Post by mastermindg on 2009-06-05
The following is a working bash script for recording streams in VLC:
```

#!/bin/sh

#Variables:

DATE1=$(date +%d%m%Y)
DATE2=$(date +"%d-%m-%Y")
STREAM=http://scfire-mtc-aa03.stream.aol.com:80/stream/1040
DURATION=750
MUSIC_DIR=/share/music/ripped

cd $MUSIC_DIR

# Download the stream and convert it to wave format:

vlc -vvv -I dummy --sout '#transcode{acodec=s16l,ab=128,channels=2}:duplicate{dst=display,dst=std{access=file,dst=80s_rip.wav}}' $STREAM --run-time=$DURATION vlc://quit

# Convert to MP3:

lame -V2 /share/music/ripped/80s_rip.wav /share/music/ripped/80s_rip_$DATE1.mp3

# Setup ID3 tags:

mp3info 80s_rip_$DATE1.mp3 -t ".977 The 80's Channel" -l ".977 80's Live Streams" -a ".977" -c "Encoded with Lame"

# Clean up:

rm 80s_rip.wav
```

I use the following crontab, set to record everyday at 6:30 PM:

```
30 18 * * * /home/me/vlc_80s.sh > /home/me/rip.log 2>&1
```

---

### Post by andrew.46 on 2009-06-05
Hi mastermindg,

It is good to see someone working the whole thing basically on their own :-).

Andrew

---

