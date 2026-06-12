---
title: "How do i separate an audio stream from a video stream?"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by Ameliorate on 2007-05-18
I have downloaded some videos from youtube and other various sites and I want to separate the audio stream from the video so that I can use it separately for another purpose. Is there any free software I could use to do this(on linux)?

---

### Post by girishv on 2007-05-18
Hi,

You can use mplayer to separate (or dump the sound as a .wav file). Here is a command to achieve it.
mplayer -vo null -ao pcm your_video_file

It creates an audio file called audiodump.wav

Similarly, you can use mencoder to extract or create video only
mencoder -nosound -ovc lavc -o your_new_video.avi your_video_file

I am looking at a way to combine the two commands into one.

I use these methods most of the times when I want to reduce the resolution to fit into my mobile display

Girish

---

### Post by Ameliorate on 2007-05-19
where does the command put the dumped .wav file?   Edit:  (never mind)

Edit: thanks, it worked. However I had to change th -ao pcm to -ao sdl

Thanks

---

### Post by Ameliorate on 2007-05-19
I did that command, but I only get an audio file that is 2 minutes and 12 seconds long. I tried using different audio drivers but I still got the same problem. 
Here is what the terminal output.


kent@kent-desktop:~/Desktop$ mplayer -vo null -ao oss Mario_Piano.flv
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 75, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Mario_Piano.flv.
libavformat file format detected.
VIDEO:  [FLV1]  320x240  0bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffflv] vfm: ffmpeg (FFmpeg Flash video)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 22050 Hz, 1 ch, s16le, 64.0 kbit/18.14% (ratio: 8000->44100)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [oss] 22050Hz 1ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [null] 320x240 => 320x240 Planar YV12 
A: 132.5 V: 240.6 A-V:-108.138 ct:-12.045 3611/3611  1%  0%  0.5% 0 0 
Too many audio packets in the buffer: (4096 in 866962 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A: 132.5 V: 240.6 A-V:-108.138 ct:-12.049 3611/3611  1%  0%  0.5% 0 0 

Exiting... (End of file)
kent@kent-desktop:~/Desktop$

---

