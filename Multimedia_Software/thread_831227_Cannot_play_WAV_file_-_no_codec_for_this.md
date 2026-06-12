---
title: "Cannot play WAV file - no codec for this"
date: 2008-06-16
forum: Multimedia Software
---

### Post by malanciault on 2008-06-16
Hi, I'm using Ubuntu 8.04 and I'm trying to play a simple WAV file. I opened it with Rhythmbox. I had the "Search for suitable codec" screen. I clicked OK but : "No matching application found".

I also tried to play it with Totem, and had this error:

"DVI ADPCM decoder plugin required"

What am I missing ?

Thanks !

---

### Post by Bungo Pony on 2008-06-16
What kind of .wav file is it? 16 bit or 32 bit?

There isn't a lot of support for 32 bit .wav files which could be your problem (I had a problem similar to this). Try playing it in Audacity. If it doesn't work in Audacity, try a different .wav file.

---

### Post by wolfen69 on 2008-06-16
add [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repos. then search synaptic for gstreamer. you can install the good, bad, and ugly.

---

