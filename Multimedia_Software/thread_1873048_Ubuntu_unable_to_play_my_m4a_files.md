---
title: "Ubuntu unable to play my m4a files"
date: 2011-10-31
forum: Multimedia Software
---

### Post by patman0623 on 2011-10-31
I can't figure out why neither Rhythmbox nor Banshee is able to play my m4a files. I have gstreamer-0.10-good|bad|ugly all installed. It just says "looking for plugin" and then it can't find one. It used to be able to play them.

---

### Post by ajgreeny on 2011-10-31
How about vlc, which can normally play just about anything?

---

### Post by mc4man on 2011-10-31
What you need installed is gstreamer0.10-ffmpeg, which very well may already be installed. So d. check there.

If installed & no playback then browse here & delete the registry.i686.bin file, the reopen your player(s) & try again
```
nautilus .gstreamer-0.10
```

---

### Post by patman0623 on 2011-10-31
> **ajgreeny said:**
> How about vlc, which can normally play just about anything?Yes; actually it does work in vlc.


> **mc4man said:**
> What you need installed is gstreamer0.10-ffmpeg, which very well may already be installed. So d. check there.

If installed & no playback then browse here & delete the registry.i686.bin file, the reopen your player(s) & try again
```
nautilus .gstreamer-0.10
```1) where is "here"? 2) can I have someone verify it's safe to delete that file?

---

### Post by mc4man on 2011-10-31
> **patman0623 said:**
> Yes; actually it does work in vlc.


1) where is "here"? 2) can I have someone verify it's safe to delete that file?

The location is your home folder > .gstreamer or just paste the above code in a terminal

Wouldn't tell you to delete something if it wasn't 'safe' to do so & hadn't done so here.

---

### Post by patman0623 on 2011-10-31
> **mc4man said:**
> The location is your home folder > .gstreamer or just paste the above code in a terminal

Wouldn't tell you to delete something if it wasn't 'safe' to do so & hadn't done so here.I'm just cautious about deleting anything based off what someone told me on the internet (especially a file named registry.i686.bin). But if it's in my home folder, no prob. Will do when I get home.

---

