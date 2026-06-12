---
title: "Wifi stopped working."
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by Moonlitflower on 2010-01-12
Here I am on my mother's computer because the internet/wifi signal on my laptop(netbook) stopped working altogether. Normally when i click on the little wifi icon, i get a list of signals to choose from under wireless networks. now under wireless networks, it just says wireless is disable. I dont understand how that could be, because i didnt purposely disable anything. I tried right clicking it  because I know that theres a box where you can check or uncheck networking /and or wireless. However, I am unable to click the box for "enable wireless". Enable networking looks normal, but enable wireless is dark and faded out. I have no idea what the problem is or else to do. Help T.T

---

### Post by changingstate on 2010-01-13
Could you open a teminal and post the result of 

```
sudo lshw -C network
```to give everyone an idea of what the computer is up to, please?

---

### Post by snares on 2010-01-14
if it's the Broadcom 43xx you might want to check the post I just did. Wifi seems to be effected by the latest kernel 2.6.31

[http://ubuntuforums.org/showthread.php?p=8664056#post8664056](http://ubuntuforums.org/showthread.php?p=8664056#post8664056)

---

### Post by Moonlitflower on 2010-01-14
When I put sudo lshw -C network i told me:
-network DISABLED
description: Wireless interface
product: AR9285 Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc. 
physical id: 0
bus info: pci@0000:02:00.0
logical name: wmastero
version: 01
serial: 00:25:d3:46:aa:63
width: 64 bits
clock: 33MHz
capabilities: pm msi pci express bus_master cap_list logical ethernet physical wireless
configuration: broadast-yes driver-ath9k latency-0 multicast-yes wireless-IEEE 802.11bgn
resources: irq:17 memory: fbff0000-fbffffff

I also typed in rfkill list which i got from the link and it says Soft blocked: yes Hard blocked: no
What does that mean?

---

### Post by changingstate on 2010-01-14
Could you try : 

> sudo rfkill unblock all and see if the result of rfkill list changes?

---

### Post by Moonlitflower on 2010-01-14
=O YOU FIXED IT!!!!!!!!!!!! THANK YOU SO MUCH!!!!!!!!!!! Nothing is "blocked" now and i can now click on wifi signals =D Thanks again

---

### Post by bgmainx on 2010-08-14
> **changingstate said:**
> Could you try : 

and see if the result of rfkill list changes?

The thread is kinda old now, but I got curious why does it blocks the network? My problem is similar : 1. Internet stops 2.The Wi-Fi indicates that no networks exists around 3. When I shut down and then turn on,  all the networks show up and everything's allright for unknown amount of time. :(

Wish you well. ^ ^

---

