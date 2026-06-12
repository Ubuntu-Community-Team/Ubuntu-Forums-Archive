---
title: "trouble with cinelerra"
date: 2007-09-10
forum: Multimedia Production
---

### Post by tipdrinker on 2007-09-10
I've finally managed to get cinelerra installed in ubuntu studio but its running at a snails pace. was just wondering if anyone knew some typical problems that would be causing this. 

My computer is only about 6 months old and is a dual core and all so i know it should be able to handle it. any help would be fantastic as i have a few important professional editing jobs that are being put on the back burner because of it...

any feedback would be great.

---

### Post by cotcot on 2007-09-11
It is not clear what is running slow : the whole program or for instance only play back in the compositor window. I had problems with stalling of the playback in the compositor window and got it solved by enabling Settings > Preferences > Playback select ALSA sound driver check tab labeled "Stop playback locks up". (it was on a gentoo box : cinelerra on feisty is running well)

---

### Post by tipdrinker on 2007-09-16
well i figure out what the problem was, When i was importing media it was creating a new track for each file (nearly 200) so i changed the settings when importing media and its running fine now...

---

### Post by aouie on 2007-11-07
Though not your specific problem, there may be another common problem that people may encounter. I noticed my 64-bit Cinelerra used to be much slower (three times as long??) than my 32-bit Cinelerra (on the same computer). Though I haven't confirmed it, this was probably due to improper OpenGL support on that installation (since I use a newer computer, I didn't test it).
Sincerely,
Aouie

---

