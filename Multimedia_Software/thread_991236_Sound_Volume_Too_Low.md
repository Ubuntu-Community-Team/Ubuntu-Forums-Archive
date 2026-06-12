---
title: "Sound Volume Too Low"
date: 2008-11-23
forum: Multimedia Software
---

### Post by jereece on 2008-11-23
I have an Acer Extensa 5620z laptop and I just installed Ubuntu 8.10.  The sound worked out of the box, but the volume is too low.  I have the master volume at 100% in Ubuntu.  When viewing a video on Youtube for example, I have that volume control at 100% as well.  The volume is so low that if the TV is on in the room, you won't be able to hear the laptop.  I realize laptops are not meant to be very loud but my speakers had more volume under Windows.  Is there any way to boost the volume of my sound card any other way?

Thanks,
Jim

---

### Post by morphos on 2008-11-23
Right-click on sound icon in status tray.

Choose 'Open Volume Control'.

Turn PCM and Front up.

If this solves your issue, please make sure to mark your thread [Solved].

---

### Post by blattengel on 2008-11-23
Try running alsaconf, then alsamixer from the terminal?

```
alsaconf
alsamixer
```

---

