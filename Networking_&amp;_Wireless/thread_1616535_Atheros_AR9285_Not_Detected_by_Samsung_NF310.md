---
title: "Atheros AR9285 Not Detected by Samsung NF310"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by taiji_jian on 2010-11-08
Hi guys,

I recently got a Samsung NF310 netbook. It has a Broadcom 802.11n wireless card, which is not very well supported currently. In order to have reliable wireless, I switched it out with an Atheros AR9285 wifi card. The Atheros card seems to be invisible to the system. It doesn't show up in the output of lspci, and I can't find anything weird in dmesg. It's like it just doesn't exist. 

At first I thought the card was just dead, but then I tried it out in my old EeePC900 and it works fine. I know the slot on the the NF310 is OK, because the original Broadcom card still works. I also determined that the NF310 isn't doing some BIOS weirdness to only us the Broadcom card, because my AR5BXB63 802.11g card works in it. (Unfortunately it's a full-length footprint, and the NF310 has a half-length Mini PCIe slot, so I can't leave it in there.) 

The NF310 is running Maverick. The EeePC identifies the wifi card as:

Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

Anyone have any ideas what I should try next?

---

### Post by harmsma on 2010-11-19
Hi,

I also got the Samsung NF310, with the Broadcom wireless-N (bcm4313 if I remember correctly). On maverick the wireless works fine with the restricted drivers installed from the GUI. (I think the GUI installs bcmwl-modaliases and bcmwl-kernel-source.)

BTW, I installed using the maverick amd64 install disk, since the N550 atom is a 64 bit CPU.

---

