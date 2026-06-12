---
title: "Software to turn one large mp3 into several small ones."
date: 2008-08-27
forum: Multimedia Software
---

### Post by cwrann on 2008-08-27
I have a large MP3 of a concert and would like to divide the songs into a separate file for each song. 

Anybody know a good application for this purpose?

---

### Post by calito on 2008-08-27
audacity. look for it in synaptic

---

### Post by vanadium on 2008-08-28
> 
audacity. look for it in synaptic 
This is fine, but will cause the need to decode the mp3, and reencode the audio again to mp3, which means: quality loss.

A tool like mp3splt can split your mp3 in different files without the need to decode. Split on silent points. Otherwise, slight gaps between tracks you will introduce will damage your listening experience.

The only tool that is capable of splitting mp3's gaplessly without the need to reencode is a java utility pcutmp3. These files can be played back gaplessly with audio software that knows to handle lame tags (and that playback software is unfortunately rare under Linux). However, you run into the same limitation when using the approach with Audacity.

---

### Post by cwrann on 2008-08-28
Thanks for the suggestions.

---

