---
title: "more sound problems, SoundBlaster ens1371"
date: 2006-07-26
forum: Multimedia &amp; Video
---

### Post by mojacks on 2006-07-26
I'm running Ubuntu 6.06 with a Soundblaster 16 bit PCI card and on startup it doesn't have sound.

I found a solution here that works to a degree. 
At the welcome screen I can press ctrl+alt+f1, go to the cli and do a
sudo modprobe -r snd_ens1371
sudo modprobe snd_ens1371

then I can go back to the GUI, log in, and I use the mixer to unmute everything and I have sound for that session.

With this work around, is it safe to assume Ubuntu recognizes the card and it works... I just have a problem with the sound module? How can I get it so the sound works everytime I log on without having to unload the module, reload it, then unmute everything?

Thanks

---

