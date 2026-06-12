---
title: "Surround sound stops working after kernel upgrade"
date: 2013-06-22
forum: Multimedia Software
---

### Post by smilingfrog on 2013-06-22
This is for my own benefit, as I remember researching it before, and then forgetting how I did it.
Lots of guides on how to get surround sound to work in Ubuntu 10.04. I'm still using it. Unfortunately, really hard to get an easy solution by googling. I may find this in the future.

My problem is when I upgrade to a new kernel, the surround stops and alsamixer reverts to two channels.

for me, this works:
```

sudo apt-get install build-essential linux-headers-$(uname -r) linux-backports-modules-alsa-$(uname -r)

```

Then reboot. 
Surround sound returns.

---

