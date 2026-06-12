---
title: "Making electronic music"
date: 2007-07-27
forum: Multimedia Production
---

### Post by machoo02 on 2007-07-27
Ever since I was a DJ back in college, I've been interested in electronic music of all sorts (IDM, drum and base, ambient; artists such as Aphex Twin, Autechre, the Orb, Orbital, Future Sound of London, etc.).  Lately I've been wanting to play around with making my own, but I'm not sure where to start.  I know that Ubuntu Studio has many good audio programs available, but what would be the different parts of putting a song together?  What is the workflow, in other words?  Any insights, tips, or references would be greatly appreciated.

thanks!:guitar:

---

### Post by waxedwing on 2007-07-28
> **machoo02 said:**
> Ever since I was a DJ back in college, I've been interested in electronic music of all sorts (IDM, drum and base, ambient; artists such as Aphex Twin, Autechre, the Orb, Orbital, Future Sound of London, etc.).  Lately I've been wanting to play around with making my own, but I'm not sure where to start.  I know that Ubuntu Studio has many good audio programs available, but what would be the different parts of putting a song together?  What is the workflow, in other words?  Any insights, tips, or references would be greatly appreciated.

thanks!:guitar:

I've been pretty happy with ubuntu studio for music.  All you really need is hydrogen for drums, which has some great free drumkits.  Then for synths you can try ZynAddSubFX which has some really great sounds and microtonal ability. Rosegarden will handle your midi stuff.
Then to put it all together there is the awesome DAW, Ardour.  And then Jamin for mastering.

What I do is make a beat in hydrogen, export a wav.  Trigger multiple zsynths with rosegarden, and zsynth will also export wavs for you.  Then just throw the wavs into Ardour and mix it all together.

If you really want to get into some glitch and warpy stuff you could use pure data or supercollider, both in the repositories.  Not too fun to work with unless you are into programming though.

---

### Post by machoo02 on 2007-07-28
Cool....thanks for the info.  I'll have to add the audio stuff to my current install sometime soon.

---

### Post by stmiller on 2007-07-28
Ardour2 + every synth/audio plugin you can find in Synaptic.

---

### Post by conorkirk on 2007-07-28
To get some cool sounds you can get a Bitmap (Windows BMP Format) then do this:

cat /path/to/bitmap/image.bmp > /dev/dsp

You get some cool sounds.

You can do this with other **uncompressed** data too

---

### Post by machoo02 on 2007-07-29
Cool!!!!  A lot of the ones that I tried sounds like funky static, but a few of them had some nice clicks and beats to them.  Thanks for the tip!

---

### Post by luisbg on 2007-07-29
conorkirk : and to write this to a wav file?

luisbg

---

### Post by machoo02 on 2007-07-29
Install sox (in the universe repos) and record it like this:```
cat /your/favorite/bitmap.bmp | sox -s -b -t raw -r 8000 - out.ogg
```

the -r flag will adjust the sampling rate

---

