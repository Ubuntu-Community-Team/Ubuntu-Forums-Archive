---
title: "Connecting to wireless AP, but DHCP doesn't work"
date: 2006-02-24
forum: Networking &amp; Wireless
---

### Post by NeoChaosX on 2006-02-24
Hardware:
Dell Inspiron 5100
D-Link DWL-G630 PCMCIA wireless adapter

I recently reinstalled Kubuntu, and I installed wpa_supplicant because my home network is secured with it. I've enabled wpa_supplicant, and have a block for my home network in /etc/wpa_supplicant.conf.  When I boot up, the computer connects to the access point on our wireless router just fine, with a good connection according to KWifiManager. However, DHCP does not work, so I can't go online. When I manually try to run dhclient, it ends up failing to find the DHCP on the wireless router for some reason,  creating this output:
```
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
However, I also have wpa_supplicant configured for several other outside networks (one is unencrypted, the other uses WEP), and when I'm connected to those networks, dhclient is able to find a DHCP and give me an IP address. So I'm stumped: I don't know what I'm doing wrong here that Kubuntu isn't able to find the DHCP server on my wireless router. What should I do?

---

