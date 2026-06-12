---
title: "Cutting avi video with ffmpeg, audio doesn't sync"
date: 2014-04-19
forum: Multimedia Software
---

### Post by aspidistra on 2014-04-19
Command :  
 
ffmpeg -ss 00:54:10 -t 00:03:04 -i movie.avi -acodec copy -vcodec copy output.avi

gives me un-synced audio/video (when the file 'movie.avi' is synced).  Why is that?

How to cut with perfect sync.

---

### Post by andrew.46 on 2014-04-19
There may be some hints in the complete terminal output, including the commandline. Can you copy and paste this into a Forum post?

---

### Post by aspidistra on 2014-04-19
> **andrew.46 said:**
> There may be some hints in the complete terminal output, including the commandline. Can you copy and paste this into a Forum post?
  

ffmpeg -ss 00:54:10 -t 00:03:04 -i outpost11.avi -acodec copy -vcodec copy oooo.avi
ffmpeg version 0.8.10-4:0.8.10-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Feb  6 2014 20:56:59 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[mpeg4 @ 0x13a79a0] Invalid and inefficient vfw-avi packed B frames detected
Input #0, avi, from 'outpost.avi':
  Duration: 01:30:10.04, start: 0.000000, bitrate: 1081 kb/s
    Stream #0.0: Video: mpeg4 (Advanced Simple Profile), yuv420p, 640x272 [PAR 1:1 DAR 40:17], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
Output #0, avi, to 'oooo.avi':
  Metadata:
    ISFT            : Lavf53.21.1
    Stream #0.0: Video: mpeg4, yuv420p, 640x272 [PAR 1:1 DAR 40:17], q=2-31, 25 tbn, 25 tbc
    Stream #0.1: Audio: libmp3lame, 48000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press ctrl-c to stop encoding
[NULL @ 0x13a79a0] Invalid and inefficient vfw-avi packed B frames detected
frame= 4672 fps=  0 q=-1.0 Lsize=   17080kB time=184.01 bitrate= 760.4kbits/s    
video:13866kB audio:2911kB global headers:0kB muxing overhead 1.804645%

---

### Post by andrew.46 on 2014-04-19
Hmmm.... the only error there is a complaint from FFmpeg that a hack has been used to push b frames into an avi container and usually this is a cautionary warning only. Does the following command make any difference:

```

ffmpeg -i -ss 00:52:10 outpost11.avi -ss 00:02:00 -t 00:03:04 -codec copy test.avi

```

If not perhaps you may have to actually reencode the video stream. Some interesting reading [here]("http://trac.ffmpeg.org/wiki/Seeking%20with%20FFmpeg"). You would probably also be well served by upgrading your copy of FFmpeg as detailed elsewhere on this excellent wiki...

**Edit:** See the cautionary note on the wiki page a linked to:

```

Doing a bitstream copy gives me a broken file?

If you use -ss with -c:v copy, the resulting bitstream might end up being choppy, 
not playable, or out of sync with the audio stream, since ffmpeg is forced to 
only use/split on i-frames. 

```

---

### Post by aspidistra on 2014-04-20
will try it

command doesn't seeem to work

when i've tried it again i'll get back to you

thanks

---

### Post by SeijiSensei on 2014-04-20
You could try [mencoder]("http://askubuntu.com/questions/59383/extract-part-of-a-video-with-a-one-line-command") for this task. It's pretty old now but was developed originally to handle the AVI container.  You can install it from the repositories with "sudo apt-get install mencoder".

I ran a little test with an AVI encoded with DivX and MP3 and had audio syncing problems as well.  However you can [adjust the synchronization]("http://www.misterhowto.com/index.php?category=Computers&subcategory=Video&article=synchronize_sound_with_mencoder") with the "-delay" parameter.  I'd be surprised if ffmpeg didn't have the same type of option.

Andrew, do you suppose this has to do with not cutting exactly on a keyframe?

---

### Post by andrew.46 on 2014-04-26
> **SeijiSensei said:**
> Andrew, do you suppose this has to do with not cutting exactly on a keyframe?

I have to confess I am no expert in this issue and thus I would only be guessing :(.

---

