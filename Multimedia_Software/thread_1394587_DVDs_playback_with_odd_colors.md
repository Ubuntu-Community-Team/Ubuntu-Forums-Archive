---
title: "DVDs playback with odd colors"
date: 2010-01-30
forum: Multimedia Software
---

### Post by diablo75 on 2010-01-30
I recently upgraded my girlfriend laptop to 9.10 and now, for some odd reason, when she plays DVDs on her laptop (the most recent attempt was the latest Harry Potter movie) the movie would play back fine but the colors for everything were way off.  I've re-added the medibuntu software sources to her system and applied all available updates but it didn't help.

This problem did not occur on my own computer when attempting to play the exact same DVD.

Any ideas about what I can try to fix this?

---

### Post by gradinaruvasile on 2010-01-30
What programs have you tried? I found mplayer to be the best. 

Have you installed the w32codecs package?

---

### Post by diablo75 on 2010-01-30
> **gradinaruvasile said:**
> What programs have you tried? I found mplayer to be the best. 

Have you installed the w32codecs package?

I've tried playing DVDs with both mplayer and VLC.  I've also tried to purge w32codecs (which were already installed) and libdvdcss2, and then reinstall them both... Didn't work.

:(

EDIT:  Uploaded a couple screenshots to show you what it looks like.

---

### Post by gradinaruvasile on 2010-01-30
The image has reversed color values. Interesting... I attached the image with 180 hue applied in Gimp...

Is there some setting wrong with the playback hue?
In totem (movie player) go to edit -> preferences ->
 display. The bottom setting is for hue. It should be in the middle.

On another note: install smplayer. Its the best player around if you ask me.

PS. You may check the video driver - it also has hue settings separately for video playback -  at least nvidia's control panel has it.

---

### Post by diablo75 on 2010-01-30
> **gradinaruvasile said:**
> The image has reversed color values. Interesting... I attached the image with 180 hue applied in Gimp...

Is there some setting wrong with the playback hue?
In totem (movie player) go to edit -> preferences ->
 display. The bottom setting is for hue. It should be in the middle.

That did the trick.  Hue was slammed all the way to the right so I just clicked on the "Reset defaults" button and it solved the problem.  VLC even plays the movie just fine now.  Didn't have to make any further adjustments or change settings in VLC either.

Thanks a million for the help!!!  Time for movies:

:popcorn:

---

