---
title: "Wifi unbearably slow after Ubuntu 11.04 install"
date: 2012-01-15
forum: Networking &amp; Wireless
---

### Post by 09061920 on 2012-01-15
Just switched from Windows 7, where I had around 30 Mbps to Ubuntu 11.04, 0.86 Mbps according to speedtest.net. 

I'm not sure what the problem is, tried looking at other threads but they don't help...

Here is result of iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"xxxxx"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:FE:49:6F:2C   
          Bit Rate=243 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:32  Invalid misc:32397   Missed beacon:0

```

lspci:

```

01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)


```

I noticed that ipv6 was disabled so I set it to automatic, but this didn't really help...any ideas? :(

---

