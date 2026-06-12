---
title: "Not able to rip DVD's"
date: 2010-05-28
forum: Multimedia Software
---

### Post by argedion on 2010-05-28
I have been trying to rip a DVD for the past few days. I have Ubuntu 9.10 installed and updated. I have Ubuntu Restricted formats installed. I have installed everything I can think of and have checked the forums and installed stuff I'm not even sure about. I have run the following command:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```
from the following article [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Things installed with no errors. I use dvd rip and it just hangs and gives me errors. When I ran dvdrip from a command line I get the following:

```
argedion@Littious:~$ dvdrip
GLib-CRITICAL **: g_bookmark_file_load_from_data: assertion `length != 0' failed at /usr/share/perl5/Video/DVDRip/GUI/Base.pm line 96.
```

The program gets to a certain point and stops. Here is a screen shot
[ATTACH]158518[/ATTACH]

When I close the program Terminal shows me this information:
```
Gtk-WARNING **: Attempting to store changes into `/home/argedion/.recently-used.xbel', but failed: Failed to rename file '/home/argedion/.recently-used.xbel.FDTTCV' to '/home/argedion/.recently-used.xbel': g_rename() failed: Operation not permitted at /usr/share/perl5/Video/DVDRip/GUI/Main.pm line 205.
Gtk-WARNING **: Attempting to set the permissions of `/home/argedion/.recently-used.xbel', but failed: Operation not permitted at /usr/share/perl5/Video/DVDRip/GUI/Main.pm line 205.
argedion@Littious:~$ 
```

I have set permissions for the account to do video so I really don't have a clue as to where I need to go from here. I really want the ability to rip dvd's and store the avi on my hard drive. Any help will be very appreciated.

DVD Rip seems to make the VOB files but it stops at that point. I have tried using winff to convert the VOB file over to AVI but get an error
```
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:05:49, gcc: 4.4.1
Input #0, mpeg, from '/home/argedion/dvdrip-data/Vendetta/vob/001/Vendetta-001.vob':
  Duration: 00:20:36.00, start: 0.036444, bitrate: 6949 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], 7500 kb/s, 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x81]: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
    Stream #0.2[0x80]: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
Unknown encoder 'libmp3lame'

```
hope all this info is helpful to someone who can help me get on the right track. I have rebooted the computer a few times and still nothing helps.

---

