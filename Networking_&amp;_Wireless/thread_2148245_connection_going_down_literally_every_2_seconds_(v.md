---
title: "connection going down literally every 2 seconds (vista doesn't)"
date: 2013-05-24
forum: Networking &amp; Wireless
---

### Post by vistajustcrashedagain on 2013-05-24
believe it or not, but vista is working better than Ubuntu at the moment. i installed Ubuntu 12.4 LTS along side vista on an hp laptop and it did great, until i updated it. now it connects and disconnects every 2 seconds even when i plug it into the Ethernet cable. and before you think it's the computer, when i went on vista the internet worked! so can anybody tell me whats going on and how to fix it?

---

### Post by Bucky Ball on 2013-05-24
Welcome to the forums. We have a better chance of helping you if you can tell us what release are you using. Also, open a terminal and put in these two commands one at a time:

```
iwconfig
sudo lshw -C network

```
Please post the result here. Thanks.

---

### Post by vistajustcrashedagain on 2013-05-24
i tried what you said, but it did not work. is there any other way or am i doing something wrong? please reply. Plus the Ubuntu i use is 12.4 LTS

results in  [COLOR=#000000]terminal:[/COLOR]

cmt@cmt-HP-Pavilion-dv6700-Notebook-PC-mick:~$ iwconfig
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.


eth0      no wireless extensions.


cmt@cmt-HP-Pavilion-dv6700-Notebook-PC-mick:~$ sudo lshw -C network
[sudo] password for cmt: 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: NVIDIA Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:59:43:a1
       capacity: 100Mbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:42 memory:f6488000-f6488fff ioport:30f8(size=8) memory:f6489c00-f6489cff memory:f6489800-f648980f
  *-network
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:e1:09:b0:62
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.5.0-30-generic firmware=N/A ip=192.168.1.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f6000000-f600ffff
cmt@cmt-HP-Pavilion-dv6700-Notebook-PC-mick:~$

---

### Post by praseodym on 2013-05-24
Deactivate the hardware encryption of the wireless driver:

```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k

```
For the LAN driver add two module parameters:
```

echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
sudo modprobe -rfv forcedeth
sudo modprobe -v forcedeth
```

---

