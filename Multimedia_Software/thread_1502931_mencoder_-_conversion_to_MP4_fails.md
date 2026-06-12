---
title: "mencoder - conversion to MP4 fails"
date: 2010-06-06
forum: Multimedia Software
---

### Post by mykrob on 2010-06-06
Using Miksoft's Mobile Media Converter, and I cannot convert files to MPEG4.

[http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)

Converting to MPEG1/2 works fine, but trying to convert video for my son's PSP always produces an error. Here's the output:


```

>> Command executed:
"/opt/MIKSOFT/MobileMediaConverter/lib/mencoder" -oac lavc -ovc lavc -of lavf -lavcopts aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=700:acodec=libfaac:abitrate=128 -af lavcresample=24000 -vf scale=320:240,harddup -lavfopts format=psp -ofps 30000/1001 -o "/home/myk/Desktop/4522.mp4" "/home/myk/Desktop/4522.flv"

>> Result: 
MEncoder SVN-r30524-snapshot-4.4.1 (C) 2000-2010 MPlayer Team
success: format: 0  data: 0x0 - 0x67f227
libavformat file format detected.
[flv @ 0xaa46d10]Estimating duration from bitrate, this may be inaccurate
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [FLV1]  400x300  0bpp  25.000 fps  495.3 kbps (60.5 kbyte/s)
[V] filefmt:44  fourcc:0x31564C46  size:400x300  fps:25.000  ftime:=0.0400
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 22050 Hz, 2 ch, s16le, 8.0 kbit/1.13% (ratio: 1000->88200)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
** MUXER_LAVF *****************************************************************
REMEMBER: MEncoder's libavformat muxing is presently broken and can generate
INCORRECT files in the presence of B-frames. Moreover, due to bugs MPlayer
will play these INCORRECT files as if nothing were wrong!
*******************************************************************************
OK, exit.
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [scale w=320 h=240]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffflv] vfm: ffmpeg (FFmpeg Flash video)
==========================================================================
----------------------------


```

any idea how to fix this?

Thanks,
-myk

---

### Post by mykrob on 2010-06-06
Looks like i figured it out. I looked at the command used to convert and see that it uses Mobile Media Converter's own mencoder. I edited the command to use the repository's mencoder instead and the conversion worked.

Just removed the part that said $MENCODER and changed it to /usr/bin/mencoder

-myk

---

### Post by mykrob on 2010-06-06
proper solution for the same problem:

install mencoder from the repository.

Since there is no way to permanently modify the command that mobile media converter is passing, simply remove their version of mencoder and add a symbolic link to the good version in its place like so:


cd /opt/MIKSOFT/MobileMediaCnverter/lib
mv mencoder mencoder.bak   ***this renames their mencoder to have a backup
ln -s /usr/bin/mencoder mencoder    **creates a link to the working mencoder




done. Now the program calls the working mencoder each time instead

---

### Post by Redcode on 2010-08-24
thnx for the info i was having the same problem:D

---

