---
title: "fstab entry for a drive that is shared"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by thomashw on 2010-03-20
I have a secondary HDD that I'm auto-mounting on boot. I also want this drive to be accessible over my network.

Right now I have it auto-mounting correctly, but whenever I try to access a shared folder over the network I get the error "Failed to mount Windows share".

I'm guessing the drive isn't being mounted correctly. I need it to have "guest" access... or something.

Here's my fstab entry:

```
/dev/sdb1 /media/sdb1 ext4 auto,users 0 0
```

Any ideas? :)

---

