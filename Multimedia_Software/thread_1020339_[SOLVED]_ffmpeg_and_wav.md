---
title: "[SOLVED] ffmpeg and wav"
date: 2008-12-24
forum: Multimedia Software
---

### Post by cotcot on 2008-12-24
I want to convert an mpg movie to avi with wav audio in it using ffmpeg.
Can anybody advise which audio codec i need to use ? Reason for this is to hav wave 16 bit audio in the container in order to use the audio in blender. I tried pcm_s16be (this is the compatible audio for blender) instead of the question marks but it did work. wvma2 did not work either.

```
ffmpeg -i input.mpg -acodec ??? -vcodec copy -ab 224k 
```

A suggestion with mencoder is fine as well.

This should shorten the work flow i use now : extract audio to a separate file with avidemux as pcm and use it in blender as a separate file.

---

### Post by Samhain13 on 2008-12-25
I just did a test with a file that has these particulars:

```
ffmpeg -i test.mpg -b 1024kb test.avi
```

> Input #0, mpeg, from 'test.mpg':
  Duration: 00:08:20.9, start: 0.500000, bitrate: 1103 kb/s
  Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 800x592, 104857 kb/s, 30.00 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 44100 Hz, stereo, 64 kb/s

Output #0, avi, to 'test.avi':
  Stream #0.0: Video: mpeg4, yuv420p, 800x592, q=2-31, 1024 kb/s, 30.00 fps(c)
  Stream #0.1: **Audio: mp2, 44100 Hz, stereo, 64 kb/s**

In Blender's Sequence Editor (using 2.48a from the Blender site):

1. Add > Movie + Audio (HD)
2. Go to Panels, Scene - Audio Sound Block Buttons
3. Under "Sequencer", click "Sync" and "Scrub": so you can hear the audio during preview and frame scrubbing.
4. Back to Panels, go to Render Buttons.
5. Under the Audio tab, select "Multiplex Audio".

You don't need to have WAV audio in your AVI clips for you to be able to have sound in your render. But then, I could be wrong. :)

---

### Post by cotcot on 2008-12-25
No, you are correct.
I tried the mpg test also and confirm what you write.
I read about audio in the blender tuts and did even not try with mp1. The tutorials write that only wav can be imported as stand alone.  

I checked a little bit further on the blender VSE. A separate mp1 track is OK, an mp3 is not OK.

Thanks

---

### Post by Samhain13 on 2008-12-25
> The tutorials write that only wav can be imported as stand alone.
I'm not happy about this as well because I have mostly Vorbis and MP3 audio. :(

---

### Post by cotcot on 2008-12-26
> **Samhain13 said:**
> I'm not happy about this as well because I have mostly Vorbis and MP3 audio. :(

Do you get these (vorbis) from a camcorder ?
I have a Canon HF100. Converting it with Nero 9 (linux transcoding of the AVCHD format to mpg or avi gives stuttering playback on some clips) gives mp1 audio in the container. Blender can take it.

---

### Post by Samhain13 on 2008-12-27
No, I rip my audio stuff to Vorbis. I don't have a camera (except the one on my phone).

The other files I have are from desktop captures (Theora) and from ESpeak and MIDI samples. It's not really a pain converting these stuff from .ogg to .avi/.wav; but I guess there's no harm in hoping that one day, we can use .ogg in Blender too. Hehe! :)

---

