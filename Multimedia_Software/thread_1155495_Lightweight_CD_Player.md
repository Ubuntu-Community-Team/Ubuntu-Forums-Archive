---
title: "Lightweight CD Player?"
date: 2009-05-10
forum: Multimedia Software
---

### Post by DnDer on 2009-05-10
I've put a music album in both my optical drives (one's CD-RW, one's DVD-RW) and Totem won't recognize it. I'm guessing that means it's not a replacement for something like iTunes. Can someone help me pick out what is?

I checked the linuxalt project and found several options, but I'm not too savvy. What would be the best one for a minimal usage type of player? All I really need is shuffle, repeat and play. I don't even need to rip music to my hdd.

So... from personal experience, what's the simplest player yo guys can recommend?

---

### Post by kerry_s on 2009-05-10
i use gnome-mplayer, it's in the repo, just look for it in synaptic.

---

### Post by andrew.46 on 2009-05-11
Hi DnDer,

> **DnDer said:**
> So... from personal experience, what's the simplest player yo guys can recommend?

To go really minimal you can play cds from the commandline:

```
mplayer -cache 2048 cdda://
```

There are a few options that can be added in but I don't believe that tracks can be 'shuffled'. I am ready to be proved wrong :-).

All the best,

Andrew

---

