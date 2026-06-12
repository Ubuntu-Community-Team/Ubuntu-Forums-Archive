---
title: "sound doesn't work"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by sdd231163 on 2007-01-04
I'm running kubuntu edgy and the sound rarely works.
the sound card is on the mother board and aplay recognizes it.
I also have a 5.1 surround sound but when I tried setting that up it caused the knotify to start crashing.
Although the sound sometimes works, to get it to do so requires a reboot and luck.
please help.

---

### Post by Dekunuts on 2007-01-04
I had sound problems with two sound cards in my pc, but using UBUNTU. 

I think it's easier if you only use one for starters. Then what i did was reinstall the sound packages alsa-base alsa-utils and linux-sound-base. Under ubuntu removing these packages causes ubuntu-desktop and gdm to be removed as well, so i expect the Kubuntu versions of these things to be removed by that too, reinstall them too! 

then run alsamixer or something similar to make sure nothing you want to use is muted.

you can aslo check if your card is recognized by doing aplay -l

hope it helps a bit

---

### Post by sdd231163 on 2007-01-04
I think I've got one sound card but it is not separate from the motherboard.
I am actually running ubuntu with kdm added on.
alsamixer says that it should have a grey or green box under each sound bar but I can't see one.
I don't understand how it can be mute if I sometimes get the sound.

---

### Post by sdd231163 on 2007-01-04
sound seems to have been muted on alsamixer and other programs too.
Thanks for the help

---

### Post by Dekunuts on 2007-01-04
Glad it worked out;)

---

