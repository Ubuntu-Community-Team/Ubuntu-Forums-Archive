---
title: "my wireless doesn't connect in ubuntu 12.04"
date: 2012-09-08
forum: Networking &amp; Wireless
---

### Post by raedkandah on 2012-09-08
Hi all ...

i have dell laptop inspiron n5110 and installed linux mint 13 after that my wireless stop connecting to my network it can scan and the network appear so i remove linux mint and install ubuntu 12.04 and the problem not solved ...

here some command i try to figure out ...

[ cat /etc/modprobe.d/* | grep ath ]
output:
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci



[ ifconfig ]
output:

eth0      Link encap:Ethernet  HWaddr 18:03:73:8b:e7:58  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1a03:73ff:fe8b:e758/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5343194 (5.3 MB)  TX bytes:688266 (688.2 KB)
          Interrupt:52 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1149 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:112425 (112.4 KB)  TX bytes:112425 (112.4 KB)

wlan0     Link encap:Ethernet  HWaddr 38:59:f9:87:ae:bf  
          inet6 addr: fe80::3a59:f9ff:fe87:aebf/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:241 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27233 (27.2 KB)  TX bytes:37355 (37.3 KB)


[ dmesg | grep ath ]
output:

[   27.676780] ath9k 0000:09:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   27.676795] ath9k 0000:09:00.0: setting latency timer to 64
[   27.728121] ath: EEPROM regdomain: 0x60
[   27.728123] ath: EEPROM indicates we should expect a direct regpair map
[   27.728127] ath: Country alpha2 being used: 00
[   27.728128] ath: Regpair used: 0x60
[   27.771734] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   27.773066] Registered led device: ath9k-phy0
[   28.218802] usbcore: registered new interface driver ath3k




[ rfkill list ]
output:

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

[ lshw ] 

*-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: wlan0
                version: 01
                serial: 38:59:f9:87:ae:bf
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=3.2.0-30-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:19 memory:f7a00000-f7a0ffff

please any help i'll be appreciated 

thx

---

