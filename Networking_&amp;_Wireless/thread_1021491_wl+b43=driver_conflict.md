---
title: "wl+b43=driver conflict?"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by AJB2K3 on 2008-12-25
Would having both the wl and b43 modules loaded cause driver conflicts?
If so how do I remove the wl module (or even blacklist it)?

---

### Post by pytheas22 on 2008-12-25
Having them both loaded at the same time wouldn't cause a 'conflict' in the sense that there would be a problem or crash.  Rather, one of the modules (probably wl) would just take priority over the other, which would be ignored.

If you want to use b43 instead of wl, just run this command to blacklist wl:
```

echo 'blacklist wl' | sudo tee -a /etc/modprobe.d/blacklist
```

Also, remember that you need to download firmware for b43 before it will work.  To do that, run:
```

sudo apt-get update
sudo apt-get install b43-fwcutter
```

To know which driver you're using, check the output of the command 'lshw -C Network'; it will tell you which module is driving your card, as below:

```
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: **driver=b43-pci-bridge** latency=32 module=ssb
```

---

### Post by AJB2K3 on 2008-12-26
lshw -C Network
Matches your output but still can't connect to a secure ap.

---

### Post by pytheas22 on 2008-12-26
> Matches your output but still can't connect to a secure ap.

That's not necessarily the driver's fault.  It could be a problem with Network Manager, in which case using [wicd]("http://wicd.sourceforge.net") would probably yield better results.

If you can't see networks at all, that's probably because you still need to install firmware for b43.  But I'm assuming that you can see networks, just not connect.

By the way, is there a particular reason that you need to use b43 instead of wl?

---

