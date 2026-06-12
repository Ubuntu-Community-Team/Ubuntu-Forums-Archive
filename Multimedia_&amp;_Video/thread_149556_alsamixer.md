---
title: "alsamixer"
date: 2006-03-24
forum: Multimedia &amp; Video
---

### Post by fabien on 2006-03-24
Does anyone know a way to restore the default alsamixer configurations? I've been tweaking with the sound slides in alsamixer (PCM, wave, wave surround, etc.), but i think my sound is worst than it was when i installed Ubuntu and configured it to use ALSA!

Thkz in advance....

---

### Post by japs_it88 on 2006-03-24
I had a similar problem recently, and the solution i found in the #ubuntu chat was to reinstall the kernel

```
sudo apt-get --reinstall install linux-image-(kernel version)
```

It worked for me. Hope this will be helpful.

---

### Post by fabien on 2006-03-24
[QUOTE=japs_it88]I had a similar problem recently, and the solution i found in the #ubuntu chat was to reinstall the kernel

```
sudo apt-get --reinstall install linux-image-(kernel version)
```

It worked for me. Hope this will be helpful.[/QUOTE]

Isn't that a little bit extreme?
I thought that kind of configuration was stored in some 'conf' file, and that the simple fact of removing that file would force ALSA to reverse to it's original configuration (just guessing here, though :-k ). Besides, i've updated my kernel and nothing happened in alsamixer...

Anyway thanks for the tip! If i reach my 'maximum point of desperation', i'll use it, for sure ;) 

[]s

---

