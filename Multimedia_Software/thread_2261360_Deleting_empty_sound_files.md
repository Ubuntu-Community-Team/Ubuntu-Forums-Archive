---
title: "Deleting empty sound files"
date: 2015-01-18
forum: Multimedia Software
---

### Post by M1GEO on 2015-01-18
Hello.

Really quick question.  I have a script (arecord/lame) that's recording people talking in a room using a system of microphones into a soundcard.  Works great.  Issue is, for large amounts of time, there is no sound, just background noise.  Is there a way I can detect if the amplitude of a mono sound recording goes above a threshold, ultimately with the view of deleting "quiet" files to save disk space.

The files are MP3 files, written with lame, and are broken into 10 minute chunks. I'm happy to uncompress them back to wav to check the audio levels.  Just something that's like "threshold_audio --th 0.3 somefile.audio" and have it return 0 or 1 or something I can use (grep/awk) to find the answer?

Kindest regards

George, M1GEO.com

---

### Post by ajgreeny on 2015-01-18
Have a look at **mp3splt** (not a typo in the name; it is mp3splt, not mp3split) which will split mp3 files in many different ways including silence detection.

It does not normally decode and re-encode in order to do this, though it has to decode to carry out this silence detection. I am not sure if it then has to re-encode, or if the decoding is just to get the silence timings.

It is a command line app that I have used a huge number of times, though never for that purpose; more usually to split a large file of a whole side of a vinyl LP that I have recorded to an old audio CD recorder and then ripped to mp3.  I did try the silence detection for that but the LPs were not of good enough quality to get a consistent level for the "silence" between tracks, so I simply used the time options of mp3splt instead.

---

### Post by M1GEO on 2015-01-19
That looks very useful, thanks. I will have a look into it over the next few days, and report back with findings.

Cheers! :)

---

