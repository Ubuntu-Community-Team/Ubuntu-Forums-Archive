---
title: "Skipping Oggs"
date: 2011-10-18
forum: Multimedia Software
---

### Post by Steeperton on 2011-10-18
I've ripped a lot of my music to ogg, as it sounds better to my ears that mp3 at the same bitrate (160kbs). They were all ripped using grip.

However, when using Banshee or Clementine to play them back, I get a number of small skips in each track. I don't get this on Rhythmbox, using the "crossfading" back end (but do with this option turned off). vlc plays fine.

I've used oggz-validate on these files, and I get an error about packets out of order. Tried to fix it with oggz-sort, and no difference. Also tried to re-rip, and still no joy.

Any ideas on how to fix?

---

### Post by andrew.46 on 2011-10-18
Can you post one of the troublesome files somewhere?

---

### Post by Steeperton on 2011-10-19
Here's an example - the skipping starts approx 20 seconds in:
[http://www.megaupload.com/?d=O49B81ZF](http://www.megaupload.com/?d=O49B81ZF)

---

### Post by andrew.46 on 2011-10-19
Interesting, this files plays fine here on a variety of media players although I will admit that I do not have either Banshee or Clementine installed. I have produced an ogg of the same track from a flac backup using oggenc and AoTUV libvorbis without using ReplayGain (used in your example). See if this is any different on the troublesome players:
```

wget http://www.andrews-corner.org/tmp/Diamond.Eyes.ogg
```

---

### Post by Steeperton on 2011-10-20
> **andrew.46 said:**
> Interesting, this files plays fine here on a variety of media players although I will admit that I do not have either Banshee or Clementine installed. I have produced an ogg of the same track from a flac backup using oggenc and AoTUV libvorbis without using ReplayGain (used in your example). See if this is any different on the troublesome players:
```

wget http://www.andrews-corner.org/tmp/Diamond.Eyes.ogg
```

Thanks Andrew - yours works fine, so it must be a problem with my rip.

I tried removing the replaygain tags on mine and it's still there, so the only difference is AoTuV... 

Is this thread still valid for compiling it?
[http://ubuntuforums.org/showthread.php?t=1137670](http://ubuntuforums.org/showthread.php?t=1137670)

I'll give that a go then.

Thanks!

---

### Post by andrew.46 on 2011-10-20
Good to hear we are on the right track :). The AoTUV thing might be a red herring (much of the AoTUV magic has previously been absorbed into libvorbis), although I believe the thread you mentioned would be the way to go and certainly the patch I posted there should still be valid. But perhaps simply try your available tools first for a *test* run?

Hopefully you have access to your original cd? Rip the first track to your computer in wav format, a command like the following will do this:

```
cdparanoia "1"
```

and then simply run oggenc (which is part of the vorbis-tools package) across the file. Run oggenc in the following way:

```
oggenc cdda.wav -q 6 -o output.ogg
```

and then see if there are any playback problem with this file. If the file is ok you could either do it all manually, which I will admit is the way I do it, or use a ripper/converter like abcde for which there is a configuration file for ogg here:

[http://www.andrews-corner.org/abcde.html#ogg](http://www.andrews-corner.org/abcde.html#ogg)

or perhaps somebody who knows a little more about grip might be able to sort out how grip is mangling your files!

---

### Post by Steeperton on 2011-10-21
Andrew - Thanks for your help - doing it manually like you've said, still produced the skips. But then I updated to AoTUV, and it's all great now. Finally! I've been banging my head over this for ages!

Unfortunately, I now need to re-rip all my discs, but that's a small price to pay. Strange that some players (including my Rockboxed iPod) would play it fine though.

Thanks,

---

### Post by andrew.46 on 2011-10-21
Indeed it is all a little odd, but sounds like the issue has been resolved :).

---

