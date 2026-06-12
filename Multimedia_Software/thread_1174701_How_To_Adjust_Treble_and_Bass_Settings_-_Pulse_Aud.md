---
title: "How To Adjust Treble and Bass Settings - Pulse Audio"
date: 2009-05-31
forum: Multimedia Software
---

### Post by umechanism on 2009-05-31
I'm using Ubuntu 8.10 32 bit on a Dell desktop.  My sound works just fine except I can't find a way to adjust the treble and base in Pulse Audio.  I typed, "alsamixer" but only saw a master volume control - no tone, treble, bass...etc controls were there.

What do I need to do?

Thanks.

---

### Post by kostkon on 2009-05-31
You can access your volume using the gnome volume control, by right-clicking on your speaker icon in the system tray and selecting *Open Volume Control*.

Nevertheless, if you want to use *alsamixer*, to be able to access the volumes of your hardware (anyway, the volumes provided by the ALSA driver), try running it like this:
```
alsamixer -Dhw
```

Hope that helps.

---

