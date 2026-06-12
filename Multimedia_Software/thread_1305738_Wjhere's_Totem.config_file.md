---
title: "Wjhere's Totem.config file?"
date: 2009-10-30
forum: Multimedia Software
---

### Post by Aero-Z on 2009-10-30
Hello,

I'd like to manually set the subtitles position but I can't find the configuration file. I've looked into /home/USER/.gnome2 but there's nothing about Totem.

Any tips?

Thanks

---

### Post by diesch on 2009-10-30
It's /apps/totem in gconf - use gconf-editor (GUI) or gconftool (command line) to modify it. But I'm not sure if you can modify the subtitle position there.

---

### Post by Aero-Z on 2009-10-30
> **diesch said:**
> It's /apps/totem in gconf - use gconf-editor (GUI) or gconftool (command line) to modify it. But I'm not sure if you can modify the subtitle position there.
But there're no options to set the subtitles position.

---

### Post by diesch on 2009-10-30
So I guess you can't configure that in totem.

---

### Post by Aero-Z on 2009-10-30
> **diesch said:**
> So I guess you can't configure that in totem.
I'm pretty sure I've done it in the past from a config file.

---

### Post by diesch on 2009-10-30
Are you sure it was Totem? VLC has such on option in ~/.vlc/vlcrc

---

### Post by Aero-Z on 2009-10-31
> **diesch said:**
> Are you sure it was Totem? VLC has such on option in ~/.vlc/vlcrc
I'm positive.

---

