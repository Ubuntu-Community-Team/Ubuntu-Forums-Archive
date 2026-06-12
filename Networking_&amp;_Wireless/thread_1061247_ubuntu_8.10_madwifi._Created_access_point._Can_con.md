---
title: "ubuntu 8.10 madwifi. Created access point. Can connect to it but cant receive packets"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by eee1000huser on 2009-02-05
Hi All,

I'm trying to set up my machine as an access point. I have managed to do this using wlanconfig and iwconfig. I can see the access point advertised (essid) from another machine and I can connect to it. Since I have no dhcpd installed yet I manually set the IP addresses on both the client and ap.

When I ping the client from the AP the client can see the ARP requests (using tcpdump) and also replies to the ARP requests. The AP however never receives any of these replies (again checking using tcpdump).

When I ping the other way (from client to AP), then the AP never gets any packets.

I enabled some logging using athdebug (recv and recv_desc I think), and I can see in dmesg that packets are actually arriving on the wifi device. I can even see that they are coming from the correct MAC address.

The question is, why are these packets never delivered to ath0?

The wireless card I have is an AR242x 802.11abg.
I'm running a clean install of Ubuntu 8.10.

I've tried with the drivers it comes with (I can see ath0 and wifi0, so I assume this is madwifi not ath5k??).

I have also tried downloading the latest snapshot of madwifi-hal and compiling and installing that.

No difference noticed.

I also tried using easypeasy (booting from USB stick). the card is recognized, I think using ath5k since now the device is called wlan0. But I do not know how to put it in access point mode with this driver, or if its at all possible.


I think sticking with ubuntu 8.10 and wlanconfig etc would be best. Any ideas what I need to do to get the receiving of packets working?

Any help is much appreciated!


Cheers!

---

