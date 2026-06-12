---
title: "Mplayer's joystick support broken in 1.0rc2?"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by chmmr on 2008-01-12
A few months back, the repository version of Mplayer was updated from rc1 to rc2.  This seems to have broken the joystick support that worked fine for me before.

I'm not using any special settings, I just have a joystick at /dev/input/js0, which is the default for mplayer.  Again, it worked fine before.  Every other application that recognizes and uses the joystick, can.

I searched on the mplayer mailing list and found nothing.  If no-one here knows, is there any other mplayer support resource I can try?

---

### Post by chmmr on 2008-06-21
I forgot about this bug for a while, then realized it was still broken in Hardy.  I dug around some more, and found out that there's a ./configure option called "--enable-joystick", not enabled by default, that does just that.  When this isn't enabled, there's no "joystick device not found" error or anything, it just fails silently.

So the real problem was that the version of mplayer in the Ubuntu repos wasn't compiled with that option.  I'm not sure why it isn't on by default, but at least the Ubuntu versions should use it.

---

