---
title: "k9copy does not copy sound from DVD to AVI"
date: 2011-02-17
forum: Multimedia Software
---

### Post by resander on 2011-02-17
I want to copy one track/chapter from a DVD to an AVI file, but the
sound is not copied only the video. I

  - selected track/chapter by clicking checkbox
  - selected 'MPEG-4 encoding' for output
  - used default settings (codecs were 'copy' for video and audio)
  - clicked DVD copy action

Result:  
   1.  Movie Player: no sound
   2.  VLC: Error message 'No suitable decoder module: VLC does
       not support the audio or video format "   ". 

How can I get sound and video?


P.S.
Using k9copy version 2.3.5.
I tried all audio codecs available in the k9copy Audio tab. 
They failed in the same way as before.

The chapter list contains 'audio 1 Unknown pcm 2ch 48kHz 16bps'.
I don't know how to interpret that.


Also installed and tried AcidRip and Dvd:rip. Sound worked fine for both.
AcidRip did not show any audio settings. Dvd:rip showed:

Select track: 1: xx lpcm 48kHz 2ch => 1
Codec:  MP3
Bitrate: 128   48kHz
Quality:  2
Filter: None, volume rescale only
Volume rescale: 0

Again, it does not mean much to me.

---

### Post by resander on 2011-02-18
This problem has been the topic of two threads last year:  

   May 23 2010 k9copy not copying audio    by gwi
   Dec 25 2010 K9copy won't include sound  by Jonny87

and not resolved.

Is this a (known) bug?

---

### Post by nypaulie on 2012-04-10
You have to change the default setting by checking the audio box (defaults to empty!) for each track you are copying. Just expand the dropdown directory to show it and put a checkmark in the audio box. The video boxes already have checkmarks. Took me some head-banging to discover this one. Also wasted a pile of blank discs. Hope this helps!:popcorn:

---

