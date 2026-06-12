---
title: "cannot unpause in splayer (with space)"
date: 2011-02-28
forum: Multimedia Software
---

### Post by pickarooney on 2011-02-28
This has started happening recently - when I pause a video in smplayer with the space bar I cannot unpause it with the same key. 

The keyboard shortcut is definitely set to play/pause with space. The same problem occurs with left-mouse click, which is also set to play/pause. 
The version installed is 0.6.9 (SVN r3447) 

Is this a known bug or something wrong on my system?

I also sometimes have a problem with splayer jumping into the background when I try to skip forward or backwards with the mouse wheel but this is probably unrelated.

---

### Post by pickarooney on 2011-03-01
Does anyone know of a PPA for Maverick that includes a more recent version of Smplayer?

---

### Post by SeijiSensei on 2011-03-01
[This](https://launchpad.net/~rvm/+archive/smplayer) is the developer's own PPA.  However the most recent version there is 0.6.9-1 for Lucid, which I believe is identical with the repo version.  It runs fine in Maverick.

Perhaps your problems are actually with mplayer?  Try playing a video from the command prompt with "mplayer /path/to/video/file" and using the space bar to pause/play.  Do you get the same behavior as you see with smplayer?

---

### Post by pickarooney on 2011-03-01
I found a similar reported problem on another forum and the advice was to change output audio to pulse (previosuly alsa). Doing this, the audio now resumes on unpausing but the video stays frozen for a few seconds.

---

