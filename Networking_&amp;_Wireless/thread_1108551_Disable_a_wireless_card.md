---
title: "Disable a wireless card"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by questworld on 2009-03-27
Hi all,

I am having very poor wifi reception in my room so reading few review and  posts in this forum I have bought Edimax EW-7318USG. It seems to work when I plug it in but I have to keep the laptop's inbuilt wireless on.

How do I disable my laptops in-built wifi adaptor and use the usb one ?

Thanks.

---

### Post by marco123 on 2009-04-09
> **questworld said:**
> Hi all,

I am having very poor wifi reception in my room so reading few review and  posts in this forum I have bought Edimax EW-7318USG. It seems to work when I plug it in but I have to keep the laptop's inbuilt wireless on.

How do I disable my laptops in-built wifi adaptor and use the usb one ?

Thanks.

I've been wondering about this as well and if they can conflict with each other.  Not much info on Google about this either.

Anyone got any ideas?

Cheers, Marco.

---

### Post by marco123 on 2009-04-09
Never mind I think the only way is to blacklist your device if you know what it's called.  It's a "half-baked fix" but it should work in the meantime until there's something better: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/286164](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/286164)

---

### Post by Michael.Godawski on 2009-04-09
hi questworld,

I had a similar problem once with my Broadcom in-build wireless card. I tried to blacklist the drivers for it, so that my usb dongle would work but to no avail.

In the end I had to manually remove the in-build card from the laptop. Not that elegant but it worked. I am also interested if there is another possibility to manage this issue. 

I remember that I even tweaked the bios settings...without results.

But we can try to blacklist the drivers of the in-build card:
Please post the output from this terminal command.
It will show us the current network settings. 
```
sudo lshw -C network
```

---

