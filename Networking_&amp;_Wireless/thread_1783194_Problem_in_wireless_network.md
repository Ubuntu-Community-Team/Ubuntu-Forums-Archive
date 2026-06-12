---
title: "Problem in wireless network"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by shivaraman on 2011-06-15
Hi,
 
I recently installed ubuntu 11.04 in desktop.The PC has netgear wireless card.But it is not working.Pl help...
 
Thanks in advance.

---

### Post by TBABill on 2011-06-15
Is this a USB device since it's a desktop? if so can you open a terminal and enter this command, then paste the results back here? The command is ```
lsusb
``` which is LSUSB in lowercase. If it's an internal card, then instead use ```
lspci
``` which is LSPCI in lowercase. Those commands will list (ls) your devices whether USB or PCI.

---

### Post by shivaraman on 2011-06-15
Thanks for your reply.Its Ethernet controller: Marvell Technology Group Ltd 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

---

### Post by TBABill on 2011-06-15
If you look at this link you'll find it only works with Windows drivers for your card as of Feb 2011. [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEncore](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEncore)
 
There's a link to the thread where instructions are contained to help you get it going.

---

