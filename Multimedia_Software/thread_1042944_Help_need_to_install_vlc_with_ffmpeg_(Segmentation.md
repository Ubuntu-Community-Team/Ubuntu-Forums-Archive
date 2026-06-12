---
title: "Help need to install vlc with ffmpeg (Segmentation Fault)"
date: 2009-01-18
forum: Multimedia Software
---

### Post by running7 on 2009-01-18
Hi,

I have  been trying to install the latest version of vlc with the libraries provided in ffmpeg (latest package 2009-01-12).

FFMpeg configuration:
FFmpeg version SVN-r16564, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: 
  libavutil     49.12. 0 / 49.12. 0
  libavcodec    52.10. 0 / 52.10. 0
  libavformat   52.23. 1 / 52.23. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  built on Jan 18 2009 13:12:06, gcc: 4.3.2

Then i installed vlc.
VLC Configuration:
[00000001] main libvlc debug: VLC media player - version 0.9.8a Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--prefix=/usr' '--with-ffmpeg-tree=/home/rajesh/Desktop/ffmpeg-export-2009-01-12' '-libdir=/usr/lib'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.

The problem is this: When i try to run any videos (there is no problem with audio files) with vlc i am getting 'SEGMENTATION FAULT'. I am stuck at this point for the past 3 days.

Any help in this regard is  greatly appreciated

(I need to install vlc with the libraries provided by ffmpeg. So if anyone can tell me how to go about doing that or redirect to some other post that will also suffice.)

rajesh

---

### Post by mc4man on 2009-01-18
I took my source of 0.9.8a, cleaned it, built ffmpeg in /extras and added the -with-ffmpeg-tree= to the config.
Now while it configured, made and runs fine a close look at the configure shows the ffmpeg option is being ignored

> configure: WARNING: --with-ffmpeg-tree is deprecated. Use PKG_CONFIG_PATH instead.


For ref. 
This is what I used last time (I have a fairly recent ffmpeg installed


> ./configure --enable-libtool --enable-fast-install --disable-fb --enable-ggi --enable-esd   --enable-jack  --enable-lirc --enable-aa  --enable-mozilla --with-mozilla-pkg=libxul-plugin --disable-kde --enable-mp4  --disable-satellite  --enable-shout  --enable-flac --disable-skins --disable-basic-skins --enable-skins2  --disable-speex --enable-caca  --enable-theora  --disable-mpc --enable-vcdx --enable-twolame --disable-zvbi  --disable-atmo --enable-libass --enable-libdca --enable-real --enable-realrtsp --enable-faad  --enable-static --enable-x264 --with-x264-tree=./extras/x264-trunk --enable-live555 --with-live555-tree=./extras/live --enable-cddax 

---

### Post by Blastz on 2009-03-08
I had a problem with vlc and found a posting which advised deleting the config directory. This did not work for me but, based on it, I used this command in the terminal which did:

I tested it first with 

vlc  --ignore-config

and when that worked 

vlc --reset-config

Hope this helps someone.

---

