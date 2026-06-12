---
title: "soundconverter hanging"
date: 2009-12-12
forum: Multimedia Software
---

### Post by verdomde on 2009-12-12
hey, i've had this problem quite a while, different computers, and different distros, im trying to convert my (massive) music collection to a single format, its all different types, many duplicates, i got no tags, and the file hierarchy is all messed up.

SO im using soundconverter (sound_K_onverter just copied to static noise previously, so dont want to risk it again)
However, when i try and import my entire music collection to be converted it turns grey and hangs, sometimes even when i only import a few it hangs (it wont go near my u2 folder).
anyone any clues?
getting tired of importing 3 folders at a time and having to reboot when it goes awry!!
Thanks for listenin
Paul

---

### Post by kassoulet on 2009-12-14
Try running: ```
soundconverter --jobs 1
```
This will disable multiple jobs at the same time.
Please report here if it worked, thank you ;)

---

### Post by 4leite on 2009-12-30
I had the same problem and this fixed it for me.

---

### Post by verdomde on 2010-07-12
Just an update to this proble, I had a chat with the guys at soundconverters home, berlios.de, they say it's a memory problem, soundcon tries to load it all into memory and uses too much or something, so there is no fix at the moment, unless they are doing something about it in the upgrades at some point, guess my collection is just too big. Trying to work out why i have no extensions on the music files anymore now, i think it was soundconverter...

---

