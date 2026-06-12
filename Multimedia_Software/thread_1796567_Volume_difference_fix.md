---
title: "Volume difference fix?"
date: 2011-07-04
forum: Multimedia Software
---

### Post by bobman500 on 2011-07-04
Hey guys,

I use my laptop as kind of a media machine. It's plugged in in the bedroom and streams to the Playstation in the living room using Mediabox.
On the Playstation, there is very little difference, but on the laptop, depending on the disc/album/downloaded file, the volume differs WILDLY, which usually means that I turn the volume up to hear one thing, then blow my eardrums out with the next thing!

I was just wondering if there is any way, without having to, for example, feed each file through Audacity or something, that I could guarantee that the files are put out at the same volume?

p.s. Bear in mind that I am a beginner, so if I have to go through Terminal or something, I need it spelled out for me! Put it in shortcuts and technical terms and my brain will cry :confused:

---

### Post by CatKiller on 2011-07-04
It depends on what you're using to play them back, but most players have support for [Replay Gain]("http://en.wikipedia.org/wiki/Replay_Gain") tags. Personally, I use [EasyMP3Gain]("apt:easymp3gain-gtk") to tag the files with volume information. It handles a few file types, but not FLACs IIRC, so I do those at the command line.

---

### Post by bobman500 on 2011-07-05
I usually use Movie Player, and occasionally VLC for DVDs. How exactly do I go about adding replay gain tags?

---

### Post by CatKiller on 2011-07-05
> **bobman500 said:**
> How exactly do I go about adding replay gain tags?

Just stick them in EasyMP3Gain and analyse. That'll write the tags to the files. You can do it recursively and it will treat files in the same directory as from the same album. It doesn't handle FLACs, but you can do that with ```
metaflac --add-replay-gain
```Again, it will treat files in the same directory as being from the same album. Album gain tags are so that if you're listening to a whole album you still get the dynamic variation between tracks even though the volume of the album as a whole has been reduced to be at a similar level to all your other albums.

I have no idea if either VLC or Totem can read Replay Gain tags.

You also have the option to use EasyMP3Gain to change the contents of the file to normalise the volume. That is irreversible, though.

In principle, you could put a compressor in your signal chain, and then all audio would have the volume levelled. Easy to do with JACK, and I know you can do it with ALSA although I've never looked into how. There are lots of tutorials on having a system-wide equaliser and all you'd do is swap out the equaliser plugin for a compressor/limiter. 

Much simpler to use the tags and a player that supports them. That is what they're for, after all :)

---

### Post by bobman500 on 2011-07-05
So, will this only work with music? It didn't seem to like trying to load video files. Also, does it do it automatically? I don't seem to be able to find a "go" button.

---

### Post by CatKiller on 2011-07-05
> **bobman500 said:**
> So, will this only work with music? It didn't seem to like trying to load video files.

As far as I know. I don't watch much video on my computer, so I couldn't tell you what's available.

> Also, does it do it automatically? I don't seem to be able to find a "go" button.

Select Analysis -> Album analysis from the menu bar.

---

### Post by CatKiller on 2011-07-05
FWIW, PulseAudio remembers your volume settings on a per-application basis. So if your DVDs are coming up consistently louder than your games or whatever, you can turn down the volume of VLC and your DVDs will always be quieter.

---

