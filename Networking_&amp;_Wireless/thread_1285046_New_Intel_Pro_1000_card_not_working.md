---
title: "New Intel Pro 1000 card not working"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by xtraspecialj on 2009-10-07
Ok, I found a post from 2006 under Networking & Wireless, but it being so old I didn't trust that the solution would still apply today.

I recently purchased an Intel PWLA8391GT 1Gbit Pro 1000 card for my Ubuntu 8.10 machine. I have installed it and it shows up in **lspci** as **Intel Corporation 8254PI Gigabit Ethernet Controller**.

Under **Ifconfig**, it is listed as **eth1** (I disabled my onboard nvidia lan in the bios,  that was eth0) and shows all the correct advertised speeds, **10Mbs, 100Mbs, 1000Mbs**.  However, under speed and duplex it simply says **Unknown!** and at the bottom it says **link detected: no**. However, on the back of the card, the yellow 1Gbit light is lit. Plus, it's a brand new cable and I have tried multiple known working ports on my router. In **/etc/network/interfaces** it appears to be set up correctly as eth1 with the correct static IP, subnet mask, and default gateway for my LAN.

Do I need to download a driver for it? I have found a linux driver on Intel's website, but before I go through all that, I want to make sure that it is necessary. So far my Ubuntu experience has been painless and it has recognized every hardware device I have ever put into this machine without having to download and install any special drivers. I can't imagine a simple $25 Intel brand card wouldn't be recognized and work immediately. 
Any suggestions from the experts?

---

### Post by xtraspecialj on 2009-10-07
My problem was a big ole' dumb human error on my part.  I didn't realize my motherboard had 2 LAN interfaces on it.  I was assuming that the new card was eth1, but it was in fact eth2.  So all I had to do was go into /etc/network/interfaces and activate the eth2 interface and poof!  it worked.  Oh well, my dumb quota for the day may already be filled.

My linux noobness continues.

---

