---
title: "Asus/ Atheros AR8131 : unable to initiate wired network (wireless is OK)"
date: 2012-10-25
forum: Networking &amp; Wireless
---

### Post by MarceloH on 2012-10-25
Hi everyone

I have  a problem since I installed 12.04 (over 10.04, hence not a fresh install). My wireless does work, yet my ethernet doesnt.

ifconfig gives
> lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:331 errors:0 dropped:0 overruns:0 frame:0
          TX packets:331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45661 (45.6 KB)  TX bytes:45661 (45.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:64:42:e9:80  
          inet addr:132.207.220.155  Bcast:132.207.223.255  Mask:255.255.252.0
          inet6 addr: fe80::21e:64ff:fe42:e980/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1476  Metric:1
          RX packets:5832 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2109100 (2.1 MB)  TX bytes:161005 (161.0 KB)"lshw -C network" gives:
>   *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:64:42:e9:80
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi  driverversion=3.2.0-32-generic-pae firmware=39.31.5.1 build 35138  ip=132.207.220.155 latency=0 link=yes multicast=yes wireless=IEEE  802.11bgn
       resources: irq:47 memory:feafe000-feafffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:febc0000-febfffff ioport:ec00(size=12:cool:And, "nm-tool" gives:
> NetworkManager Tool

State: connected (global)

- Device: wlan0  [Poly-Public] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:1E:64:42:E9:80

  Capabilities:
    Speed:           36 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    eduroam:         Infra, 00:12:7F:99:83:99, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2 Enterprise
    Poly-Securise:   Infra, 00:12:7F:99:83:91, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2 Enterprise
    eduroam:         Infra, 3C:CE:73:08:F6:E9, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2 Enterprise
    Poly-Securise:   Infra, 3C:CE:73:08:F6:E1, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2 Enterprise
    Poly-Public:     Infra, 3C:CE:73:08:F6:E3, Freq 2412 MHz, Rate 54 Mb/s, Strength 54
    *Poly-Public:    Infra, 00:12:7F:99:83:93, Freq 2437 MHz, Rate 54 Mb/s, Strength 53

  IPv4 Settings:
    Address:         132.207.220.155
    Prefix:          22 (255.255.252.0)
    Gateway:         132.207.220.1

    DNS:             132.207.144.2
    DNS:             132.207.144.3and finally, "lspci -nn | grep 0200"

> 04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8131 Gigabit Ethernet [1969:1063] (rev c0)I struggle with this problem for hours  :sad:

Any help would be greatly appreciated.
Sincerely,

Marcelo

---

### Post by MarceloH on 2012-10-25
I found the problem !!

I forget that point, but a few weeks ago, I blacklisted eth0 because of the slow booting that it used to create. See [http://askubuntu.com/questions/149514/disable-ethernet-permanently-to-speed-up-boot-time](http://askubuntu.com/questions/149514/disable-ethernet-permanently-to-speed-up-boot-time)

I seldom use ethernet (only when I move to a specific office abroad) so I did not realized that.

Now I reversed the protocol described in the link above, and got it back, youhou ! :)

---

