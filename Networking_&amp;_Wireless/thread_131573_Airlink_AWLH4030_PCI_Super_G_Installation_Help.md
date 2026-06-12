---
title: "Airlink AWLH4030 PCI Super G Installation Help"
date: 2006-02-16
forum: Networking &amp; Wireless
---

### Post by oneybm on 2006-02-16
Been awhile since I've gotten to play with my Ubuntu box; however, I have recently bought the aforementioned wireless nic for my system and it works in Windows of course. I did my research and made sure this card was supported and it appears that Ubuntu does detect it as I can type ifconfig and get information on the NIC but it doesn't ever show me as connected or getting an ip address from my router.

If I look at the Network Administrator tool it shows the card as activated and I can put in the ESSID. I didn't use WEP or WPA as I have MAC filtering enabled and will be playing with WEP/WPA later after some other tweaking on a third system being put in the network later on.

Did I miss something or overlook a post on this already that may be able to help me out?

*****Information from me posting in Desktop Support incorrectly*****

Post a couple of things if you wouldn't mind. Can you post the output from 
Code:
sudo ifup wlan0replacing wlan0 with the interface name if it's something different. If that gives you an error, make sure the system knows the card you're using by typing 
Code:
lspciand posting that.


do ifup ath0 comes back saying interface ath0 already configured. 

lspci gives back quite a bit of information but concerning the NIC it shows 

0000:00:08.0 Ethernet Controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

---

