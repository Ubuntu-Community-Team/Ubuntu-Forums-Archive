---
title: "Apple Lossless (ALAC) Support?"
date: 2006-12-12
forum: Multimedia &amp; Video
---

### Post by jcq on 2006-12-12
OK, forgive me if there's an answer to this somewhere that I've just missed.   What (if any) support is there for decoding Apple Lossless (ALAC) files under linux?   I've seen some conflicting info as I've searched around, so I'm hoping to see what the current status is.  I'm opposed to lossy formats, and though I don't currently have an iPod, I'd like to keep whatever digital rips I do in a format that's compatible with one I might get in the future.   I found a DirectShow filter that allows me to play them under Windows MCE, but since I intend to also be running Ubuntu on my new machine, I'd like to find a solution that will work here as well.    I most likely will install Wine, Crossover, or something similar, but I'd rather have a solution that didn't rely on running iTunes under that.

Thanks in advance...

---

### Post by tbroderick on 2006-12-12
You can decode ALAC, I've never used ALAC so I can't tell you how good/bad it is. It's not in the repo so you can go here to download.

[http://craz.net/programs/itunes/alac.html](http://craz.net/programs/itunes/alac.html)

If you are looking for a good free lossless codec then try FLAC.

---

### Post by jcq on 2006-12-12
I wouldn't mind using FLAC, but I don't relish the thought of re-ripping everything if/when I get an iPod.  :(

Is there a reason this can't be put into the package repository?   I mean, I can certainly do it manually, but why not make it more seamless for folks?   I'm new to Ubuntu, so I don't know all of the guidelines for what makes it in and what doesn't...

---

### Post by MetalMusicAddict on 2006-12-12
Because ALAC is a proprietary codec. Ubuntu only ships free (libre) applications.

I would really encode to FLAC. You can play 'em on ANY OS no problem.

Wait. FLAC isnt supported by the iPod unless you have Rockbox installed.

---

### Post by logos34 on 2006-12-13
Decoding: Most of my music lib is in apple lossless and I have alac playback in Amarok, Audacious, BMPx, but the tags aren't being read right (no bitrate, sample rate, just track, artist. album).  Temporary problem, i hope.  In windows i have alac plugins for winamp, nero among others, and playback, tags are perfect.  

Check this out: [http://crazney.net/programs/itunes/alac.html](http://crazney.net/programs/itunes/alac.html)

Personally I'm in no hurry to switch to flac because 1) apple lossless is well-regarded -- right up there with monkey's audio/ape if i'm not mistaken, and 2) according to the above link, its only a matter of time before there's an open-source encoder.

---

### Post by jtfolden on 2006-12-18
After installing the GStreamer .10 Good, Bad, and Ugly packages from the repositories I have no problems at all playing ALAC files in RhythmBox. The tags seem to be read just fine, too. (except for bitrate it seems, but I've noticed that iTunes doesn't always read the bitrate properly from ALAC files made with other sources, either, so nothing unusual here).

I have to agree with a few other posters here in that FLAC is not an answer. I have a 300GB drive full of ALAC encoded music and I'm not about to re-rip all that into a less well supported format for my needs (not to mention lose iPod compatibility).

What I really need is a decent encoder for ALAC when ripping under Ubuntu, or at the very least something that will do m4a... so far I've been rather unlucky finding anything to do m4a.

---

### Post by tbroderick on 2006-12-18
> **jtfolden said:**
> 
What I really need is a decent encoder for ALAC when ripping under Ubuntu, or at the very least something that will do m4a... so far I've been rather unlucky finding anything to do m4a.

There won't be any native Linux app that will encode ALAC. Encoding is closed source. Complain to Apple. Your only chance is if you can find a windows program that can encode ALAC and run it under wine. For m4a, you can use faac to encode.

---

