---
title: "Rhythmbox doesn't recognize audio CD"
date: 2009-12-26
forum: Multimedia Software
---

### Post by gazer22 on 2009-12-26
After I've inserted an audio CD into the computer, Rhythmbox does not recognize it, and therefore can't play it.

Relevant debugging information from the rhythmbox:
```
(13:43:00) [0x9a26028] [dump_volume_identifiers] rb-removable-media-manager.c:642: unix-device = /dev/sr0
(13:43:00) [0x9a26028] [rb_removable_media_manager_add_volume] rb-removable-media-manager.c:687: Unhandled media

```

Nothing else in the log implies anything else going wrong.

Amarok does recognize the CD, but I'd rather stick with Rhythmbox.

Rhythmbox 0.12.5
XFCE 4.6.1
Kernel 2.6.31-16-generic
Xubuntu/Mythbuntu 9.10

Any thoughts?

---

