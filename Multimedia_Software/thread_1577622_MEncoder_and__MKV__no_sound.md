---
title: "MEncoder and  MKV : no sound"
date: 2010-09-19
forum: Multimedia Software
---

### Post by emma_peel on 2010-09-19
Hello forum.

After a couple of tries, I think I found a bug in MEncoder. I did a couple of google research, without success. I can't be the first to notice it, but did not find any documents on this topic.

When transcoding video with MEncoder using the .MKV container, I do not have any sound, except if I copy the audio stream.

Here is the command I've used :

```
mencoder Tron.mov -o Tron.mkv -of lavf -oac faac -faacopts br=128:mpeg=4:object=2 -channels 2 -srate 48000 -ovc x264 -x264encopts threads=auto:bframes=0:partitions=all:8x8dct:subq=6:bitrate=1800
```

Using mp3 gives the same result :

```
mencoder Tron.mov -o Weeds.S06E01.mencoder.mkv -of lavf -oac mp3lame -lameopts br=128 -ovc x264 -x264encopts threads=auto:bframes=0:partitions=all:8x8dct:subq=6:bitrate=1800
```

No sound.

When I use the .AVI container (MEncoder seems manipulating this container better than the others). I have the sound.

There is one message in the log :

```
x264 [info]: profile High, level 4.0
Pos:   0.0s     23f ( 0%)  0.00fps Trem:   1min   0mb  A-V:0.084 [0:0]
Skipping frame!
VIDEO CODEC ID: 28f ( 0%) 39.87fps Trem:   3min   0mb  A-V:0.034 [0:0]
AUDIO CODEC ID: 15002, TAG: 0
Writing header...
[matroska @ 0x62a2e0]Codec for stream 0 does not use global headers but container format requires global headers
[matroska @ 0x62a2e0]Codec for stream 1 does not use global headers but container format requires global headers
**[matroska @ 0x62a2e0]No AAC extradata, unable to determine samplerate.**

```

That could be a clue, but did not find relevant documentation.

So, is there some tricks I did not find ? Or is it just bugged and useless to generate a clean .MKV in a single step ?

Thank you for your support !

---

### Post by emma_peel on 2010-09-21
Arf, I finally found it in the documentation :

> 11.1.12. Muxing Now that you have encoded your video, you will most likely want to mux it with one or more audio tracks into a movie container, such as AVI, MPEG, Matroska or NUT. **MEncoder is currently only able to natively output audio and video into MPEG and AVI container formats.**


This is in this chapter :

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html#menc-feat-dvd-mpeg4-muxing](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html#menc-feat-dvd-mpeg4-muxing)

---

### Post by ron999 on 2010-09-21
What is it that you're trying to do?

---

### Post by SeijiSensei on 2010-09-21
> **emma_peel said:**
> When transcoding video with MEncoder using the .MKV container, I do not have any sound, *except if I copy the audio stream*.

Is there some reason you need to convert the audio stream?  If copying it directly works, why not do that?

You could use mencoder to extract the video and audio into separate files then use [mkvtoolnix]("http://www.bunkus.org/videotools/mkvtoolnix/") to build the MKV from the separate streams.  That seems like more work than it's worth, though.

---

### Post by emma_peel on 2010-09-27
Well, my idea was to convert any source to a file compatible for a given device in one instruction. That's why I cannot just copy the audio stream. I some case, it will not work.

I have written a short script, which transcodes the audio and video streams separately, and then muxes them together.

---

### Post by ron999 on 2010-09-27
> **emma_peel said:**
> ... some case, it will not work.
Hi
I think that me and the other guy above were gonna explain that there's no need to convert aac into aac.

But if you want to keep the script to use for all types of input files then you are correct, it won't work every time.:)

---

