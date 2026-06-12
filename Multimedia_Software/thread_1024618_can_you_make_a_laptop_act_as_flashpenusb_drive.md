---
title: "can you make a laptop act as flash/pen/usb drive?"
date: 2008-12-29
forum: Multimedia Software
---

### Post by notquitemichael on 2008-12-29
hi all,

after an up hill struggle trying to get my desktop to share files with my xbox 360, i realised that i could simply stick files on my usb drive and my xbox would happily mount it like a portable media player.

this also works, it turns out, with external hard drives. which is all good, but a tad argovating syncin' the disks etc.

so, does anyone know how to get ubuntu to share a drive/folder behaving like a external drive, then i would be able to simply plug my laptop via usb?

thanks,

---

### Post by atngplusultra on 2008-12-29
First off, if you've got one of those male-to-female USB cables - awesome.
But, uh, the first place I would personally look to set those kind of things would have to be fstab:
```
sudo gedit /etc/fstab
```

maybe, decide which USB port you'll connect to the Xbox to, and then put a pound sign ( # ) before it?

Fstab may be too drastic, though, I'm not certain.

---

