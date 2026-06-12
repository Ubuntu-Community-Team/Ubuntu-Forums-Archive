---
title: "is there a way?"
date: 2013-01-05
forum: Networking &amp; Wireless
---

### Post by DatSik on 2013-01-05
I was just curious if there is a way to tell what kind of encryption a connection is using? even if im not connected to it can i see if it requires a wpe/wpa or other?

---

### Post by tgalati4 on 2013-01-05
Kismet provides details on wireless connections.  It requires some configuration and a wireless card that allows permissive listening--not all cards allow it.

---

### Post by haqking on 2013-01-05
you can use```
 iwlist wlanx scan
``` where the x denotes your adaptor will generate a list of aveilable networks and encryption modes.
airodump-ng
kismet
wicd

pretty much any wireless tool will tell you the networks available and the encryption mode in use, including the one built into your DE most likely such as network manager

---

### Post by steeldriver on 2013-01-05
there's nm-tool as well if you are running a recent version of network-manager - gives a list of SSID, mode, MAC, frequency, bitrate, strength, encryption type for all the APs that it can see

---

