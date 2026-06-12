---
title: "How Do You Increase The Quality Of Ogg Vorbis Audio Rips?"
date: 2009-07-02
forum: Multimedia Software
---

### Post by ebozzz on 2009-07-02
Hello All! I am doing some personal experimentation with audio file formats and I would like to know if anyone can share with me how to increase bitrate of Ogg Vorbis rips from it's default value of 160 kbps in Sound Juicer? Currently, all of my audio rips are 320 kbps MP3 files. Is it possible to obtain that same bitrate for Vorbis files?

Here is how the Ogg Vorbis profile is configured at this time.....

```
audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5 ! oggmux
```

I would appreciate it if someone could explain what values need to be modified to accomplish my task. Thanks!

---

### Post by ebozzz on 2009-07-02
I think that I figured out a way to get 320 kbps. I tried this first....

```
audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=[COLOR="Red"]1.5[/COLOR] ! oggmux
```

That profile gave me 112 kbps which was less than the default setting. So, I then changed it to the following....

```
audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=[COLOR="Red"]0.9[/COLOR] ! oggmux
```

Voila! I achieved 320 kbps in the Vorbis format. When I compared the same files to an 320 kbps MP3 file of the same track, I immediately found that the Vorbis file was the smaller of the two (MP3 - 13.5 MB; Vorbis - 10.4 MB). Now I need to listen to the audio comparisons for a period of time to see what my ears tell me. 

Ideally, what I would like to do is find a Ogg bitrate that is comparable to 320 kbps MP3. If I can use a lesser quality rip in Ogg to achieve that it would be great as I would save save a significant amount in storage without compromising the quality that I desire. At 320, it already saves space. I'll have to dabble with the profile a little more to see what the results are. If you peeked in here, thanks but I think that i have a handle on this now..... ;)

---

### Post by bobince on 2009-07-02
> **ebozzz said:**
> Ideally, what I would like to do is find a Ogg bitrate that is comparable to 320 kbps MP3.

You already have it. Vorbis at quality 0.9 is almost certainly better than CBR320 MP3, and well beyond transparency for almost all listeners/music.

320, whilst it is the ‘best’ quality the MP3 format can supply, is actually usually a terrible choice of encoding setting. It's way bigger than any sensible VBR setting, for very little gain in sound quality. Sometimes it can even be bigger than lossless (eg. FLAC) files! (In particular for simple sounds and silence, which FLAC will compress away to nothing, but a CBR codec will happily continue spitting out 320kb/s of data for.)

(It is a pity that certain MP3 download services seem to have settled on CBR320 for the reason of it being ‘best’. In practical terms it is close to ‘worst’. If you're going to use files that big you might as well go lossless; at least it's possible to transcode lossless files to a smaller size for portability, without incurring an additional quality loss.)

Vorbis uses VBR encoding by default and you'd be well advised to stick to that. You can ask it to encode to a fixed ‘bitrate=...’ if you really want to, but the results at any given filesize will be worse.

(‘quality=1.5’ shouldn't have worked and is probably a bug; presumably it wrapped around to 0.5.)

---

### Post by ebozzz on 2009-07-02
> **bobince said:**
> You already have it. Vorbis at quality 0.9 is almost certainly better than CBR320 MP3, and well beyond transparency for almost all listeners/music.

320, whilst it is the ‘best’ quality the MP3 format can supply, is actually usually a terrible choice of encoding setting. It's way bigger than any sensible VBR setting, for very little gain in sound quality. Sometimes it can even be bigger than lossless (eg. FLAC) files! (In particular for simple sounds and silence, which FLAC will compress away to nothing, but a CBR codec will happily continue spitting out 320kb/s of data for.)

(It is a pity that certain MP3 download services seem to have settled on CBR320 for the reason of it being ‘best’. In practical terms it is close to ‘worst’. If you're going to use files that big you might as well go lossless; at least it's possible to transcode lossless files to a smaller size for portability, without incurring an additional quality loss.)

Vorbis uses VBR encoding by default and you'd be well advised to stick to that. You can ask it to encode to a fixed ‘bitrate=...’ if you really want to, but the results at any given filesize will be worse.

(‘quality=1.5’ shouldn't have worked and is probably a bug; presumably it wrapped around to 0.5.)

bobince,

Thanks for the insight! Going forward I probably will rip into a lossless format and covert those files as needed for portability. This was more of just a test to see what I would like to use for portable devices such as mobile phones, MP3 players, etc.

BTW, here is the default Lossless profile in Sound Juicer....

```
audio/x-raw-int,rate=44100,channels=2 ! flacenc name=enc
```

Unlike the Vorbis profile, I don't see anything that can clearly distinguishes the output quality. I take it that the output would be basically the same as the disc that is being ripped, right? 

On that 1.5 quality issue, I just tried something to see if I could effect a change and it did give me something different than the default settings. I searched for while to see if there were more detailed instructions on modifying profiles in the audio extractor. I had no luck. Are you aware of any tutorials that do a good job of answering some of the questions that I initially posed? Thanks again....

---

### Post by bobince on 2009-07-02
> **ebozzz said:**
> Unlike the Vorbis profile, I don't see anything that can clearly distinguishes the output quality. I take it that the output would be basically the same as the disc that is being ripped, right?

Yes, that's what lossless does.

There is a ‘quality’ switch in FLAC, but this doesn't actually change the audio quality: it just tells the encoder to try harder to compress the file. It takes somewhat longer to encode and can result in a smaller file... although it's not very much different either way.

> searched for while to see if there were more detailed instructions on modifying profiles in the audio extractor. I had no luck.I guess the important bits for encoder settings are in the [gstreamer]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/") docs (see in particular base-plugins->OGG, good-plugins->FLAC and ugly-plugins->lame).

---

### Post by ebozzz on 2009-07-02
Understood. If you are an American and celebrate the 4th, I hope that you have a great holiday! If you don't celebrate it, just have a wonderful weekend! Thanks for your help....

---

### Post by nomnex on 2009-11-23
Not sure if you are still looking for information:

FLAC compression

```
audio/x-raw-int,rate=44100,channels=2 ! flacenc name=enc quality='n
```Replace **'n** with a number from 0 to 8

Lower number gives lower compression

Here for the documentation:

[http://flac.sourceforge.net/documentation_tools_flac.html](http://flac.sourceforge.net/documentation_tools_flac.html)

For general information about compression levels:

[http://www.hydrogenaudio.org/forums/index.php?showtopic=58731](http://www.hydrogenaudio.org/forums/index.php?showtopic=58731)

BTW from an audio perspective, Rubyripper is without comparison with SoundJuicer

---

