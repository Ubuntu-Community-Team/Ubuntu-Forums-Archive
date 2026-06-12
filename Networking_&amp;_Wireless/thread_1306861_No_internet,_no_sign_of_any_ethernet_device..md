---
title: "No internet, no sign of any ethernet device."
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by rsheridan6 on 2009-10-30
I have a new installation of Karmic in which there is no internet connection. The motherboard is a GIGABYTE GA-EG43M-S2H LGA 775 Intel G43 (copied from the product page at newegg where I got it) with onboard ethernet - Realtek 8111C according to newegg. But I can't find any sign of it. lspci shows no ethernet device. ifconfig shows "lo" but that's all - no "eth0" or anything else. dmesg | grep -i eth shows nothing. 

The machine is hooked up to a live ethernet wire which is known to be good, but the motherboard itself has never been used, so it could be defective.  There is a green light right next to the ethernet cable that does come on when I plug in the ethernet cable.

This is a brand-new install of the final version of Karmic that was released yesterday - no Windows or anything other than Ubuntu here.

I was under the impression that lspci should show a device whether there's a driver problem or not. Does the lack of anything under lspci mean that I have non-working hardware?

---

### Post by Iowan on 2009-10-30
Although it probably won't reveal any extra information, **lshw -C network** *should* give specifics on network devices.

---

### Post by rsheridan6 on 2009-10-30
Unfortunately, that command doesn't turn up anything either.

---

### Post by ninjatiger422 on 2009-10-30
> **rsheridan6 said:**
> Unfortunately, that command doesn't turn up anything either.

Do  you have a non-released-yesterday OS that you can use to see if it detects your hardware?

---

### Post by rsheridan6 on 2009-11-01
I had the same problem with Karmic alpha 5, and I couldn't even get Jaunty to install.  I guess I'll try another distro or a BSD next.

---

