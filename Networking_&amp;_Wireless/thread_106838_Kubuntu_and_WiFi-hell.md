---
title: "Kubuntu and WiFi-hell"
date: 2005-12-21
forum: Networking &amp; Wireless
---

### Post by jafro on 2005-12-21
Hello, I've got Kubuntu 5.10 on an Aopen 1557, with an ISL3890-based wlan-card in it. I currently use this with ndiswrapper.

Even though I've configured everyting right, and I get connection as indicated by signal readings and green light in KWifimanager, can't even ping the local network. I've tried wpa, wep and open. Windows connects just fine, same computer.

Here is some info from iwconfig. Looks connected to me (*by me):

IEEE 802.11b/g  ESSID:"E******"
          Mode:Master  Frequency:2.437 GHz  Access Point: 00:90:4B:1E:54:BB
          Bit Rate:54 Mb/s   Tx-Power=31 dBm   Sensitivity=20/200
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Link Quality:147  Signal level:0  Noise level:144
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by gnu2tux on 2005-12-21
i had a problem where i found that wifi0 and eth0 were both being used by the wireless driver, which showed up in iwconfig and ifconfig.

However, i had to do an iwconfig for both wifi0 and eth0 to get the details working, however, the kde config tool worked for me in the end - have you tried that? ( i know it sounds obvious)

anyways try this (firstly with encryption off, eg, open net) and see what happens:

```

iwconfig ethX enc off
iwconfig ethX essid youressid
iwconfig ethX ap auto

```

replace ethX where it is eth whatever and wifi whatever.

then type:

```

dhclient ethX

```

does it get an IP address? If so, great, if not let me know!

Cheers!

---

### Post by jafro on 2005-12-23
Message is posted below

---

### Post by jafro on 2005-12-23
Actually it didn't. Heres the output:

```
root@suushi:/home/jafro # dhclient eth1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:90:4b:1e:54:bb
Sending on   LPF/eth1/00:90:4b:1e:54:bb
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

