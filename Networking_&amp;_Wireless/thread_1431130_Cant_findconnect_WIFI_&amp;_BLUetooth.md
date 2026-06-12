---
title: "Cant find/connect WIFI &amp; BLUetooth"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by Pezza on 2010-03-16
I have ubuntu installed 9.04 and couldnt get wifi working.. I also had  bluetooth working.

Now I installed or updated to 9.10 version and still cant get wifi  started. I cant even turn it on or find networks etc. Im confused bad.

Also when updating I have lost bluetooth. How do I get both of these  working..

So confusing,

Now if I could have a step by step process, even if someone makes a video..

There are so many threads out there on this and none of them a good, 
we need step by step. videos as well..

It would make things so much easier.

---

### Post by AlanR8 on 2010-03-16
What sort of machine? What sort of network card?

---

### Post by Pezza on 2010-03-16
It is a 10"  netbook no name brand.

where do i find the network card im using?

---

### Post by AlanR8 on 2010-03-16
Try issuing the following command in terminal:

> lspci

When I did that on my Compaq Mini, the last few lines said:

> 01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
02:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)


Please copy and paste your output then people can point you in the right direction!

---

### Post by Pezza on 2010-03-17
hello,
I typed it in and got this..

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
user@user-laptop:~$ 


this is while im plugged into etho cable

---

### Post by Pezza on 2010-03-18
Can Anyone help?

---

