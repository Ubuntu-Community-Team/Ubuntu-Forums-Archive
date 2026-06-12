---
title: "CD sound passthrough not reaching SPDIF, while DVD's play normally"
date: 2008-02-24
forum: Mythbuntu
---

### Post by pnauta on 2008-02-24
I installed Mythbuntu 7.10 on a Nvidia 630a based mobo, and have SPDIF connected via optical output to a DTS receiver.  When I play a DVD or ISO, this works wonderfully, no complaints there. So, no hardware setup problems.  I even had everything setup correctly, including playing my music through this digital interface.  

This was until my daughter remarked that WMA files (no DRM) didn't play.  So, I selected some packages that should have resulted in WMA playback, and this didn't work, but also resulted that the music playback stopped altogether.  Even connecting the audio out / CD interface like it was before, renders no results.  No music from this box.  I even now see no spectrum display when attempting to play the list.  

I have noticed several other things, like the frond end being loaded 3 times (used ALT-TAB, and three cubes show up, which I can then shutdown with ALT-F4) and I now have to present a password.  Not the way it used to work.

Short of setting it up from scratch (and then redoing all the work like making my TV work over HDMI, reloading ISO's / MP3's etc) does anybody have any ideas?  I'm not totally stumped but lack the technical knowledge on Mythbuntu (Myth newbie, but less newbie on Linux), and troubleshooting is already taking some weeks now .  None of the ideas already found seem to apply in this case, so any help is welcome, including those pointers to the obvious.

---

### Post by pnauta on 2008-02-25
Well, even a new setup doesn't solve much.  DVD sound works, streams sound work, but the music player refuses.  Symptoms are that the visualisation does not show, so it looks like there&#347; no codec for whatever needs to be played.  This is true for MP3's as well as CD playback.

Solved the multiple frontend problem though...and no login required anymore.

---

### Post by fenian on 2008-02-25
Did you enable the proprietary codecs in mythbuntu control center?

---

### Post by laga on 2008-02-26
Hi,

there's a separate setting for the audio device for MythMusic. Maybe that's what's missing.

Have you read [http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound](http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound) and [http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound_with_AC3_and_SPDIF](http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound_with_AC3_and_SPDIF) yet?

I don't know how relevant those documents are because I don't own a AV receiver (yet), but they might be a good starting point.

Regards,

Michael

---

### Post by pnauta on 2008-02-28
I solved the problem.  Hindsight shows that the first article you mentioned gives an important clue: aplay was configured as using output device "standard".  How does it get there?  It is one of the values in the dropdown list that can be used in Mythmusic.  I used ALSA:default, and it works perfectly again.

---

