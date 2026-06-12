---
title: "Converting OGM files"
date: 2010-06-21
forum: Multimedia Software
---

### Post by 7raTEYdCql on 2010-06-21
I have a set of .ogm files, which don't play in any of my media players.

Is there any way in which I can play these files. I have checked forum postings, and haven't found any helpful advice there.

Considering that I have no clue on audio and video encoding, can someone please help.

---

### Post by TechnikAlsace on 2010-06-21
Just have a look at [http://www.ffmpeg.org/](http://www.ffmpeg.org/)

and then install the ffmpeg package with the ubuntu software center

---

### Post by 7raTEYdCql on 2010-06-21
Can you please elaborate. I tried winff (which is the gui version of ffmpeg), and I don't think it works.

It generated a .avi file which is 0bytes in size.

Any suggestions?

---

### Post by ron999 on 2010-06-21
Hi
See if mencoder will convert to avi.
Use a command like this:-
```
mencoder <input_filename> -o foo.avi -oac mp3lame -ovc lavc

```
(I got the information from another thread, here:-[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1501566]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1501566"))

---

### Post by 7raTEYdCql on 2010-06-22
The output of the above command gives the following.
mehrzad@mehrzad-laptop:~/Desktop$ mencoder The\ Blues\ 1\ Red\ white\ and\ blues.ogm -o foo.avi -oac mp3lame -ovc lavc
MEncoder SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x3464a494
[Ogg] stream 0: video (FOURCC VP70), -vid 0
[Ogg] stream 1: audio (Vorbis), -aid 0
Ogg file format detected.
VIDEO:  [VP70]  640x352  12bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:18  fourcc:0x30375056  size:640x352  fps:29.970  ftime:=0.0334
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 64.0 kbit/4.17% (ratio: 8000->192000)
Selected audio codec: [ffvorbis] afm: ffmpeg (FFmpeg Vorbis)
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [vfwex] Win32/VfWex video codecs
Loading codec DLL: 'vp7vfw.dll'
Win32 LoadLibrary failed to load: vp7vfw.dll, /usr/lib/codecs/vp7vfw.dll, /usr/lib/win32/vp7vfw.dll, /usr/local/lib/win32/vp7vfw.dll
Can't open library vp7vfw.dll
ICOpen failed! unknown codec / wrong parameters?
VDecoder init failed :(
Cannot find codec matching selected -vo and video format 0x30375056.
Read DOCS/HTML/en/codecs.html!
==========================================================================

Exiting...
mehrzad@mehrzad-laptop:~/Desktop$ 

I guess the problem as can be seen from above is something to do with a missing vp70codec. And that is something to do with the windows operating system. Any help?

---

### Post by ron999 on 2010-06-22
Hi
Make sure you have the extra Medibuntu codecs installed.
Then maybe the ogm files can be viewed with mplayer or converted with mencoder.
Read about **Playing Non-Native Media Formats**.
Here:-[https://help.ubuntu.com/community/Medibuntu#Playing%20Non-Native%20Media%20Formats]("https://help.ubuntu.com/community/Medibuntu#Playing%20Non-Native%20Media%20Formats")

---

### Post by 7raTEYdCql on 2010-06-23
Thank you ron99, it worked. I play the ogm files on mpleyer.

---

