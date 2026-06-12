---
title: "No sound... except..."
date: 2009-04-26
forum: Multimedia Software
---

### Post by Sin@Sin-Sacrifice on 2009-04-26
So yeah... I have no idea how but all of a sudden I boot up and there's no sound. Except from audacious. I know I have audacious set to oss because of unresolved issues with pulse. I thought that was suffucient for a long time because I had sound from everything from movies to youtubeish videos and music software. About 3 weeks after the pulse problems I boot up and nothing from avis, youtube (and other stream sites), rhythmbox, amarok, and not even from my audio and video production software. Only audacious for some reason. I was thinking it was the oss setting but then I realized it worked for 3 weeks prior. Any clues?

---

### Post by Sin@Sin-Sacrifice on 2009-04-27
Thought a bump might catch the attention of someone that might know about this...

---

### Post by Sin@Sin-Sacrifice on 2009-04-28
Update: Audacious actually works with both oss or alsa plugin just not pulse audio. I've also found that the gui sound management shows an error on all "tests" : ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused 
``` Everything is set to the correct device and neither oss nor alsa are letting movies, streamed or not, games and other audio players make a sound. Audacious works flawlessly.

---

### Post by Scipio_Publius on 2009-04-28
seems like we might have a common bug.

[http://ubuntuforums.org/showthread.php?t=1139935](http://ubuntuforums.org/showthread.php?t=1139935)

---

### Post by markbuntu on 2009-04-28
If you are using Hardy studio then go here. It is a very long post but it will get pulse set up so you can use it with jack. You can probably skip over a lot of it but you will learn just about everything about how sound works in Ubuntu.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Sin@Sin-Sacrifice on 2009-05-01
Thanks markbuntu. Every things working now.

---

