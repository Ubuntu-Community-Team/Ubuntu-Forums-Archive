---
title: "Wired and wireless problems with Kubuntu"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by wong89138 on 2009-11-15
Hi,

I am very very noobish and would greatly appreciate any help at all.

I just installed Kubuntu 9.04 64 bit on my Acer Extensa 5420.  I have a Marvell Yukon 88E8071 PCI-E Gigabit Ethernet Controller and a Broadcom 802.11g Network Adapter.

Absolutely no wireless networks or devices show up, which is to be expected according to other forums.  But the wired should work automatically right?  When the ethernet cord is in, it shows that it is attempting to connect to eth0, but then it just gives up, and there's nothing in the KDE Control for any internet network whatsoever.

If there's any information I may have left out, please let me know.

Thanks!

Jason

---

### Post by Iowan on 2009-11-15
My laptop had Ubuntu Jaunty - it had [this]("http://ubuntuforums.org/showthread.php?t=1156441") problem.  If that doesn't help, post results of **ifconfig**. If the wired device shows no IP address, post results of **lshw -C network**.

---

### Post by wong89138 on 2009-11-15
Hi,

I got it to work.  Thanks anyways!

Jason

---

### Post by HunkirDowne on 2009-11-15
> **wong89138 said:**
> Hi,

I got it to work.  Thanks anyways!

Jason

Excellent!  How?

---

