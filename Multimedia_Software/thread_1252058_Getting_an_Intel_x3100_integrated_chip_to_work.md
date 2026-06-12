---
title: "Getting an Intel x3100 integrated chip to work?"
date: 2009-08-28
forum: Multimedia Software
---

### Post by Grimhound on 2009-08-28
I have a Compaq C712nr notebook computer with an Intel x3100 integrated graphics chip. I have just recently installed Ubuntu again, yet I think I've run into an issue. I am unable to switch through Visual Effects settings (with Ubuntu trying and failing to find drivers for the graphics), and moreso flash makes Firefox extremely laggy. I am curious if the two could have any connection, and if so how to make it so Ubuntu works with my graphics chip. Thanks for any help you can offer.

---

### Post by HappyFeet on 2009-08-28
[Here]("http://sourceforge.net/projects/kcheck/files/") is the .deb file for KernelCheck. Once you install it, it will allow you to download and install the latest kernel from kernel.org. Any problems should be fixed after that.

---

### Post by Grimhound on 2009-08-28
> **HappyFeet said:**
> [Here]("http://sourceforge.net/projects/kcheck/files/") is the .deb file for KernelCheck. Once you install it, it will allow you to download and install the latest kernel from kernel.org. Any problems should be fixed after that.

While it did fix the Visual Effects issue, it wiped out my Broadcom propriety driver for the wireless card that Ubuntu found when I first installed and any ability for me to recover it. I'm not that astute to know how to go about manually putting it in place. Mainly because the driverscape for that wireless card has about 50 different versions, many of which don't work or frequently fail.

---

