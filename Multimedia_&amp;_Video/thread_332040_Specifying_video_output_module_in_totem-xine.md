---
title: "Specifying video output module in totem-xine?"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by wisam on 2007-01-05
I want totem-xine to use the xshm video output module instead of the default xvideo. Normally I would start xine as follows
```
xine -V xshm video_file.avi
```

I don't seem to find a way to let totem pass arguments to xine. 
Specifying the video output module in ~/.xine/config makes xine use it by default, but not Totem.

Any ideas?

---

### Post by ziri on 2007-12-24
Edit the file ~/.gnome2/Totem/xine_config

---

