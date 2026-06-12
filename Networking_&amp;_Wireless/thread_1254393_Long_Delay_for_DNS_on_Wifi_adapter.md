---
title: "Long Delay for DNS on Wifi adapter"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by mscoxoh on 2009-08-31
I just got my Wifi adapter (below) working on Ubuntu 9.04 desktop. I initially had a problem with it asking me to re-authenticate to my WPA network every 1 to 5 minutes, but I switched to wicd instead of network-manager and so far, so good. However, with both, I noticed that when connecting to a new network, there's a long delay before it works and the problem seems to be DNS. After associating, I have an IP address and can connect/ping my local network, but external requests (i.e. ping yahoo.com) result in no ip address - no DNS lookup. After some time, 30 seconds to a minute, I try again and DNS is working and it works fine for all external requests. Any ideas on the long delay before the DNS entry kicks in? BTW, the DNS server on my internal network is my Cisco router which uses OpenDNS for external lookups. Thanks.

Adapter:
```

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
        Subsystem: Intel Corporation Device 1020
        Flags: bus master, fast devsel, latency 0, IRQ 2300
        Memory at efdff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: iwl3945
        Kernel modules: iwl3945
```

iwlist wlan0 scan:
```
wlan0     Scan completed :
          Cell 01 - Address: 00:14:F1:61:2F:70
                    ESSID:"buckI"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=92/100  Signal level:-38 dBm  Noise level=-89 dBm
                    Encryption key:on
                    IE: Unknown: 00056275636B49
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 851E00008D000F00FF031900636F782D6372303100000000000000000300002B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD050040960304
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000026df3d9894e
                    Extra: Last beacon: 56ms ago


```

---

