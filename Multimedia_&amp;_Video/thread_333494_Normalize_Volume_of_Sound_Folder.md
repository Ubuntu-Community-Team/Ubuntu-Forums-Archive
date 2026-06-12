---
title: "Normalize Volume of Sound Folder"
date: 2007-01-07
forum: Multimedia &amp; Video
---

### Post by SuperMike on 2007-01-07
Anyone have a script I can run that normalizes the volume of a folder (and subfolders) full of MP3s?

---

### Post by SuperMike on 2007-01-08
Found the technique:

1. Backup your MP3 folder somewhere else, just in case, and so you can compare the sound.
2. Flip on Universe option temporarily in /etc/apt/sources.list.
3. 

$ sudo apt-get install normalize-audio
$ normalize-audio -b ~/mp3/*/*.mp3

...this of course assumes you have an MP3 folder layout like:

~/mp3/<artist>/<song>.mp3

...and you can also try using -m instead of -b.

---

