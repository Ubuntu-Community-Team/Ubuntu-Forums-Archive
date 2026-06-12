---
title: "mpd_status in Conky"
date: 2011-02-12
forum: Multimedia Software
---

### Post by clicker4721 on 2011-02-12
I'm using Conky [NightDrive]("http://goo.gl/m7oDd"). I absolutely love it and I've come leaps and bounds in configuring it to work with my system, but I have one hurdle left yet:

If MPD is playing, it shows the play arrow and gives album art and track information.
If MPD is paused, it shows the pause double-bar lines and give album art and track information.
If MPD is stopped, it does the same thing as if it's off.
If it's off, it shows a blank-cover album.

Is there any way I can make the following true? ```
${if "mpd_status" == "Stopped"}
```

---

