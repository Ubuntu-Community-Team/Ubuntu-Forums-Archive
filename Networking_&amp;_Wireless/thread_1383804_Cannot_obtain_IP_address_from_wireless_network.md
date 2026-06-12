---
title: "Cannot obtain IP address from wireless network"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by bj_rn on 2010-01-17
Hello,

I'm using Ubuntu 9.10 and for a while I had no problems connecting to the internet through the wireless network. But recently, my wireless connection started disconnecting regularly. Following an advice I found online, I installed linux-backports-modules-karmic, but after a reboot the wireless device stopped working altogether - it had lost its driver. Since then I managed to associate the device with Broadcom's STA driver, which I had been using before. But now, the wireless device cannot connect to the internet anymore. The network manager's output to /var/log/syslog indicates that the device cannot obtain an IP address. When I run
```

sudo dhclient eth1

```
I get an error, saying "No DHCPOFFERS received".
I have browsed through many threads but couldn't find any solutions. 

Maybe some of the information below helps resolving this problem:
```

1) Machine Brand and Model
Dell Latitude D830

2) Wireless Brand, Model and Chipset
$ lspci | grep 'BCM4328'
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

3) Check Interface
$ ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:19:7e:a2:64:e1  
          inet6 addr: fe80::219:7eff:fea2:64e1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:1008
          TX packets:14 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:596 (596.0 B)  TX bytes:4028 (4.0 KB)
          Interrupt:17 Base address:0xc000 
$ iwconfig eth1
eth1      IEEE 802.11abgn  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:14 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received

4) Check for modules:
$ lsmod | grep wl
wl                   1272936  0 
lib80211                6432  1 wl

5) Kernel boot messages
$ dmesg
[   25.487957] lib80211_crypt_tkip: disagrees about version of symbol lib80211_unregister_crypto_ops
[   25.487959] lib80211_crypt_tkip: Unknown symbol lib80211_unregister_crypto_ops
[   25.488226] lib80211_crypt_tkip: disagrees about version of symbol lib80211_register_crypto_ops
[   25.488228] lib80211_crypt_tkip: Unknown symbol lib80211_register_crypto_ops
[   25.488650] eth1: Broadcom BCM4328 802.11 Wireless Controller 5.10.91.9

6) Network config
$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 03
       serial: 00:19:7e:a2:64:e1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f9ffc000-f9ffffff memory:f0000000-f00fffff(prefetchable)

7) Scan for networks
eth1      Scan completed :
          Cell 01 - Address: 00:24:FE:41:42:B3
                    ESSID:"FRITZ!Box WLAN 3270"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:5/5  Signal level:-43 dBm  Noise level:-91 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD5B0050F204104A0001101044000102103B000100104700100F00000B00000A0032700024FE524C8F1021000341564D1023000341564D10240000104200001054000800000000000000001011000341564D100800020188103C000103
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

8) Ubuntu Version
$ lsb_release -d
Description:    Ubuntu 9.10

9) Kernel/architecture
$ uname -mr
2.6.31-17-generic i686

10) Restarting the network
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
11) Output from /var/log/syslog when trying to connect to wireless network
Jan 17 19:55:56 blund-laptop dhclient: Listening on LPF/eth1/00:19:7e:a2:64:e1
Jan 17 19:55:56 blund-laptop dhclient: Sending on   LPF/eth1/00:19:7e:a2:64:e1
Jan 17 19:55:59 blund-laptop dhclient: DHCPREQUEST of 192.168.178.25 on eth1 to 255.255.255.255 port 67
Jan 17 19:56:06 blund-laptop dhclient: DHCPREQUEST of 192.168.178.25 on eth1 to 255.255.255.255 port 67
Jan 17 19:56:16 blund-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Jan 17 19:56:22 blund-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Jan 17 19:56:31 blund-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
Jan 17 19:56:40 blund-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Jan 17 19:56:42 blund-laptop NetworkManager: <info>  (eth1): DHCP transaction took too long, stopping it.

```
Any help would be greatly appreciated!

Thanks

---

### Post by ratcheer on 2010-01-17
Has your DHCP server used up all of its available IP's to be assigned? Mine will sometimes assign them all from 1 to max and, even though many of the leases have expired and not all of the IP's are currently being used, it still won't reassign the old ones, again. Maybe just resetting the DHCP server would allow the IP's to be served.

Tim

---

### Post by bj_rn on 2010-01-18
Tim,

Thanks for your post!

I checked the router: It has assigned only 5 IP addresses in total - there should be plenty more. Actually, I noticed that my wireless device is recognized by the router and was even assigned an IP address, but for some reason I cannot receive it.

Another idea? Any help would be most welcome..

Bjoern

---

### Post by ratcheer on 2010-01-18
I don't know how to force the DHCP address to be received, but since the assigned IP is now known, you could hard-code it in your Network Settings and use it until you can find out how to resolve the DHCP receive problem.

Tim

---

### Post by bj_rn on 2010-01-18
Tim,

I was going to follow your advice, but when looking for the necessary information on my router - a Fritz!Box WLAN -, I stumbled upon a thread where it was suggested to change the WPA mode within the router's configuration menu from WPA+WPA2 to WPA2 (CCMP). I was sure that the encryption played no role in my wireless issue because I had tried earlier without encryption with the same error message saying that no IP address could be obtained. But it turns out that changing the WPA mode solved my problem - I'm posting this using my wireless connection.

Thanks again for your help!

Bjoern

---

