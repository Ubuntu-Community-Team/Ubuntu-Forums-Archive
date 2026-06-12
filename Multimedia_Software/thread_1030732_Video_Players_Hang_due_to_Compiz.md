---
title: "Video Players Hang due to Compiz"
date: 2009-01-04
forum: Multimedia Software
---

### Post by Macintosh SE on 2009-01-04
I have enabled "Visual Effects" on my Hardy Heron machine. When I play a large video file (recorded TV) or watch live TV, the system will hang at random times during playback. When this occurs, the video image freezes, along with all of my applets. The mouse can be moved but clicking has no effect. Audio from the file will continue playing. The system will un-freeze itself after a few seconds. During the "freeze" period, CPU usage is 100%. This occurs on all players (MPlayer, VLC, and Totem). How can I prevent this from happening (aside from disabling visual effects)?

---

### Post by 2hot6ft2 on 2009-01-04
Get a faster computer and/or graphics card. You asked.

---

### Post by 5n4K3 on 2009-04-06
> **Macintosh SE said:**
> I have enabled "Visual Effects" on my Hardy Heron machine. When I play a large video file (recorded TV) or watch live TV, the system will hang at random times during playback. When this occurs, the video image freezes, along with all of my applets. The mouse can be moved but clicking has no effect. Audio from the file will continue playing. The system will un-freeze itself after a few seconds. During the "freeze" period, CPU usage is 100%. This occurs on all players (MPlayer, VLC, and Totem). How can I prevent this from happening (aside from disabling visual effects)?
try with y xorg.conf
```

	Option 		"UseEvents"		"false"

```

> **2hot6ft2 said:**
> Get a faster computer and/or graphics card. You asked.
the most stupid answer that i've ever seen [-X

---

