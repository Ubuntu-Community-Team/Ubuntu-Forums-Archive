---
title: "xmms-flac?"
date: 2005-10-20
forum: Multimedia &amp; Video
---

### Post by shortl on 2005-10-20
I can't seem to find xmms-flac or flac-xmms anywhere (in the Synaptic Package Manager).  I have two sound cards and flac is the only player where I know how to change sound cards--I like it anyway for the plug-ins and so forth.  Any help would be appreciated.  thank you, ls

---

### Post by Pablo_Escobar on 2005-10-20
You need to comment out the "universe" lines in Your /etc/apt/sources.list

Use "sudo gedit /etc/apt/sources.list" in terminal.
Then remove "#" signs from lines which say "universe" -> Save, voila :)

---

### Post by shortl on 2005-10-20
Thanks, somehow I got it myself--I think when I enabled the Universe repository to get Grip--but anyway there is was and didn't I feel like an idiot--live and learn--thanks, ls

---

