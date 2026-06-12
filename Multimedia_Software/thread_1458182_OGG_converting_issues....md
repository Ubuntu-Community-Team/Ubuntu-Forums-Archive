---
title: "OGG converting issues..."
date: 2010-04-19
forum: Multimedia Software
---

### Post by omelette on 2010-04-19
When I use **'WAV Breaker File Splitter'** to divide large WAV's (22,050Hz) into equal parts and recode them as OGG files, invariably, up to half a second of audio is missing from each piece when played back. When listening to audio-books, this can amount to 1-2 words, which can be confusing and annoying.  Initially I was recoding with 'Fairstars Audio converter' via Wine and presumed this was a Wine glitch of some kind.  However, after installing the Linux applications, **'Sound Converter'** & **'OggConverter'**, I'm dismayed to find the very same thing is occurring!  Note that the big WAV is split perfectly - using 'Sound Converter' to recode to MP3's results in perfect and seamless playback.

So, I'm trying to establish is this a bug with the OGG codec itself (unbelievable that something this 'big' could have been missed!) or is it down to little/no checking/debugging by the application coders?

---

### Post by omelette on 2010-04-23
Bump!

Let me take another crack at explaining this.  First, I find this problem is not confined to OGG files, MP3's also suffer the same fate.

The problem; WAV files (which themselves play back perfectly) when converted to either OGG or MP3 formats *regularly* have one quarter to one half of a second of audio missing _from its end._  Ironically, I find that the "experimental" AMR codec encodes the WAV file perfectly!  As an experiment, I have taken a massive WAV (100's of megs) and steadily 'split' a piece off, encoded it as MP3/OGG and checked the result for 'completeness' - right down until the piece I am encoding is just a few megs in length.  What I find is that unless the WAV being encoded is very small (a few megs) there will be an incomplete OGG/MP3 file.  And this seems to happen with both Linux (encoding with SoundConverter/OggConverter) & WindowsXP (encoding with Fairstars Audio Converter).

What I don't understand is how this could have been missed.  It is one thing for MP3/OGG formats to be "lossy" by nature, another thing entirely when they don't encode parts of the audio to begin with!  And this is particularly noticeable where audio-books are concerned. (as opposed to music)

Is it possible that there is the same buggy source libraries in use for encoding MP3/OGG formats???

---

### Post by omelette on 2010-04-23
Bump!

Let me take another crack at explaining this.  First, I find this problem is not confined to OGG files, MP3's also suffer the same fate.

The problem; WAV files (which themselves play back perfectly) when converted to either OGG or MP3 formats *regularly* have one quarter to one half of a second of audio missing _from its end._  Ironically, I find that the "experimental" AMR codec encodes the WAV file perfectly!  As an experiment, I have taken a massive WAV (100's of megs) and steadily 'split' a piece off, encoded it as MP3/OGG and checked the result for 'completeness' - right down until the piece I am encoding is just a few megs in length.  What I find is that unless the WAV being encoded is very small (a few megs) there will be an incomplete OGG/MP3 file.  And this seems to happen with both Linux (encoding with SoundConverter/OggConverter) & WindowsXP (encoding with Fairstars Audio Converter).

What I don't understand is how this could have been missed.  It is one thing for MP3/OGG formats to be "lossy" by nature, another thing entirely when they don't encode parts of the audio to begin with!  And this is particularly noticeable where audio-books are concerned. (as opposed to music)

Is it possible that there is the same buggy source libraries in use for encoding MP3/OGG formats???

---

### Post by ron999 on 2010-04-23
Hi
I can't explain what's causing the fault.

But maybe you could try recoding the whole file first, then split the recoded file into equal parts after.

---

