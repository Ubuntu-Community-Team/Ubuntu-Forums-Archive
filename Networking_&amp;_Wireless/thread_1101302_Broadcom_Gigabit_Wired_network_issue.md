---
title: "Broadcom Gigabit Wired network issue"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by Dakeyrus on 2009-03-20
Hi Guys,

First time listener, first time caller.  I am REALLY new to UBUNTU (Intrepid)and linux in general.  I recommended we install it on our raid server as we kept on coming up with a 10 user limit on XP Pro.

Anyhow got the desktop version installed OK and spent a day figuring out how to install and use SAMBA but got it all working in the end.  All our winXP Pro PCs could see it and read and write to the Ubuntu Raid machine.  The issue now is that the gigabit card is only being used in 100 mode full duplex.  I need it to go gigabit mode.

I have used ethtool to look at settings and try to change it to 1000 speed but when I do, the network icon top right disconnects and won't reconnect.  As soon as I change it back to 100, it finds itself again.

Installing GNOME device manager sees the network card as a Broadcom NetXtreme BCM5721.  It is seen on the system as eth0.

driver = tg3
version = 3.94
firmware version = 5721-v3.299

Any help would be greatly appreciated.

Dave

---

### Post by albandy on 2009-03-20
my proliant server has this one:
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5721 Gigabit Ethernet PCI Express (rev 21)
and it's working perfect at gigabit speed. Are you sure you've conencted the card to a gigabit ethernet port?

---

### Post by Dakeyrus on 2009-03-20
Thanks for the quick response...

I installed as a dual boot system with XP so same network cable.  On the winxp machine I use to access the ubuntu machine, I often save files in photoshop direct to the raid (ubuntu).  I notice now that if I try to RLE compress a B&W image as it saves to the raid, it takes a long time.

I am home for the weekend and won't be back at the ubuntu machine till monday.  I might boot into XP and confirm the gigabit connection.

---

