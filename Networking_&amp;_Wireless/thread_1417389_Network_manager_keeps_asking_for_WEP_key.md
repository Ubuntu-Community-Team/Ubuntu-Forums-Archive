---
title: "Network manager keeps asking for WEP key"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by norky on 2010-02-27
Hi, 

Since the last update the 'wireless network authentication required' box keeps asking me for my wep key.  Everything was working fine previously,  I've even re-installed ubuntu just in case it was something I did....again everything was working OK until I installed the latest Nvidia drivers and updated ubuntu.

I can see my wireless connection when I click on the network manager icon I just wont connect.

Wired connection works fine.

05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

I'm using a revo 3610.

Thanks in advance for your help.

Norky

---

### Post by bruno9779 on 2010-02-27
Try right clicking on the network manager icon, and click "edit connections"

then go to the wifi TAB and delete all the wireless profiles there.

then try to connect again.

My wife seems to have this issue every once in a while, and I usually fix it like this

---

### Post by Xantane on 2010-03-11
I'm having the same issue but the card is :

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01

- Device: eth2 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl

---

### Post by Xantane on 2010-03-11
> **Xantane said:**
> I'm having the same issue but the card is :

0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01

- Device: eth2 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
i forgot to mention that the problem seems to be after an update to the Kernel/restricted module headers

---

