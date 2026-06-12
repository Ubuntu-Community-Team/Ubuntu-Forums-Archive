---
title: "Network adapter missing on an Abit IL9 Pro (Maverick)"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by matiasw on 2011-06-06
Hi,
I have an Abit IL9 Pro, but I'm having trouble with the integrated network adapter (a Realtek Gbit ether): It's not even visible in the output of lspci/lshw -C network. 

I used to have a different motherboard. After swapping mobos, the network adapter is simply missing as described. I've already got the latest BIOS, and the integrated network adapter is enabled in the BIOS. 
Any clues?

---

### Post by chili555 on 2011-06-06
> It's not even visible in the output of lspci/lshw -C Please show us:```
lspci -nn
lshw -C network
```Thanks.

---

