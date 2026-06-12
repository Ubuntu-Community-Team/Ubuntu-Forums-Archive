---
title: "I have VLC installed but I can't find it."
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by LoganT on 2006-06-17
So I went into Synaptic Package Manger and installed VLC, but when I go into Applications>Sound And Video it's not there.

---

### Post by x64Jimbo on 2006-06-17
You might need to add it manually. Not all packages have instructions about what menu they're supposed to go in. Sounds like you're using Gnome, so I can't be of any assistance as to *how* to do this, but it should be relatively simple.

---

### Post by tronica on 2006-06-17
it will be in apps - sound/video. you might restart and it will restart. or you can launch it from the terminal, just type vlc. or use Alacarte menu editor to add it to the menu.

---

### Post by LoganT on 2006-06-17
Okay, I tried Alacarte Menu Editor but couldn't find VLC. I typed in vlc in the terminal and vlc popped up but it was the "skins2" version (The one that looks like it's meant for Macs) and if I exit the terminal it exits the player.

EDIT: Restart worked. :)

---

### Post by Galban on 2006-06-17
If you really have it properly installed you should find it at /usr/bin/vlc. From there you can open it or, thereafter just build a launcher on your desktop. Any ways, this is the VLC's HowTo from the Unofficial Ubuntu 6.06 Guide.

```
sudo apt-get install vlc vlc-plugin-*
```

Then you should find it at:

Applications -> Sound and Video -> VLC Media Player

---

