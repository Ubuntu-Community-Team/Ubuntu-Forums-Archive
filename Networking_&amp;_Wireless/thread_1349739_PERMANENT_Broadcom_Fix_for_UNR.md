---
title: "PERMANENT Broadcom Fix for UNR"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by jared3000 on 2009-12-08
I'm trying to make my Broadcom fix permanent. I can bring the wireless card online quickly, but I need to re-enter some commands following reboot:

```
cd hybrid_wl
sudo modprobe lib80211
sudo insmod wl.ko
```I've tried out many of the offered fixes, but I invariably have to re-insert the code following reboot.

Is there a way to make the hybrid_wl PERMANENT?

I'm working with a mini Dell Inspiron 910 and the most recent UNR release.
EDIT: I should mention that the wireless card is Broadcom BCM4312 802.11b/g

---

### Post by jared3000 on 2009-12-08
OK... so I removed bcmwl-kernel-source from the list in Synaptic Package Manager, rebooted, re-installed the hybrid_wl fix for temporary internet, then reinstalled BOTH fwcutter and Broadcom STA drivers.

On reboot, it worked... I'll give it a go and repost

---

### Post by jared3000 on 2009-12-08
SUCCESS! :KS

Post below if this works for you

---

