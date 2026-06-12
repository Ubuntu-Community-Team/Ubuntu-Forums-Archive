---
title: "optimize music for mp3-player - which app/script?"
date: 2011-11-10
forum: Multimedia Software
---

### Post by daniel227 on 2011-11-10
hello,

i'd like to optimize some of my music for my mp3-player.
i mean: 
1. normalize and/or boost
2. convert to a lower (but bearable) bitrate
3. (if possible) do some tweaking, i think compressing, before normalising.

the main reason is that the player has a limited output volume and i'd like to have all songs equally loud and as loud as possible.

i spent some time googling, browsing the packet manager and forums, and came up with this: 
- a2mp3, a command-line thingy which, i think, only changes bitrate and only accepts mp3 and ogg as input
- gnormalize, which seems to be more suitable and has a satisfyingly complex gui; but somehow the things i want are greyed out. duh.

so, some gui or no-gui app, or a script (maybe for audacity), anything you can think of?

thx,

daniel

---

### Post by alex2399 on 2011-11-11
Normalizing can be done with mp3gain, converting with Soundconverter. For compression I wouldn't know, but search for LADSPA in the Software Center, though this seems like overkill for such a simple task.

---

### Post by MoreOrLess on 2011-11-11
Personally, I would just use ffmpeg (make sure you have lame encoder package).
```
ffmpeg -i input.mp3 -ab <desired_rate> output.mp3
```
where desired rate is in bits/s (e.g. you would use 128k for 128kbps).
Then you could just make a little script with mp3gain and ffmpeg to optimize a batch of mp3's to your desired format.

---

### Post by daniel227 on 2011-11-12
thanks to both.
it looks like even with a gui i can't avoid serious work.
i will give it a go, and i will also try creating some kind of batch operation for audacity.
i'll get back to this later.

heiho.

daniel.

---

### Post by Chronon on 2011-11-12
I have found Foobar2k to have a very fast replaygain scanner.  I was able to quickly apply replaygain tags to music files in formats including Ogg Vorbis, FLAC, m4a (with LC-AAC), mpc, mp3.  It's a viable GUI option for batch scanning your entire library and it runs great via wine.

I think you can use it to transcode files too, but I never used it for that.  My portable audio players run Rockbox, so they can handle all of the above formats.  I think Clementine can probably transcode on the fly while syncing to an audio player.  If it has a replaygain scanner it could be a good option too.

---

