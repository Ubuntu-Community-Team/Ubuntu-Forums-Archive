---
title: "Problem getting audio to work"
date: 2010-02-05
forum: Multimedia Software
---

### Post by blwnv8 on 2010-02-05
I just installed ubuntu on top of my windows xp on my laptop. I've got all the files I need to play mp3's i think. I'm using rhythmbox music player and the track play but I get no sound. Any ideas? Is there a better mp3 player out there? Thanks

---

### Post by saif_held on 2010-02-05
No sound as if there're no codecs to play MP3's? Or is there something wrong with your audio driver?

---

### Post by ajgreeny on 2010-02-05
Does rhythmbox appear to play with the position slider moving along the track, or does it just sit there and do nothing.

If the former, run alsamixer in terminal and see if you can find any sliders set too low or muted.  Use the cursor keys for moving from slider to slider and to raise and lower them, and "M" to mute/unmute any thay show with an M at the bottom that might be needed.  Tab will take you from **playback** to **capture** to **all**.  Alsamixer often shows sliders that you are not even aware exist, and can somethimes enable sound for users.  Esc will exit and should save settings.

---

