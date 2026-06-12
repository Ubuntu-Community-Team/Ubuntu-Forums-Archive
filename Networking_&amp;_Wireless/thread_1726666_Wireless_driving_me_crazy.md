---
title: "Wireless driving me crazy"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by dougao06 on 2011-04-11
Hello,

sorry to bother, I've been looking on internet for days now, tried everything (maybe too many things) and still can't get my wireless to work as it should.

At the moment I don't have wireless at all, I blacklisted a driver that the sticky post said, namelythe r8192se_pci below, but although the net8192se is installed in ndiswrapper, it shows as if I have no internet at all.

```
net8192se : driver installed
    device (10EC:8172) present (alternate driver: r8192se_pci)

```

If I unblacklist this driver, then I have internet, but quite slow, and worse, from time to time it shuts down, which makes downloading anything from internet impossible. A reason from this is that a iwconfig (now when I use it doesn't show any wlan0) shows bit rate at 1 MB, which I suppose it is too low (I tried to change it, but it doesn't work).

Any extra information I need to post please say so, the board is Realtek RTL8191se.

Thank you,
Pedro

---

