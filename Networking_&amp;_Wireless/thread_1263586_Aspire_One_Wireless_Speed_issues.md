---
title: "Aspire One Wireless Speed issues"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by mspn on 2009-09-11
Hi,

Just signed up to the forum about 2 mins ago after browsing google for an answer and with no luck, so Hi!

I have Ubuntu 9.04 Netbook Remix on my Acer Aspire One A150 dual booting with Windows XP, and it works an absolute charm, with one slight issue.

In Windows XP my normal download speed from the web would usually limit itself to around 350KB/s, and being on a 6MB line this seemed ok to me. However when usoing Ubuntu my download speed usually goes as high as 980KB/s, which I thought was fantastic until I started downloading large files.

When downloading anything over around 30MB the connection is dropped as if the router is rebooting, and I wondered whether the router cannot handle the speeds Ubuntu is trying to achieve?

I have since booted back into Windows XP, and the same download limits at 350KB/s and will download happily until the end.

The file I have been trying to download for testing purposes through both OS's is the Ubuntu 9.04 Netbook Remix IMG file from Canonical UK.

**PROBLEM  SOLVED...**
I have now installed the mad-wifi drivers for he atheros card in my Aspire One A150. It seems that it was the default atheros drivers that were causing the connection to drop when encountering heavy traffic (ie. 900KB/s+ over a period of around 1 min.). I have now seen that this was an issue in previous releases of ubuntu, and I mistakenly thought it was solved in this version. Maybe it will teach me to read the instructions first next time!!

---

### Post by Xyphoid on 2009-09-17
I had the same problem a couple of months ago

[http://ubuntuforums.org/showthread.php?t=1135959](http://ubuntuforums.org/showthread.php?t=1135959)

Because of that (and the crappy Flash support for Linux) I changed to XP. I tried 8 distro's the last couple of days, but non of them solved the problem (or appealed to me enough).

If these two problems are solved, maybe more people will try out Ubuntu.

For now I'm back to XP :(

---

