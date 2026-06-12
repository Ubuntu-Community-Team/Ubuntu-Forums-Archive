---
title: "another totem dvd problem"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by vector on 2007-09-03
HI all
I asked this on PPC user forum but got no responses at all. Im trying my best, Im not trying to waste peoples time. Im off on holidays soon and really really want this laptop to play dvds for my kids on the long drive. I have followed links, and pretty sure and double checked I have done the right thing.

If anyone is willing to hold my hand and just get me to interrogate or try things Id really appreciate it. Im sure its a simple hurdle.
..................

Problems with dvd play on Pismo under ubutnu 6.06 on a Pismo G3.
totem, vlc, mplayer, tried and failed.
I possibly wont have the space to just load everything like in a automatix or easybuntu.
ANy help on purging the hd for space is also welcomed.

Following is a list of things I have done or at least remember doing. I am new and generally get out of trouble by apt installing things mentioned on posts, till it works. But this time it hasnt worked and I have run out of ideas.

Machine History.
This machine, Pismo powerbook G3, was given to me with ubuntu already loaded. Most of it is working. Mp3 playback, wireless etc etc. *added(wont play mpegvideo file either)*

Space difficulty.
I have a lack of disk space. Its an 18gig hd. partitioned and running 97% full on root. So everything I load continues to cause me problems with space. I often have to remove it in order to make space for other things or another attempt.

Problem
totem wont play DVDs.
Reported error on insertion of dvd.
Totem could not play dvd:///media/cdrom-1
No URI handler implemented for "dvd".

which sounds like a codec probelm?


Sources .list
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) dapper free non-free

Things tried.
added medibuntu to sources. Installed libdvdcss2
could not install ppc-codecs tho. no package found.

remove install totem..no difference.
install totem-xine...caused some graphic display issues. going yellow not running etc.

VLC installed... could not work out how to point VLC to dvd device. user error?
mplayer installed ... could not work out how to point to dvd..user error?

dpkg -l *libdvd*
un libdvdcss <none> (no description available)
un libdvdcss0.0.1 <none> (no description available)
un libdvdcss0.0.2 <none> (no description available)
ii libdvdcss2 1.2.9-2medibun Library for accessing DVDs like block device
ii libdvdnav4 0.1.9-3 The DVD navigation library
un libdvdread-dev <none> (no description available)
un libdvdread1 <none> (no description available)
un libdvdread2-de <none> (no description available)
ii libdvdread3 0.9.4-5.1 Simple foundation for reading DVDs
ii libdvdread3-de 0.9.4-5.1 Simple foundation for reading DVDs



dpkg -l *gstream*
ii gstreamer0.10- 0.10.7-0ubuntu GStreamer plugin for ALSA
un gstreamer0.10- <none> (no description available)
un gstreamer0.10- <none> (no description available)
ii gstreamer0.10- 0.10.3-0ubuntu GStreamer plugin for ESD
un gstreamer0.10- <none> (no description available)
ii gstreamer0.10- 0.10.2.debian- Fluendo mp3 decoder GStreamer plugin
ii gstreamer0.10- 0.10.7-0ubuntu GStreamer plugin for GnomeVFS
un gstreamer0.10- <none> (no description available)
un gstreamer0.10- <none> (no description available)
ii gstreamer0.10- 0.10.7-0ubuntu GStreamer plugins from the "base" set
ii gstreamer0.10- 0.10.7-0ubuntu GStreamer helper programs from the "base" se
ii gstreamer0.10- 0.10.3-0ubuntu GStreamer plugins from the "good" set
un gstreamer0.10- <none> (no description available)
ii gstreamer0.10- 0.10.6-0ubuntu Tools for use with GStreamer
un gstreamer0.10- <none> (no description available)
ii gstreamer0.10- 0.10.7-0ubuntu GStreamer plugins for X11 and Pango
ii gstreamer0.8-a 0.8.12-1ubuntu ALSA plugin for GStreamer
ii gstreamer0.8-a 0.8.12-1ubuntu AudioFile plugin for GStreamer
un gstreamer0.8-a <none> (no description available)
ii gstreamer0.8-c 0.8.12-1ubuntu cdparanoia plugin for GStreamer
un gstreamer0.8-c <none> (no description available)
ii gstreamer0.8-d 0.8.12-1ubuntu DV plugin for GStreamer
ii gstreamer0.8-d 0.8.12-1ubuntu DVD plugin for GStreamer
ii gstreamer0.8-e 0.8.12-1ubuntu Enlightened Sound Daemon plugin for GStreame
ii gstreamer0.8-f 0.8.12-1ubuntu FLAC plugin for GStreamer
ii gstreamer0.8-g 0.8.12-1ubuntu Gnome VFS plugin for GStreamer
ii gstreamer0.8-g 0.8.12-1ubuntu GSM plugin for GStreamer
ii gstreamer0.8-h 0.8.12-1ubuntu colorspace conversion plugin for GStreamer b
ii gstreamer0.8-j 0.8.12-1ubuntu JPEG plugin for GStreamer
ii gstreamer0.8-m 0.8.12-1ubuntu Collection of various GStreamer plugins
ii gstreamer0.8-m 0.8.12-1ubuntu Musepack (MPC) audio decoder plugin for GStr
ii gstreamer0.8-o 0.8.12-1ubuntu OSS plugin for GStreamer
ii gstreamer0.8-p 0.8.12-1ubuntu Simple GStreamer applications
un gstreamer0.8-p <none> (no description available)
ii gstreamer0.8-s 0.8.12-1ubuntu SDL videosink plugin for GStreamer
ii gstreamer0.8-s 0.8.12-1ubuntu Speex plugin for GStreamer
ii gstreamer0.8-t 0.8.12-1ubuntu Theora plugin for GStreamer
ii gstreamer0.8-t 0.8.12-1ubuntu Tools for use with GStreamer
un gstreamer0.8-v <none> (no description available)
ii gstreamer0.8-v 0.8.12-1ubuntu Vorbis plugin for GStreamer
un gstreamer0.8-w <none> (no description available)
ii gstreamer0.8-x 0.8.12-1ubuntu X videosink plugin for GStreamer
ii libgstreamer-g 0.8.12-1ubuntu GConf support for GStreamer
ii libgstreamer-p 0.10.7-0ubuntu GStreamer libraries from the "base" set
ii libgstreamer-p 0.8.12-1ubuntu Various GStreamer libraries and library plug
ii libgstreamer0. 0.10.6-0ubuntu Core GStreamer libraries and elements
ii libgstreamer0. 0.8.12-1ubuntu Core GStreamer libraries, plugins, and utili
ii totem-gstreame 1.4.3-0ubuntu1 A simple media player for the Gnome desktop
un totem-gstreame <none> (no description available)

---

