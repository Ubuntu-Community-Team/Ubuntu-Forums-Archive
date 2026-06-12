---
title: "Cannot play sound in gnome (permissions problem)"
date: 2008-10-31
forum: Multimedia Software
---

### Post by djvishnu on 2008-10-31
I've done a "command line only" install, and just installed x and gnome manually. "linux-sound-base" was installed manually as well. Sound works, but i have a problem:

When im in a console (not x), i can play sound and use alsamixer. When i startx, the gnome volume-applet cannot access the sound device, and i cannot play sound unless i "sudo mplayer something.mp3"

/dev/dsp has these permissins:
crw-rw----+ 1 root audio 14, 3 2008-10-31 12:14 /dev/dsp

I added myself to "audio"-group by
> sudo adduser joern audio

But this did not help. What is the proper way of allowing my user to play audio? Why does it work in the console?

---

