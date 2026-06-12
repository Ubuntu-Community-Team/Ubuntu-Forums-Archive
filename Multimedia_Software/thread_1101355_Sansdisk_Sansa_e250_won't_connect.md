---
title: "Sansdisk Sansa e250 won't connect"
date: 2009-03-20
forum: Multimedia Software
---

### Post by KCG102282 on 2009-03-20
My Sansdisk Sansa e250 won't connect using Ubuntu 9.04 Alpha 6. I did connect to Debian SID however so I know the player works and it is set to mcs. ANy Ideas?

---

### Post by mastermindg on 2009-03-20
Your distro is in Alpha, may want to open up a ticket in Launchpad. Not sure how this device connects, but if it's USB you can check if it's being recognized by using:

```
sudo fdisk -l
```

---

