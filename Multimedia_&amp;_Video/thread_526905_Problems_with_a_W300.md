---
title: "Problems with a W300"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by carlosjoan91 on 2007-08-16
Hi i just purchased this music phone, and im running into a bit of trouble syncing music with ubuntu, as when i copy and paste a lot of songs in the phone, when i try to unmnount it, it just lasts forever, and if i disconnect before, i have nothing on the phone, and if i just copy one song, then the unmount lasts like 5 minutes, and i get it on the phone but with incomplete tags, (example, the song was named song the artist was named artist, and the album was named album, i get it in the phone as so by arti in alb) so im practically stuck with restarting in windows each time i want to sync, wich is a bit of a hassle, anyone has any idea why this happens? usb thumdrives work fine in ubuntu, and the phone and cable work fine in windows, so i have no idea =S thanks in advance

---

### Post by ddrichardson on 2007-08-17
Try mounting the device explicitly as vfat, like a usb disk:
```
mount -t vfat /dev/sdaX /mnt/player
```

---

### Post by carlosjoan91 on 2007-08-17
I found its actually because the phone has an awfully slow transfer rate, and thats platform independent, so actually i already ordered a USB 2.0 Memory stick writer to write things directly, the ms writer will appear in linux automatically, like a pendrive, right?

---

