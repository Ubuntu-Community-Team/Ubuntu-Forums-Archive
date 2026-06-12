---
title: "Lots of dead drives in the /media folder"
date: 2010-06-24
forum: Multimedia Software
---

### Post by fabdango on 2010-06-24
Dudes,

I have lots of *ghost* drives on my /media folder and can't get rid of them.

I'm using Maverick now but the problem comes from Lucid. Any help?

[IMG]https://dl.dropbox.com/u/6111247/unmount-media.png[/IMG]

They're all USB drives: a Huawei mobile modem and an iPod Nano 4g.

---

### Post by VH-BIL on 2010-06-24
To delete a directory not owned by you
```
sudo rm -r <DIR>
```

or you can load Nautilus with admin permissions with:
```
gksudo nautilus
```

---

### Post by fabdango on 2010-06-24
It worked great! I thought those were drives to unmount, never thought of them as plain folders.

Thanks a lot, VH-BIL!

---

### Post by VH-BIL on 2010-06-24
Your welcome :)

---

