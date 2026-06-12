---
title: "Headphone signal processing...crossfeed,  Dolby Headphone, stereo-to-binaural"
date: 2008-05-22
forum: Multimedia Software
---

### Post by BetterSense on 2008-05-22
does this exist in linux, or what? 

Since switching from the dark side there's only one thing that I have given up, and that is effective DSP for headphones. For those of us that listen exclusively to headphones and have picky tastes, some kind of stereo-collapsing signal processing is almost mandatory for a satisfactory listening experience. 

In windows I used foobar2000 which had several different plugins, for 'crossfeed' as it's called. There is also the Baur Stereo-to-binaural DSP on sourceforge and the [4Front plugin]("http://www.yohng.com/headphones.html"). There is also Dolby headphone, which is very effective.

I usually use Amarok, or rhythmbox; I have yet to find any way to implement any of these very available DSPs in linux. Please help. It's almost worth booting back into windows in order to listen to music, but I don't want to.

---

### Post by DefineByte on 2008-05-22
I use Foobar2000 under Wine.

The Bauer DSP seems to work fine for me (last time I checked).

---

### Post by BetterSense on 2008-05-23
Any suggestions other than using foobar under Wine? Last I tried that, it kept crashing on me. I'd rather use native linux applications.

---

### Post by DefineByte on 2008-05-23
I believe MPlayer has some kind of crossfeed option. Not the ideal interface of course.

---

### Post by BetterSense on 2008-05-23
I have no problem with mplayer. Is it in the man page?

---

### Post by DefineByte on 2008-05-23
I don't know if it's in the man page.

I don't use MPlayer myself but I remember searching for Linux apps supporting crossfeed in the past and only coming up with MPlayer. Something like 'mplayer -af pan:2:1:.5:.5:1' maybe?

---

### Post by BetterSense on 2008-05-23
Imagine my joy upon reading in the mplayer man page that mplayer has a 'hrtf' option that supposedly 'Converts multichannel audio to 2 channel output for headphones, preserving the spatiality of the sound'. At first I tried it, but it error'd saying it wasn't 48kHz, so I resampled it and tried it, but it didn't work. It sounded bad and crackled and other bad stuff.

```
chaz@brutus:~/Music/Lossless albums/Hot Water Music/Forever and Counting$ mplayer -af resample=48000:0:2,hrtf=s  10\ Western\ Grace.flac
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5400+ (Family: 15, Model: 107, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 10 Western Grace.flac.
Audio file file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 979.8 kbit/69.43% (ratio: 122477->176400)
Selected audio codec: [ffflac] afm: ffmpeg (FFmpeg FLAC audio decoder)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
[hrtf] Using active matrix to decode 2 channel input, HRTF to mix 3/2 matrix surround into L, R channels
A:  20.7 (20.6) of 257.0 (04:17.0) 18.7%
Exiting... (Quit)
chaz@brutus:~/Music/Lossless albums/Hot Water Music/Forever and Counting$      
```

---

### Post by DefineByte on 2008-05-23
I guess '-af pan' is rather unsophisticated. I don't think you can specify frequencies to mix etc, which is a shame.

I'd be interested if you get any good results from hrtf, although it sounds like it's for multichannel files.

---

### Post by BetterSense on 2008-05-23
I think -af pan is worthwhile, that is, better than nothing. I've been using it like you suggested 

```
mplayer -af pan=2:1:x:x:1 musicfile.flac
```

It takes the edge off nicely. This is just like the 'stereo width' option on the Behringer feedback destroyer, which can work as a primitive crossfeed. I've experimented with the value of x, and I think between .05 and 1.5 is where the best results are obtained. This seems to work nicely.

I've been having trouble with mplayer failing to play things. I don't know what exactly it is but I have a feeling it's from my config file, because when I pound out all the options so far it hasn't done it. But I wanted to put

```
af=pan=2:1:x:x:1 musicfile.flac
```

so that it always did it, and it worked, but I think my config file in general might be causing my freezage problems. Sometimes with video too, it will act like it's going to play, but then the % counter doesn't take off; you can still page up and down through the video but it won't play. I have video options in my config file such as subtitle position and stuff.

---

### Post by xzero1 on 2008-06-04
Sox might be a good choice since it has some built-in audio processing including 'earwax' designed for headphones and can apply various ladspa plugins.

---

### Post by DefineByte on 2008-06-04
Looks very interesting.

---

### Post by mhd78 on 2009-03-22
Has anyone found a good solution to this issue?  

Most of the music I listen to is from the 60s and thus mixed for speakers and just doesn't sound right on headphones.  I have [Rockbox]("http://www.rockbox.org/") on my portable MP3 player which implements crossfeed very well.

I wonder if the Rockbox [crossfeed code]("http://svn.rockbox.org/viewvc.cgi/trunk/apps/dsp.c?view=markup") could be easily modified to make a [GStreamer]("http://gstreamer.freedesktop.org/") plugin that could then be used with Totem and other linux media players.  Does this sound like a sensible approach?  I'm not exactly a C expert and I really don't know what I'm talking about at this point but may have time to tinker around.  Of course I have no interest in reinventing the square wheel if a solution already exists.

---

### Post by DefineByte on 2009-03-22
If you don't mind the interface you could build a Rockbox UI simulator. Rockbox as an application has been put forward as a project for Google Summer of Code 2009 but I don't know if there are any plans for a desktop friendly UI.

A GStreamer plugin based on the Rockbox crossfeed would be great. :)

---

### Post by mhd78 on 2009-03-22
A solution I found to be satisfactory..

[http://www.rpgameplace.de/blog/index.php?/archives/21-Stereo-to-binaural-with-ALSA-using-bs2b-LADSPA-plug-in.html](http://www.rpgameplace.de/blog/index.php?/archives/21-Stereo-to-binaural-with-ALSA-using-bs2b-LADSPA-plug-in.html)

I'm using jack and pulse, so I have all the sound on my system patched through the plugin via jack-rack

---

### Post by mejensen1 on 2010-05-02
thanks for the exchange

---

