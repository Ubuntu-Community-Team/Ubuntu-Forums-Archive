---
title: "problems with wda-2320"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by gakuma on 2009-02-11
I cannot for the life of me get my wda-2320 to accept and maintain a connection with the access point. It currently will not attach to the access point when I use iwconfig. And even when it is connected to the access point (according to iwconfig) it won't ping other computers on the network and I get the error 'destination host unreachable'.  

I'm running it with the ath5k driver found in the linux-backports-modules-intrepid-server (2.6.27.11.14) package. 

It worked fine for several hours yesterday, and I tested it with elinks. And then it just decided to take a massive dump on me.


(uname -r)

2.6.27-11-server

(ifconfig)
wlan0 
Link encap: Ethernet HWaddr: 00:22:60:4f:5f:58
inet addr: 192.168.0.12 Bcast: 192.168.0.255 Mask: 255.255.255.0
UP BROADCAST MULTICAST   MTU: 1500 Metric: 1
RX Packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0
TX Packets: 0 errors: 0 dropped: 0 overruns: 0 carrier: 0
collisions: 0 txqueuelen: 1000
RX bytes: 0 (0.0 B) TX byes: 0 (0.0B)


(iwconfig)
wlan0
IEEE 802.11 bg ESSID "Motorola"
Mode: Managed Frequency: 2.412 GHz Access-Point: Not-Associated
TX-Power=27dBm
Retry min limit: 7 RTS thr: off Fragment thr: 2352 B
Encryption key: XXXX-XXXX-XX Security mode: open
Power Management: off
Link Quality: 0 Signal Level: 0 Noise Level: 0
RX invalid nwid: 0 RX invaild crypt: 0 RX invalid frag: 0
TX excessive retries: 0 Invalid misc: 0 Missed beacon: 0

(iwlist scan)
Address: XX:XX:XX:XX:XX:XX
ESSID: "Motorola"
Mode: Master
Channel: 1
Frequency: 2.412 (Channel 1)
Quality = 31/100 Signal level: -85dBm Noise level: -96dBm
Encryption key: on

(/etc/network/interfaces)
auto lo 
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.0.12
gateway 192.168.0.1
netmask 255.255.255.0
network 192.168.0.1
broadcast 192.168.0.255

If you need any other information, I'll gladly supply.

---

### Post by gakuma on 2009-02-11
It just dawned on me that you might need this as well:

(lspci)

02:02.0 Ethernet controller: Atheros Communications Inc. Atheros AR 5001X+ Wireless Network Adapter (rev 01)

---

### Post by gakuma on 2009-02-11
I got it attached to the access point, and have it bypassing the firewall in the router settings.

However, I still cannot ping anything besides the computer itself. So it will not ping anything within or external to the network, including the router.

Suggestions? :confused:

---

