---
title: "Repairing an avi file"
date: 2010-03-15
forum: Multimedia Software
---

### Post by Roger Allott on 2010-03-15
I have an avi file that's 144.6 Mb.

It plays fine on Gnome Mplayer, including the ability to move the scroll bar to get to anywhere I like in the file.

It plays fine in Movie Player, except that it fuggs up when I move the scroll bar to a new place on the file.

VLC is about half way between them, in that it plays OK after giving me an error message - 
```
"VLC can't recognize the input's format:
The format of '/media/SYSTEM/Users/Stuart/Downloads/JDownloader/super.avi.idx' cannot be detected. Have a look at the log for details."
```
It allows me to move to different places on the file, but only after grumbling a bit.

In Nautilus, the file displays a thumbnail OK.

When I open it in Avidemux, I get the error message shown in the thumbnail attached to this post. If I click 'Use safe mode', the file opens but with only 138 frames in the whole thing, which is ridiculous. If I click 'Cancel', Avidemux closes.


When I boot into Windows, no thumbnail appears in Windows Explorer. It plays only audio in Win Media Player and Real Player. Win Movie Maker and Win Live Movie Maker refuse to open it at all.


Clearly, there is something not right with the file, but equally clearly, all (or almost all) of the required data exists because Gnome Mplayer plays the file fine.

Any ideas on how I could repair the file and/or convert it into a better format such that it will play in almost any player on both Linux or Windows would be greatly appreciated.

---

### Post by andrew.46 on 2010-03-15
Hi Roger Allott,

You could test if the container itself is faulty by running something like:

```
ffmpeg -i **[COLOR="Red"]<my_file.avi>[/COLOR]** -acodec copy -vcodec copy fixed_version.avi
```

where <my_file.avi> is the actual name and path to your own file. This will build a new avi container and will eliminate this as possible cause of trouble, if not fix the actual problem...

All the best,

Andrew

---

### Post by Roger Allott on 2010-03-16
Many thanks for that Andrew. Unfortunately, it didn't fix the problem, but the terminal's output might point to why not, and what's wrong with the file.

```
:~$ ffmpeg -i super.avi -acodec copy -vcodec copy fixed_version.avi
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
[NULL @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!
[h264 @ 0x8d67f40]non-existing PPS referenced
[h264 @ 0x8d67f40]B picture before any references, skipping
[h264 @ 0x8d67f40]decode_slice_header error
[h264 @ 0x8d67f40]no frame!

Seems stream 1 codec frame rate differs from container frame rate: 180000.00 (180000/1) -> 29.97 (30000/1001)
Input #0, mpegts, from 'super.avi':
  Duration: 00:19:27.09, start: 85366.081722, bitrate: 1039 kb/s
  Program 1 
    Stream #0.0[0x44]: Audio: aac, 44100 Hz, stereo, s16, 118 kb/s
    Stream #0.1[0x45]: Video: h264, yuv420p, 29.97 tbr, 90k tbn, 180k tbc
Output #0, avi, to 'fixed_version.avi':
    Stream #0.0: Video: 0x0000, yuv420p, q=2-31, 90k tbn, 90k tbc
    Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, s16, 118 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
[avi @ 0x8d69690]dimensions not set
Could not write header for output file #0 (incorrect codec parameters ?)
```

---

### Post by AnthonyBeldt on 2010-03-16
what software will be best to edit video files in ubuntu 9.1

---

### Post by andrew.46 on 2010-03-16
Hi Roger,

Looks like you have h264 video in an avi container and this is usually *not* recommended (there are B-Frame errors in your FFmpeg output). So my final thought is to attempt the same strategy but change the *container*:

```
ffmpeg -i super.avi -acodec copy -vcodec copy fixed_version.**[COLOR="Red"]mp4[/COLOR]**
```

If this does not produce a result wiser heads than mine will have to jump in :).

Andrew

---

### Post by Roger Allott on 2010-03-16
Thanks again, andrew. I've got what looks to be the same result from Terminal, except that a new file called fixed_version.mp4 has been created with size 0 bytes.

