---
title: "network printing problems"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by ottosykora on 2010-12-25
Situation:
PC1 , XP, h470 office printer from HP connected via usb

PC2, ubuntu 10.04 , connected to same network

can see shares on the XP from ubuntu

However can not connect to the HP h470 printer. The printer is set on XP so it is open to the network and it is the default printer on that machine.

What ever I try in the ubuntu, can not connect to the printer.

How is that done exactly?

---

### Post by drdos2006 on 2010-12-25
It is easier to maintain if your PC1 has a static IP address rather than a dynamic IP address from your router. Ubuntu would then connect to the XP attached printer via Internet Printing Protocol in this format:  ipp://<static-ip-address>:631/shared-printer-name.
See if you can use your browser to connect to [http://PC1-ip-address:631/shared-printer-name](http://PC1-ip-address:631/shared-printer-name)

regards

---

### Post by ottosykora on 2010-12-25
well this can be arranged, I can set fixed IP outside of the dynamic range.

It is just strange:
when trying to add new printer to ubuntu, one other PC shows 4 different protocols
AppSocket/HP JetDirect
Internet-PrintProtocol
LDP/LPR Host
Windows Printer via SAMBA

on the one I am trying to install the printer the last one (samba) is msissing.
Do I have to install something extra for that?

---

### Post by drdos2006 on 2010-12-25
From your Ubuntu machine select Internet Printing Protocol plus the IP address of your Windows machine plus port 631 plus your print-shared-name.

Result is:
 ipp://192.168.0.3:631/HP-shared
then Ubuntu will look for HP drivers.

regards

---

### Post by ottosykora on 2010-12-26
OK will try this one too, but meanwhile at least I realized that installing samba will not install the samba client automatically. So installed client, now samba line in the options, works fine this way too.
But sure, the ipp is more universal, will try with it as next.

many thnaks

---

