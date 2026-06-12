---
title: "wireless internet connection"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by Mystiques on 2010-03-23
Hi!

my wireless chipset is Intel corporation PRO/wireless 3945ABG (Golan) network connection (rev 02)

However, my question was how can i connect my wireless to the internet as with window vista it auto-detects the wireless. But with linux i have to configure the wireless so i can be able to surf.

I would appreciate if you provide assistance.

---

### Post by n0dix on 2010-03-23
Did you see if there is a private driver for your hardware?
Intel hardware has great support in Linux. 
Do you attempt to connect with network manager?

---

### Post by TBABill on 2010-03-23
Easiest is to just try the network icon in the upper right. Right click it to make sure wireless is enabled. Then left click to connect to a network. If you see it grayed out or no networks available, you most likely need a proprietary driver. Easiest then is to just connect to your router via ethernet cord and allow the system to download updates and prompt you to install proprietary drivers. For most cards it is that easy, but some can require a bit more work so post your results and ask for further assistance if you still can't get it up and running.

---

### Post by Mystiques on 2010-03-23
I have tried to use the following command 
#iwconfig
lo  no wireless extensions

eth0 no wireless extensions

wmaster0 no wireless extensions

wlan0 IEEE 802.11abg ESSID:"DLINK_WIRELESS"
         Mode:Managed  Frequency:2.412 Ghz Access Point:Not-Associated
         Tx-Power=0 dBm
         Retry min limit:7 RTS thr off Fragment thr=2352 B
         Encryption key off
         Power Management: off

---

### Post by n0dix on 2010-03-23
But the commando don't connect you. Is only to see the wireless connections you have. Try with the Network Manager applet, is a tray icon.

---