I'll post the output to see whether there's any new info in it.

```
:~$ ffmpeg -i super.avi -acodec copy -vcodec copy fixed_version.mp4
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
[NULL @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
    Last message repeated 1 times
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!
[h264 @ 0xa004f40]non-existing PPS referenced
[h264 @ 0xa004f40]B picture before any references, skipping
[h264 @ 0xa004f40]decode_slice_header error
[h264 @ 0xa004f40]no frame!

Seems stream 1 codec frame rate differs from container frame rate: 180000.00 (180000/1) -> 29.97 (30000/1001)
Input #0, mpegts, from 'super.avi':
  Duration: 00:19:27.09, start: 85366.081722, bitrate: 1039 kb/s
  Program 1 
    Stream #0.0[0x44]: Audio: aac, 44100 Hz, stereo, s16, 118 kb/s
    Stream #0.1[0x45]: Video: h264, yuv420p, 29.97 tbr, 90k tbn, 180k tbc
Output #0, mp4, to 'fixed_version.mp4':
    Stream #0.0: Video: 0x0000, yuv420p, q=2-31, 90k tbn, 90k tbc
    Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, s16, 118 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
[mp4 @ 0xa006690]dimensions not set
Could not write header for output file #0 (incorrect codec parameters ?)
```

---

### Post by d3v1150m471c on 2010-03-16
> **AnthonyBeldt said:**
> what software will be best to edit video files in ubuntu 9.1

kdenlive and ffmpeg

---

### Post by andrew.46 on 2010-03-17
Hi Roger,

I suspect then that the video stream itself must be damaged and I am not completely sure if it would be possible or even desirable to re-encode this stream. I have sent an sos to the real FFmpeg expert who may have more insight in this matter than me :).

Andrew

---

### Post by Roger Allott on 2010-03-17
> **andrew.46 said:**
> Hi Roger,

I suspect then that the video stream itself must be damaged and I am not completely sure if it would be possible or even desirable to re-encode this stream. I have sent an sos to the real FFmpeg expert who may have more insight in this matter than me :).

Andrew

Many thanks for taking the trouble to do that.

I can understand what you mean by there being some sort of corruption in the video stream, but I just find it odd that it plays about as perfectly as any other avi file in one player (Gnome MPlayer), yet other players and editors refuse to play it or allow me to interrogate or edit it.

---

### Post by andrew.46 on 2010-03-17
Hi Roger,

> **Roger Allott said:**
> I can understand what you mean by there being some sort of corruption in the video stream, but I just find it odd that it plays about as perfectly as any other avi file in one player (Gnome MPlayer), yet other players and editors refuse to play it or allow me to interrogate or edit it.

It is a little odd but not unknown. I know it is a reasonably sized file but is there a place that you can upload it? I would be interested to see the file itself...

Andrew

---

### Post by Roger Allott on 2010-03-17
> **andrew.46 said:**
> Hi Roger,



It is a little odd but not unknown. I know it is a reasonably sized file but is there a place that you can upload it? I would be interested to see the file itself...

Andrew

Its content is somewhat adult, so are you sure you want it?

To be honest, the file has no value to me whatsoever - it's just a good project that is helping me to learn about video formats, structures and editing in general.

---

### Post by andrew.46 on 2010-03-17
Hi Roger,

> **Roger Allott said:**
> Its content is somewhat adult, so are you sure you want it?

I am 50 years old, a grandfather of 2 and a Registered Nurse with 20 years in Intensive Care : nothing can shock me :). Even so perhaps PM a link to me so the Forums rules are not possibly broken...

Andrew

---

### Post by andrew.46 on 2010-03-17
Hi Roger,

In fact that is a slightly broken file and the usual best strategy is to demux audio and video and then remux. FFmpeg however would have none of this, with a multitude of errors and zero-byte files, so I went to my old friend MPlayer/MEncoder. Audio demux:

```
mplayer super.avi -vo null -vc null -ao pcm:fast:waveheader:file=sound.wav
```

This produced a few error messages but created a workable file. Demux the video:

```
mencoder super.avi -of rawvideo -nosound -ovc copy -o video.h264
```

