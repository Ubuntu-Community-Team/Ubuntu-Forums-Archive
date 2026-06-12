---
title: "Wireless Not Detecting Any Networks (Ubuntu 10.10)"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by mirikaz on 2010-11-07
Hi all,

I'm new to ubuntu and have been having problems setting up my wireless connection on ubuntu 10.10. Essentially, the network manager on the top right corner doesn't seem to be able to see any wireless networks, though my other computer can see it fine.  I followed the instructions of some of the wikis, but still haven't figured out what's wrong. I'm currently using a d-link dwa-566, which I believe ubuntu has a pre-installed driver for.
-----------------------------------------------------------------------------------------------
iwconfig:
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.427 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
-----------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------
sudo iwlist scan:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results <== [not sure why this is happening]
------------------------------------------------------------------------------------------------

Please let me know if you need any more information. Would really appreciate any help, as I've been stuck for the past two days. Thanks!

---

### Post by uncaspi on 2010-11-07
Is it a laptop? Have you turned the card on on the keyboard?

---

### Post by mirikaz on 2010-11-07
Thanks for the reply. It's a desktop, so I assume it'll be on by default.

---

### Post by KresentPhresh on 2010-11-15
I'm seconding this issue in 10.10 - I'm on a D-Link DWL-520 PCI card in my desktop, hardware should be fine, but it won't show OR connect to any Wifi networks. I was having the same problem with the latest Fedora as well, only with Fedora, I could manually input the network that SHOULD be there and it would "connect," but as soon as it did, the system would go through a weird cycle of freezing for around 5 minutes (no mouse movement even) and spontaneously unfreeze for only a few seconds before freezing again. Dunno if that might make any sense to anyone.

Thanks in advance.

Ryan

---

### Post by uncaspi on 2010-11-15
Please post the content of /etc/network/interfaces

---

