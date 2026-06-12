---
title: "Decent quality FLV to MPEG2 conversion with ffmpeg?"
date: 2012-03-21
forum: Multimedia Software
---

### Post by viipu on 2012-03-21
Hiya,

there's a bunch of FLV videos I'd like to archive on DVDs, but my nitpicky DVD player only accepts MPEG2 (or various nasty DivX formats). I don't necessarily need to convert these, but it would be nice to watch them with the family and not just on my teensy netbook. I've tried a few converters, but usually they just give awful video quality, sometimes loss of sound and/or video completely.

ffmpeg with -target dvd -s 640x360 gives good  quality, but the output file is 3 times the size of the input. Any tips on how I could reduce the file size  without any noticeable loss in quality?

Alternatively, does  anyone know what -target dvd actually sets, I mean exactly? I could  probably figure out some solution if I knew what to work from, but I  can't seem to find the exact settings in the documentation. They're  probably there in the ffmpeg output but what options should I try and modify,  and how? In short, where is the extra "data" likely to be coming from, and is there any way to minimise it? 

Or is this a doomed enterprise? What would you guys actually do, convert them, or leave them be and just watch them on a computer? 

Metadata on the input and output files below (from ffmpeg -i filename.flv -target dvd -s 640x360 filename.mpg)

```

Input #0, flv, from 'filename.flv':
  Metadata:
    duration        : 2986
    moovposition    : 28
    width           : 640
    height          : 360
    videocodecid    : avc1
    audiocodecid    : mp4a
    avcprofile      : 77
    avclevel        : 30
    aacaot          : 2
    videoframerate  : 0
    audiosamplerate : 48000
    audiochannels   : 2
  Duration: 00:49:45.51, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 640x360 [PAR 1:1 DAR 16:9], 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16
Assuming PAL for target.

Output #0, dvd, to 'filename.mpg':
  Metadata:
    encoder         : Lavf52.64.2
    Stream #0.0: Video: mpeg2video, yuv420p, 640x360 [PAR 1:1 DAR 16:9], q=2-31, 6000 kb/s, 90k tbn, 25 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, stereo, s16, 448 kb/s

```Awfully sorry if this has been asked and answered before, must be blind if that's the case.
Any help very much appreciated, thanks in advance!

---

### Post by pixiq on 2012-03-21
Hi viipu,

I have converted videos according to this link
[[COLOR="SeaGreen"]_http://ubuntuforums.org/showthread.php?t=1920371_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1920371")

It is not targeting a dvd player, but I think that using the codec libx264 will reduce the size a lot compared to the big mpeg files you are making.

Can you connect your netbook to the TV set via the vga port? That's a way to share your videos with the whole family.

---

### Post by SeijiSensei on 2012-03-21
He won't be able to play an H.264-encoded video on a regular DVD player.  As he mentioned, the one he has supports MPEG2 and DivX/XviD.  Connecting the computer to the TV via VGA or DVI/HDMI is one approach, but it makes it hard to send a copy to grandma so she can play it on her DVD player.

@ OP
My guess is the size reduction is simply the result of the encoding.

Personally I'd just encode them with XviD in the AVI container if the player supports that.  (Most DivX-compatible players do.) There will be a slight loss of quality, but it probably will be invisible to your family.  That might not work so well if you want a solution for grandma so she can just stick the DVD into the machine and watch.

---

### Post by viipu on 2012-03-21
Hey, thanks for the quick replies! 

@pixiq
Wish I could connect to the telly straight, but it's a proper CRT monstrosity (who'd have LCD when you can have an electron gun?), even the DVD's connected through composite video because all my SCART cables were eaten by virtual mice. I really don't want to invest in more cables or VGA converters when the TV'll probs be done for in a few years anyhow.

So what I'm actually asking is that is there any sense to be converting the files at all. I guess your reply would be no, or not to mpg anyhow?

@SeijiSensei
She I think you'll find :P
The dvd player ([Philips DVP3880]("http://www.philips.co.uk/c/blu-ray-dvd/3000-series-dvp3880_05/prd/")) specs give compression formats MPEG1, MPEG2, DivX 3.11, 4.x, 5.x, 6.0, Ultra, along with DivX in the section with the disc types (CD, DVD, Video-CD etc). 
Do you reckon that could handle XviD? I'm really lost when it comes formats (in case you didn't notice)

//edit just read your reply again, I'll give XviD a go and report back, cheers for the tip!

Thank you both!

---

### Post by SeijiSensei on 2012-03-21
[DivX]("http://en.wikipedia.org/wiki/DivX") is a proprietary codec. [XviD]("http://en.wikipedia.org/wiki/Xvid") is a reverse-engineered open version; I believe it's equivalent to DivX 4.

The most common "container" format for XviD is Microsoft's AVI.  That's probably what your DVD player expects to find.  Use MP3 for the audio encoding.

I recommend mencoder for this task.  I've used it in the past to convert from H.264+AAC encodes in the Matroska (.mkv) container to XviD+MP3 in the AVI container.  Here are some [quick guidelines]("http://en.gentoo-wiki.com/wiki/Mencoder#XviD") to XviD encoding with mencoder.

---

### Post by viipu on 2012-04-26
Took a while to actually get round to converting these but thank you for thoroughly excellent advice!

The command I ended up using was

```
ffmpeg -i source.wmv -sameq target.avi
```Not absolutely 100% but will do very well, a tiny bit of fuzz around the picture and a slight increase in size but the best solution I've seen. Cheers!

//edit Too quick off the mark, picky specimen that Philips DVD player. It won't play .flv to .avi files no matter what codecs I try (NOT going to stoop to Windows codecs though), although .wmv to .avi seemed to play ok. So looks like it'll have to be .mpeg after all. Oh, hello again, HUGE files. Still, better than I expected.

---