again a couple of error messages but a workable file is produced. Next to *remux* with FFmpeg:

```

ffmpeg -i video.h264 -vcodec copy -i sound.wav -acodec libfaac -ab 128k -ac 2 super_repaired.mp4

```

There is not a lot of dialogue in this clip so difficult to tell if the AV sync is good or not, but certainly the file plays, seeks etc with all the media players I have on hand. There are probably better ways to this I suspect and I am a little puzzled that MEncoder succeeded where FFmpeg fails...

All the best,

Andrew

---

### Post by Roger Allott on 2010-03-18
Thanks Andrew. I followed your instructions and for the first two commands, I'd guess I got pretty much the same output as you got.

I didn't though for the third command. The first problem was that it said 
```
output.wav: no such file or directory
```
so I presumed this was an oversight and changed the command to include sound.wav instead of output.wav.

But then I ran into error:
```
Unknown encoder 'libfaac'
```

I checked my package list on Synaptic and, whilst I don't have one named 'libfaac', I had one named 'libfaac0'. So I tried that instead, but still got the same error. I tried 'faac' instead, but still got the same error.

Any ideas?

---

### Post by mc4man on 2010-03-18
> ...but still got the same error.
You're using the repo version of ffmpeg (inc. libavcodec52, libavformat52, ect.
aac encoding thru ffmpeg (libfaac), has been removed starting in karmic - see here to resolve ( C. is probably your easiest option - medibuntu extra versions

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by andrew.46 on 2010-03-18
Ho Roger,

> **Roger Allott said:**
> I didn't though for the third command. The first problem was that it said 
```
output.wav: no such file or directory
```
so I presumed this was an oversight and changed the command to include sound.wav instead of output.wav.

Oops :). I have edited my post to reflect the correct name. I see mc4man has given you a steer for the faac error, it is a pain that aac encoding was removed in this way from Karmic's FFmpeg...

Andrew

---

### Post by Roger Allott on 2010-03-19
> **mc4man said:**
> You're using the repo version of ffmpeg (inc. libavcodec52, libavformat52, ect.
aac encoding thru ffmpeg (libfaac), has been removed starting in karmic - see here to resolve ( C. is probably your easiest option - medibuntu extra versions

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

Many thanks for that. I had the Medibuntu repository installed anyway but hadn't got the '-extra-' versions of libavcodec and libavformat. I installed them with Synaptic and ran Andrew's terminal code successfully to create the file as desired.

Are there any other '-extra-' versions of stuff that it would be wise to get?

Looking through the Medibuntu multiverse, these packages pop up as including '-extra-' in their names:
libavfilter-extra-0
libpostproc-extra-51
libswscale-extra-0
libavdevice-extra-52

Would any harm be done to my existing setup if I were to install them?

---

### Post by Roger Allott on 2010-03-19
> **andrew.46 said:**
> Ho Roger,

Oops :). I have edited my post to reflect the correct name. I see mc4man has given you a steer for the faac error, it is a pain that aac encoding was removed in this way from Karmic's FFmpeg...

Andrew

Many thanks for your help with this. It has increased my abilities with video editing and formatting quite a lot.

I just need now to clean up my home folder of the files that were used in the process.

Obviously, sound.wav can now be deleted, but there are 2 other files that look as if they're no longer needed - video.h264 and x264_2pass.log.

Would you agree that I can now delete these?

---

### Post by andrew.46 on 2010-03-19
Hi Roger Allott,

Glad it all turned out :). Yes those files can safely be deleted. If you are keen about manipulating video you might be best at some stage to compile the svn FFmpeg, it makes life a lot easier...

All the best,

Andrew

---

### Post by ben.walker on 2010-03-22
> **d3v1150m471c said:**
> kdenlive and ffmpeg

Can you please post the download link of these softwares?

---

### Post by peter.hopkins on 2010-03-26
> **ben.walker said:**
> Can you please post the download link of these softwares?


I also want, please share it

---

### Post by mister_playboy on 2010-04-02
Thanks for this thread... it helped me out. :)

---

