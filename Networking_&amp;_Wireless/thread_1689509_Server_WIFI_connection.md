---
title: "Server WIFI connection"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by Red Dog 99 on 2011-02-16
System Asus P7H57D-v EVO CPU i5-650
SATA 320 GB
4GBb DDR3 ram
AUSU RT-13N WFI interface adapter PCI

Dual boot Server 10.10 64bit and Desk 10.4 32bit

I have to use a KVM switch to work with the Ubuntu machine, so code snippets are very  hard and possible contain mistakes.

Installed  Desk 10.4 first and was amazed that it found all the hardware  correctly. To connect to the Router/Internet all I had to do was supply  the SSID of the router. This is a wireless system only no LAN available.

Now the server wasn't that good. After a great amount of work I finally got wireless-tools installed and functioning. 

```
lspci
```
09:00.00 Network Controller: RaLink RT2860
```
lshw -c network
```
*-Network
        description wireless interface
        product RT2860
        vendor RaLink
        physical id: 0
        bus info pci@0000;09:00.0
        logical name: wlan0
        version 00
        serial: 70:71:bc:3e:6d:77
        width 32 bits
        clock 33mhz
        ---

```
uname -a
```
linux My Home Server 2.6.35-22-server #33 Ubuntu  SMP Sun Sep 19 20:48:58 UTC 2010 x86_64 GNU/Linux

```
lsb_release -a
```
No LSB modules are available
Distributor ID:  Ubuntu
Description:      Ubuntu 10.10
Release            10.10
Codename        Maverick

```
ifconfig
```
lo
  ------
wlan0
  Link encap: Ethernet  HWaddress:70:71:bc:3e:6d:77
  inet address: 192.172.0.196  Bcast 192.172.0.255 Mask 255.255.255.0
  inet6 address: fe80:7271:bcff:fe3e:6d77/64    Scope:link
  UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
  RX packet:9873 0 0 0 0
  TX packet :40653 0 0 0 0
  collisions:0  txqueuelen:1000
  RX bytes: 1779159 (1.7MB)  TX bytes:0
  Interrupt 19

```
iwconfig
```
lo 
  -----

wlan0  Ralink STA ESSID: ""  Nickname "RT2860STA"
          Mode:audio Frequency= 2.412 Ghz Access Point: NOT-ASSOCIATED
          Bit Rate 1Mb/s
          RTS thr: off Fragment thr: off
          Link quality=10/100 Signal level: 0 dBm  Noise level: -87 dBm
          Rx: Invalid nwid:0 Rx Invalid crypt:0 Rx Invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missing beacon:0

```
route -n
```
Kernel IP routing table
Destination    Gateway      Genmask          Flag Metric Ref Use Iface
192.172.0.0   0.0.0.0         255.255.255.0    U     0       0    0    wlan0
0.0.0.0          192.172.0.1  0.0.0.0              UG   100    0    0    wlan0

```
ping -c 3 208.67.219.101
```
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data
From 192.172.0.196 icmp_seq=1 Destination Host Unreachable
From 192.172.0.196 icmp_seq=2 Destination Host Unreachable
From 192.172.0.196 icmp_seq=3 Destination Host Unreachable
---- 208.67.219.101 Ping Statistics ----
3 packages transmitted, 0 received, +3 errors , 100% Packet loss, Time 1999ms
pipe 3

```
ping -c 3 192.172.0.196
```

Return success

NO encryption WEP or WPA (I live in the desert!)

PCI card driver= RT2800PCI ver 2.6.35-22-Server [I don't know where this came from ?]

Tried blacklisting 2x00PCI & 2x00USB drivers NO change.

](*,)
SO  what's the problem? I can't communicate with anything external to the  computer. I have read there might be a driver problem, but since it  works with the Desk version and the problem listed is not what I have , I  don't suspect the driver. The router logs show no attempt at any  connection by this device. 
The difference I notice between the  iconfig logs in the server and desk are their are more UP's in the desk  log.  i.e. (UP, Lower_Up, and state UP)

---

### Post by Red Dog 99 on 2011-02-17
The answer is "any" ?
If you notice the ESSID is "", all attemps to put in the correct SSID "Hillside" failed. Putting the choice "any" in as ESSID caused the configuration to go to "Hillside" the same as I was trying to enter manually.
 Why is "any" a better choice than the real SSID ?

Thanks for trying to solve this.

---

