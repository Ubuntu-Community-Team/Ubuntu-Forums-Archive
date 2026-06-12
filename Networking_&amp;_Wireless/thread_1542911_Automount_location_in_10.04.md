---
title: "Automount location in 10.04"
date: 2010-07-31
forum: Networking &amp; Wireless
---

### Post by kentcb on 2010-07-31
Hi,

In 9.10 I could access my auto-mounted network location with something like [FONT="Courier New"]/home/user/.gvfs/sharename[/FONT]. This was particularly useful for F-Spot because that's the only way I could get it to import photos from my server.

However, in 10.04 I no longer have a [FONT="Courier New"].gvfs[/FONT] folder and can't find a way to import photos from my server in F-Spot.

Can anyone shed some light on where this has moved to in 10.04?

Thanks

---

### Post by Morbius1 on 2010-07-31
That's not good. The ".gvfs" should have been there by default. All I can suggest is to make sure that you have the following packages installed:
```
gvfs
gvfs-backends
gvfs-bin
gvfs-fuse
```

---

### Post by kentcb on 2010-07-31
Thanks Morbius. All those packages are there. Accessing the network drive works perfectly fine from Nautilus. It just doesn't appear under .gvfs like it used to.

---

### Post by kentcb on 2010-07-31
I ran mount at a terminal with output:

```
gvfs-fuse-daemon on /home/kent/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kent)
```

But the directory did not exist. I rebooted my machine and mounted the network drive again and, lo and behold, this time it was available under .gvfs.

Hmmm, and I thought only Windows issues could be fixed by a reboot :)

---

