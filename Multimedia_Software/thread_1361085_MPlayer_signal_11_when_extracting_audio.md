---
title: "MPlayer signal 11 when extracting audio"
date: 2009-12-21
forum: Multimedia Software
---

### Post by watupgroupie on 2009-12-21
I have an MKV file and I'm trying to convert it to a MP4 file with the same video source and the ac3 audio converted to aac 2 channel. I got the video extracted and changed to a 4.1 profile just fine. The guide I'm using says to extract the audio using MPLayer using ```
mplayer cloudy.mkv -novideo -ao pcm:fast:file=audiodump.wav -channels 2
``` I assume that will extract the audio and put it into a 2 channel .wav file. But I always get this error when ever I run it. ```
kent@kent-laptop:~/Desktop$ mplayer cloudy.mkv -novideo -ao pcm:fast:file=audiodump.wav -channels 2
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing cloudy.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang eng
[mkv] Track ID 3: subtitles (S_TEXT/UTF8), -sid 0, -slang eng
[mkv] No video track found/wanted.
Matroska file format detected.


MPlayer interrupted by signal 11 in module: demux_open2
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
 [ This binary of MPlayer in Debian is currently compiled with
   '--enable-debug'; the debugging symbols are in the package
   'mplayer-dbg'.]

```

Any ideas?

---

### Post by watupgroupie on 2009-12-21
I found a solution if anyone else is having this problem. Use MKV extract the same way you got the video out and extract the ac3 audio instead ```
mkvextract tracks input.mkv 2:audio.ac3
``` Use ```

mplayer -ao pcm:file=output_file.wav input_file.ac3
``` which still uses mplayer but worked for me unlike the other command. Then just use NeroAacEnc and compile your video and audio with mp4box. I followed this tutorial by the way [http://www.linuxlove.info/site/17/converting-remuxing-a-mkv-for-playback-on-the-xbox-360/](http://www.linuxlove.info/site/17/converting-remuxing-a-mkv-for-playback-on-the-xbox-360/).

---

