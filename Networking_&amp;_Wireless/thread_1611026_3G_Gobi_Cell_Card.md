---
title: "3G Gobi Cell Card"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by Z.K. on 2010-11-01
I have a 3G Gobi 2000 Cell Card and I was wondering if anyone knows how to get this card to work in Ubuntu 10.04.  It is made by Qualcomm.  I have searched on the Internet and saw that a lot of people have been having trouble getting this card to work.  Lsusb does detect the hardware, but there does not seem to be any native drivers for it in Ubuntu.

---

### Post by Z.K. on 2011-02-01
> **Z.K. said:**
> I have a 3G Gobi 2000 Cell Card and I was wondering if anyone knows how to get this card to work in Ubuntu 10.04.  It is made by Qualcomm.  I have searched on the Internet and saw that a lot of people have been having trouble getting this card to work.  Lsusb does detect the hardware, but there does not seem to be any native drivers for it in Ubuntu.

Okay, I gave up on this card and went to a MC5720 Sierra Wireless card.  This one is much easier to work with and just works in Linux.  

The only annoyance I have and it is not related to the card is that if you modify the Interfaces file for instance using a static address on a second Ethernet port, the Network Manager sometimes disappears and there is no way to get it back.  If I go clicking around where the icon is supposed to be, I can sometimes get the menu to come up so I can connect to my broadband connection.  So, I am looking into controlling the connections via the command line.

---

