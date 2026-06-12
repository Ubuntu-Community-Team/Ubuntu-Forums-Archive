---
title: "AW-NE766 (Ralink 2860) not detected?"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by not.robb on 2010-05-13
I have an EEEPC 1000HE that has an AzureWave AW-NE766 wireless card. As far as I know, the card is based on the Ralink 2860 chipset.

It always worked fine under eeebuntu 3.0, but I just installed Ubuntu NBR 10.4 and now it's not detected at all. 

Kernel : 2.6.32-22-generic i686

lspci and lshw show no mention of wireless card at all. Network-manager and wicd both show wired connections, but no mention of wireless at all. 

I followed the instructions on the "Solved" post to install the latest Ralink driver from Jan 29. It all went fine, except "ifconfig wlan0 up/down" and "ifconfig ra0 up/down" both return  "ERROR while getting interface flags: No such device"

Any thoughts on how to tell Ubuntu that I have a wireless card in there?

---

### Post by not.robb on 2010-05-13
Argh. My bad -- The wifi radio was not turned on. 
I noticed that the blue light under the wifi icon was not on, so I tried FN-F2 and baboom - blue light. Now I can bring ra0 up and down and see the wireless card in lshw. 

Now to get network-manager or wicd to see some wireless networks.....

---

