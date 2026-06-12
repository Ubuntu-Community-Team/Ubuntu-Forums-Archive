---
title: "No AP with p54pci after upgrade to natty"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by phects on 2011-05-17
Hey,

i upgraded from 10.10 to 11.04 (server) on my alix router with p54pci (isl3886pci)  wireless NIC a few days ago. I used it as a WPA2 encrypted access point with hostapd. Despite the fact, that there are no signs of obvious defects on the router, no device here "sees" the net spanned by my AP. A reinstallation of linux-firmware-nonfree did not change the situation. "*iwlist wlan0 scan"* shows surrounding APs. An association to an open AP does not work either.

```
# lspci
00:0c.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
``````
# dmesg | grep p54
[   19.598498] p54pci 0000:00:0c.0: setting latency timer to 64
[   19.660139] ieee80211 phy0: p54 detected a LM86 firmware
[   19.660164] p54: rx_mtu reduced from 3240 to 2376
[   20.762134] Registered led device: p54-phy0::assoc
[   20.762616] Registered led device: p54-phy0::tx
[   20.763088] Registered led device: p54-phy0::rx
[   20.763575] Registered led device: p54-phy0::radio
[   20.763609] p54pci 0000:00:0c.0: is registered as 'phy0'
``````
# hostapd -d /etc/hostapd/hostapd.conf
Configuration file: /etc/hostapd/hostapd.conf
Opening raw packet socket for ifindex 0
BSS count 1, BSSID mask ff:ff:ff:ff:ff:ff (0 bits)
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
nl80211: Added 802.11b mode based on 802.11g information
RATE[0] rate=10 flags=0x2
RATE[1] rate=20 flags=0x6
RATE[2] rate=55 flags=0x6
RATE[3] rate=110 flags=0x6
RATE[4] rate=60 flags=0x0
RATE[5] rate=90 flags=0x0
RATE[6] rate=120 flags=0x0
RATE[7] rate=180 flags=0x0
RATE[8] rate=240 flags=0x0
RATE[9] rate=360 flags=0x0
RATE[10] rate=480 flags=0x0
RATE[11] rate=540 flags=0x0
Passive scanning not supported
Mode: IEEE 802.11g  Channel: 9  Frequency: 2452 MHz
Flushing old station entries
Deauthenticate all stations
Using interface wlan0 with hwaddr 00:61:f3:11:47:f1 and ssid 'Foo'
SSID - hexdump_ascii(len=4): [..]
PSK (ASCII passphrase) - hexdump_ascii(len=13): [..]
PSK (from passphrase) - hexdump(len=32): [..]
WPA: group state machine entering state GTK_INIT (VLAN-ID 0)
GMK - hexdump(len=32): [REMOVED]
GTK - hexdump(len=32): [REMOVED]
WPA: group state machine entering state SETKEYSDONE (VLAN-ID 0)
wlan0: Setup of interface done.
``````
# iwconfig
wlan0     IEEE 802.11bg  Mode:Master  Frequency:2.452 GHz  Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

mon.wlan0  IEEE 802.11bg  Mode:Monitor  Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```I would be pleased, if someone here could help me debugging this.

Thanks!
henning

---

