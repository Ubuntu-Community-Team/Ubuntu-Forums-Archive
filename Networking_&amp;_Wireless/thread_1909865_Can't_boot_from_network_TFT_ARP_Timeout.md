---
title: "Can't boot from network: TFT ARP Timeout"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by Mikken on 2012-01-16
I am using Clonezilla SE to clone images. When I boot the client machine, i get PXE-E11: ARP timeout message. 

I got this working before the weekend, but now it just won't cooperate. There are no changes in the system that i know of. Where do i start looking? I'm not too familiar with networking, but the client machine seem to be getting the IP's right.

---

### Post by Mikken on 2012-01-16
Got it working by running configure again 

sudo /opt/drbl/sbin/drblpush -i

---

