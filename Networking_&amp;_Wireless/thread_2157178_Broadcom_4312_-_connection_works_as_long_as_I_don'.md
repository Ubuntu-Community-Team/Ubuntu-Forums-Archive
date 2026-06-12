---
title: "Broadcom 4312 - connection works as long as I don't try to use the internet?"
date: 2013-06-24
forum: Networking &amp; Wireless
---

### Post by Cursed Lemon on 2013-06-24
Having a weird issue with an older Acer Aspire 5516 laptop and the Broadcom 4312 chip in it. Using 12.04, currently. 

I've done a purge of the bcmwl kernel stuff with: 

```
sudo apt-get remove --purge bcmwl-kernel-source
```

Then used Synaptic to install b43-fwcutter and firmware-b43-lpphy-installer. 

My wireless connection works fine with regards to SSH'ing around the office network.

But as soon as I try to load Firefox, the connection cuts out and I have to flip the wireless hardware switch to get it to respond again. 

Any ideas? Will post additional information upon request.

---

