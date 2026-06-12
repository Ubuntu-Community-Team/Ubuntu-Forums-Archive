---
title: "A successful experience of bridging WPA wireless and wired Ethernet."
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by Boombino on 2011-02-21
Hello!
   I spent some time trying to bridge wireless interface, working in WPA-protected network and wired ethernet interface on my laptop. I think it would be useful to post here about my experience.

   So, we want to bridge wlan0 and eth0. Let's denote bridge interface with ethtowifi. In my case wlan0 is Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection, working through iwlwifi driver. WPA is handled with wpa_supplicant.

To obtain a bridge, we can, as page [https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge) instructs us, use this:
```
ifconfig eth0 0.0.0.0
ifconfig wlan0 0.0.0.0
brctl addbr ethtowifi
brctl addif ethtowifi wlan0 eth0
ifconfig ethtowifi up
```and it won't work in my case.

Here are the reasons:
   1. wlan0 interface won't authenticate to Acces Point (further denoted as AP), because EAPol messages get eaten by ethtowifi.
   2. AP will reject ethernet frames with MAC addresses different from those which are stored in its tables. And Linux bridges frames transparently - i. e. it doesn't change MAC adresses in frames, bypassing bridge. So, if I connect a new computer to my laptop through eth0 and want it to communicate with AP - AP will reject.

   The second problem is solved with ebtables as described here:
[http://wiki.debian.org/BridgeNetworkConnections](http://wiki.debian.org/BridgeNetworkConnections)

   The first problem is solved, in my case, by messing with wpa_supplicant. In order to make wpa_supplicant ethtowifi-aware, we have to invoke it with "-b ethtowifi" command line option. But that is not enough. This didn't work for me without ```
brctl setfd ethtowifi 0
```   Finally, here is essential part of my /etc/network/interfaces:
```
auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

auto ethtowifi
iface ethtowifi inet dhcp
pre-up ifconfig eth0 down
pre-up ifconfig wlan0 down
pre-up brctl addbr ethtowifi
pre-up brctl setfd ethtowifi 0
pre-up brctl addif ethtowifi wlan0 eth0
pre-up ifconfig eth0 0.0.0.0
pre-up ifconfig wlan0 0.0.0.0
pre-up ifconfig ethtowifi up
pre-up ebtables -t nat -A POSTROUTING -o wlan0 -j snat --to-src MAC_OF_MY_WIRELESS --snat-arp --snat-target ACCEPT
pre-up ebtables -t nat -A PREROUTING -p IPv4 -i wlan0 --ip-dst IP_OF_COMPUTER_BEHIND_eth0 -j dnat --to-dst MAC_OF_COMPUTER_BEHIND_eth0 --dnat-target ACCEPT
pre-up ebtables -t nat -A PREROUTING -p ARP -i wlan0 --arp-ip-dst IP_OF_COMPUTER_BEHIND_eth0 -j dnat --to-dst MAC_OF_COMPUTER_BEHIND_eth0 --dnat-target ACCEPT
pre-up killall wpa_supplicant
pre-up wpa_supplicant -Dwext -c/etc/wpa_supplicant.conf -iwlan0 -b ethtowifi -B
post-down ifconfig ethtowifi down
post-down brctl delif ethtowifi eth0
post-down brctl delif ethtowifi wlan0
post-down brctl delbr ethtowifi
```And it works. But I'm afraid it's ugly. I'd like to receive comments and suggestions on it.

---

### Post by yfx2 on 2012-06-05
hi, i have a similar problem, well almost identical but somehow i still got lost following your instructions, i followed the instructions by savage on [http://blog.tplus1.com/index.php/2008/06/13/how-to-connect-to-a-wireless-network-from-the-ubuntu-command-line/](http://blog.tplus1.com/index.php/2008/06/13/how-to-connect-to-a-wireless-network-from-the-ubuntu-command-line/) 
to connect to the network
i have a wireless network with internet i want to share with my lan with my ubuntu server and you seem like the genius to ask, if i copy your /etc/network/interfaces changing the path of the to where my supplicant file is located it still won't work, possibly because im not sure where i have to put this brctl setfd ethtowifi 0 or the bit above. and i doubt my ./wpa_supplicant.conf is the same as yours either

im quite new to linux so be gentle

Nik

---

