---
title: "Belkin USB Wireless (F5D7050E) on Intrepid"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by pcaritj on 2009-02-15
Hello everyone.

I am having an issue with the (in)famous Belkin F5D7050E. Mine has a USB ID of 050d:705e, so I gather that it is supposed to be natively supported under Kernel ver. 2.6.27.11 and higher. So, I installed that Kernel version (Amd64) and followed the instructions [here]("http://linuxsoftwareblog.com/blog/?p=30"). And, well, it kind of works :).

The adapter locates wireless networks with no problem, and even connects normally (with WPA2!). The only problem is that it can't reliably send and receive packets. For example, it attempting to browse the internet, sometimes it will display a page normally and quickly but, more often, it will sit for awhile resolving the domain name and then, transfer a little data, wait for awhile, and usually time out. I don't have the problem using the wired adapter on this machine, connecting wirelessly from other devices, or using the same wireless adapter on the same machine under windows.

I am using Ubuntu 8.10 (Intrepid), with kernel 2.6.27.11, AMD 64.

Has anyone else seen this? I'd be grateful for any input.

---

