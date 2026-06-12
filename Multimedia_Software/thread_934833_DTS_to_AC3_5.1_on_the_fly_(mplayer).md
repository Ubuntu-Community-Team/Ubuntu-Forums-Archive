---
title: "DTS to AC3 5.1 on the fly (mplayer)"
date: 2008-10-01
forum: Multimedia Software
---

### Post by tito13kfm on 2008-10-01
I recently lost the ability to use a DTS capable receiver (long story) and was looking for a way of playing my movie backups with DTS tracks on my HDTV and have surround sound on a AC3 capable receiver.  I also wanted to make sure that my AC3 backups which I have started to make would remain untouched and passed through to the receiver as-is.

After much searching and playing I think I have found a solution.  I'm just sharing my solution so if others are looking for a way to do this they may find it.

```
mplayer file.mkv -fs -ao alsa:device=spdif -ac hwac3, -channels 6 -af lavc3enc=1 -af channels=6
```

an explanation:
file.mkv is the name of the file you are trying to play.
-fs enables full screen (not necessary, but I like it on my hdtv)
-ao alsa:device=spdif tells my computer to output sound through my optical toslink connector to my receiver.
-channels 6 tells mplayer to process 5.1 surround sound
-ac hwac3, first makes mplayer try the hwac3 codec, the trailing comma makes it fall back to default codecs if that fails.
-af lavc3enc=1 enables the magic.  This makes mplayer encode the audio stream to ac3 on the fly
-af channels=6 makes sure that the resulting ac3 stream is full surround.

I am always looking for advice and criticism to my madness.  I would love to hear the way you have gotten this to work.  There are a million and 1 ways to skin a cat in linux, this works for me.

Another tip.  If your computer cannot handle h264 HD movies very well you can add the following to that command line.
```
-lavdopts fast=1:threads=2:skiploopfilter=all
```

this enables fast decoding, enables dual core decoding, and disables the loopfilter.  Video quality suffers a little bit, but no more stuttering on 1080p DTS h264 mkv's!

---

### Post by fubarbundy on 2008-11-22
The lavc option should be -lavcac3enc=1

---

### Post by fubarbundy on 2008-11-22
A few other tips:

- For the highest quality, use ```
-lavcac3enc=1:640
```

- If you are using smplayer (a damn good media player), you can set it up to always use S/PDIF as follows: Under Options/Preferences/General/Audio, untick 'enable the audio equalizer', tick 'AC3/DTS pass-through S/PDIF' and select '6 (5.1) Surround' channels by default. Under Options/Preferences/Advanced/Options for MPlayer, enter the following in the Audio filters text box: ```
lavcac3enc=1:640
```

---

### Post by Drenhead on 2009-03-30
Do you know of a way to convert the dts into an .ac3 file that I can remux in with a .h264 file for streaming to a ps3?

I'm pulling my hair out trying to figure out how to convert dts to ac3.

---

### Post by peepingtom on 2009-03-30
> **Drenhead said:**
> Do you know of a way to convert the dts into an .ac3 file that I can remux in with a .h264 file for streaming to a ps3?

I'm pulling my hair out trying to figure out how to convert dts to ac3.

Type man ffmpeg in console, or if you want an easy solution use avidemux's GUI. You can use it to copy the video codec into a new container while converting the audio, and it's scriptable.

---

### Post by Drenhead on 2009-03-30
I've tried avidemux, but it doesn't recognize the DTS stream and fails.  

I've demuxed the streams using Tsremux and remuxed them into a .m2ts file, but that file has no audio when I play it.  I'm not sure what is wrong with that.

---

### Post by Drenhead on 2009-03-31
Well, I got mkv2vob to work using Wine, so my problem is sort of solved.  

It would be nice to be able to figure out a native linux way to do it.

---

### Post by mvnoord on 2009-05-26
The "-af channels=6" option has no effect.  To enable the channel filter it needs to be inserted before the lavcac3enc filter.  I've also found that the channel mappings going from dts to ac3 are screwed up.  Here are the params that I use which seem to correct them:
```
-ac hwac3, -channels 6 -af channels=6:6:0:0:1:4:2:3:3:5:4:1:5:2,lavcac3enc=1:640 -lavdopts threads=2
```

---

