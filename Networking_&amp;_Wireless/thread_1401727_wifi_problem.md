---
title: "wifi problem"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by cucuru on 2010-02-08
hi! I have just installed ubuntu in my laptop, I installed the wifi target, it works, but it doesn't find my own wifi signal! I'm at home, and it find other signals, but not mine.

In the laptop I have also windows, so, I restarted it with windows, and it found all of them, the signals found by ubuntu and mine, and it's now connected without any problem.

My router make is comtrend, can be any problem with it?

My wifi target is  BCM4312 I installed it with:

```


sudo aptitude install bcmwl-kernel-source

```


Thanks!!!!

Regards

---

### Post by crucialhoax on 2010-02-08
Lets see if the device itself can find it in Ubuntu with a quick command from the terminal.
where <insert your wireless card name here> = eth1 eth0 wlan0

```
ifconfig -a
```

```
sudo iwlist <your wireless card from above command> scan
```

---

### Post by cucuru on 2010-02-08
Hello, I'm not sure I understood you, but I'm posting all the information I have (about the wireless working):

```

user@user-laptop: ~$ sudo lshw

          *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth1
                version: 01
                serial: 00:22:5f:7e:73:97
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:17 memory:f6cfc000-f6cfffff


```

```

user@user-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1E:4C:73:BF:84
                    ESSID:"Livebox-EFF8"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:2/5  Signal level:-71 dBm  Noise level:-67 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 64:68:0C:0C:5A:45
                    ESSID:"WLAN_5A42"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:1/5  Signal level:-83 dBm  Noise level:-87 dBm
                    IE: Unknown: DD760050F204104A00011010440001021041000100103B00010310470010000102030405060708090A0B0C0D0EBB1021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D4150100800020088
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:03:54:01:DE:64
                    ESSID:"Zao"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-79 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:18:F8:F1:9B:4D
                    ESSID:"NANY"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-83 dBm  Noise level:-92 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s


```

My wireless network ID is WLAN_CA, as you can see it isnt in the list.

Now, what you said, (if I understood it well):

```

user@user-laptop:~$ sudo iwlist BCM4312 scan
BCM4312   Interface doesn't support scanning.


```

Thanks!!! Regards

---

### Post by crucialhoax on 2010-02-08
it should be ```
sudo iwlist eth1 scan
```

---

