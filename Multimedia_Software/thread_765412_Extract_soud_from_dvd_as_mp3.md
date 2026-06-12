---
title: "Extract soud from dvd as mp3"
date: 2008-04-24
forum: Multimedia Software
---

### Post by geir2rs1 on 2008-04-24
Hi, 
I have been looking around for a way to extract the sound from a dvd. preferably as mp3.
I have some concert dvds I wish to be able to listen to on my mp3 player.

Can anyone here please advise me how to do this?

---

### Post by cor2y on 2008-04-24
mplayer/mencoder , ffmpeg or any gui dvd movie ripper can do this for you.
Here's an example using mplayer
```
 mplayer dvd://1 -dumpfile audio.wav -ao pcm
```
dvd://1 = your dvd drive the disc is inserted in it might be something else like dvd://0 etc.
There are other more elagant ways of ripping the audio but this is a quick and dirty way. From there its just a matter of usinga cmdline tool like mencoder,ffmpeg to encode to mp3 or a gui converter like audacity.

---

### Post by geir2rs1 on 2008-04-25
Hi,
I tried this command: mplayer dvd://1 -dumpfile audio.wav -ao pcm . Thought that would make sense since I've only got one dvd drive.
I have use dvd://0 and dvd://1. Both with the same result.

Here is what happened both times




 The dvd woke up and after a while the command window presented me with a lot of messages like this:

geitho@gt-ubuntu-0:~$ mplayer dvd://1 -dumpfile audio.wav -ao pcm
MPlayer 2:1.0~rc1-0ubuntu13.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8200  @ 2.66GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
There are 4 titles on this DVD.
There are 26 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
audio stream: 1 format: ac3 (5.1) language: en aid: 129.
number of audio channels on disk: 2.
subtitle ( sid ): 0 language: en
subtitle ( sid ): 1 language: fr
subtitle ( sid ): 2 language: es
subtitle ( sid ): 3 language: de
subtitle ( sid ): 4 language: nl
subtitle ( sid ): 5 language: it
subtitle ( sid ): 6 language: pt
subtitle ( sid ): 7 language: pl
number of subtitles on disk: 8
MPEG-PS file format detected.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  9800.0 kbps (1225.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
[AO PCM] File: audiodump.wav (WAVE)
PCM: Samplerate: 48000Hz Channels: Stereo Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12 
a52: CRC check failed!  1.389 ct:  0.000   1/  1 ??% ??% ??,?% 1 0 
a52: error at resampling
a52: CRC check failed!  1.825 ct:  0.004   2/  2 ??% ??% ??,?% 2 0 
a52: error at resampling
a52: CRC check failed!  2.892 ct: -0.088  26/ 26  6%  0%  0.4% 19 0 
a52: error at resampling
A:   2.9 V:  85.4 A-V:-82.549 ct: -0.104  29/ 29  6%  0%  0.4% 21 0 


Then after a very long wait this:


a52: CRC check failed!  43.449 ct:-14.488 3625/3625  5%  0%  0.3% 1257 0 
a52: error at resampling
a52: CRC check failed!  43.253 ct:-14.520 3633/3633  5%  0%  0.3% 1260 0 
a52: error at resampling

This kept on going for about 2 hours (I wanted to see how it ended. I did have a walk with the dog while this was going on :) )
After a very long time this popped up in the command window:

A: 348.1 V: 528.0 A-V:-179.819 ct:-21.343 5339/5339  5%  0%  0.3% 1849 0 
Too many audio packets in the buffer: (4096 in 8257536 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Too many audio packets in the buffer: (4096 in 8257536 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A: 348.1 V: 528.0 A-V:-179.819 ct:-21.347 5339/5339  5%  0%  0.3% 1849 0 
gnome_screensaver_control()
Exiting... (End of file)
geitho@gt-ubuntu-0:~$ 

I'm sorry about the long listings, but I thought it might help to sort out what is missing:
 
I feel a bit lost here. I know I can do this on my work laptop but that would be an embarrassing defeat. It runs XP, and I try to avoid that at home.

Any ideas?

Geir

---

### Post by geir2rs1 on 2008-04-25
I forgot to mention that an wav file was created in my home folder.
It had the name audiodump.wav. It was quite small though.  about 43 mb. A lot smaller than I had suspected so...

Geir

---

### Post by cor2y on 2008-04-25
Like i said its a quick and dirty way although it seems it forgot the quick part :)
Dvd ripping audio found this thread from 2005 in the forums right here
[http://ubuntuforums.org/showthread.php?t=89955](http://ubuntuforums.org/showthread.php?t=89955)
I don't know how much it might help.

---

### Post by mc4man on 2008-04-25
there are many ways to structure command  - here's an example
The title with track is 2, the chapter i want is 2
Because there are 2 audio tracks i run the command first without aid (there's probably a command to show audio id's )
```
doug@doug-desktop:~$ mplayer -vc null -vo null -ao pcm:fast:waveheader:file=bowie.wav dvd://2 2-2........................clipped
Playing dvd://2.
There are 4 titles on this DVD.
There are 1 angles in this DVD title.
audio stream: 0 format: lpcm (stereo) language: en aid: 160.
audio stream: 1 format: ac3 (5.1) language: en aid: 129.
```
In this case I want the lpcm stream so
```
doug@doug-desktop:~$ mplayer -vc null -vo null -aid 160 -ao pcm:fast:waveheader:file=bowie.wav dvd://2 -chapter 2-2

```
adjust as needed ie. title, block of chapters, whole title ect.
dvd://x, (x=title)   -chapter a-b (a=start at, b=end at)
if you get warning about system too slow to play ignore as long as you can see playback activity - you'll get audio rip (or remove fast: )

---

