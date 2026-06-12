---
title: "No wired lan working"
date: 2013-07-08
forum: Networking &amp; Wireless
---

### Post by phifgo on 2013-07-08
Hi all ., I am on Ubuntu 13.04 64 bit.    It's a coup;le of months that I didn't use my wired connection  (I Think before upgraded to 13.04) . today I discovered that Ubuntu doesn't  recognize my LAN  card, No eth0, Nothing  on lspci/lshw -c network. Anyone can help me? I ve followed 2 tutorial but no result :(
My laptop is a HP Probok 4530s with Core i3 2310M. any suggestion?

---

### Post by Cheesehead on 2013-07-08
If it's not seen by lspci, lsusb, or lshw, then it's a dead-hardware issue instead of an Ubuntu issue.
If the item is seen, but unrecognized or misconfigured, then it's a kernel issue.

Boot into your BIOS, and see if it's there among the boot options.
Try a LiveUSB and see it it's seen there.

And start looking up "how to disassemble my laptop" videos on YoutTube while your new motherboard is shipping to you.

---

