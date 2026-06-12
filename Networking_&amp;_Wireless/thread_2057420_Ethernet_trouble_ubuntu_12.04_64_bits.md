---
title: "Ethernet trouble ubuntu 12.04 64 bits"
date: 2012-09-13
forum: Networking &amp; Wireless
---

### Post by Ferguson35 on 2012-09-13
Hi everybody,

I have a trouble with ethernet since 3 days. Let me explain.

I have 2 Hard drives, one with win7 64 bits and the other with Ubuntu 12.04 64bits.
I made a partition for Xubuntu on the HD of Win7 for testing. I deleted it then i had a grub rescue. To solve it i reinstalled an ubuntu 12.04 on this partition to get a grub working. So now i have 2 ubuntu 12.04 64 bits and win7.


Before those manipulations, wireless and ethernet connections were working on both ubuntu and Win7.

Now, I have wireless and ethernet working on windows 7 and only wireless working on ubuntu.

I'm stuck because i need ethernet connection on ubuntu because I am in a student accomodation.

I don't understand why ethernet doesn't work anymore on ubuntu. When i click in the Network manager on the ethernet connection to reload it, it works for 5 sec (It loads the page then take an infinite time if i want to change website. When changing website if i reload the connection, it will work for 5 seconds again load the page and stop).

Here is my ifconfig :
```

ifconfig
eth1      Link encap:Ethernet  HWaddr 00:90:f5:cd:48:6a             adr inet6: fe80::290:f5ff:fecd:486a/64 Scope:Lien           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1           Packets reçus:60254 erreurs:0 :1008 overruns:0 frame:0           TX packets:2386 errors:0 dropped:92 overruns:0 carrier:0           collisions:0 lg file transmission:1000            Octets reçus:7858538 (7.8 MB) Octets transmis:317210 (317.2 KB)           Interruption:46 Adresse de base:0x2000   lo        Link encap:Boucle locale             inet adr:127.0.0.1  Masque:255.0.0.0           adr inet6: ::1/128 Scope:Hôte           UP LOOPBACK RUNNING  MTU:16436  Metric:1           Packets reçus:1275 erreurs:0 :0 overruns:0 frame:0           TX packets:1275 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 lg file transmission:0            Octets reçus:170645 (170.6 KB) Octets transmis:170645 (170.6 KB)  wlan1     Link encap:Ethernet  HWaddr 68:5d:43:09:86:5c             inet adr:192.168.1.102  Bcast:192.168.1.255  Masque:255.255.255.0           adr inet6: fe80::6a5d:43ff:fe09:865c/64 Scope:Lien           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1           Packets reçus:6155 erreurs:0 :0 overruns:0 frame:0           TX packets:4358 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 lg file transmission:1000            Octets reçus:5039416 (5.0 MB) Octets transmis:735093 (735.0 KB)

```Here is my
```
sudo lshw -C network
```it returns 
```
  *-network                       description: Interface réseau sans fil        produit: Centrino Wireless-N 2230        fabriquant: Intel Corporation        identifiant matériel: 0        information bus: pci@0000:03:00.0        nom logique: wlan1        version: c4        numéro de série: 68:5d:43:09:86:5c        bits: 64 bits        horloge: 33MHz        fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless        configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-30-generic firmware=18.168.6.1 ip=192.168.1.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn        ressources: irq:49 mémoire:f7900000-f7901fff   *-network        description: Ethernet interface        produit: RTL8111/8168B PCI Express Gigabit Ethernet controller        fabriquant: Realtek Semiconductor Co., Ltd.        identifiant matériel: 0.2        information bus: pci@0000:04:00.2        nom logique: eth1        version: 0a        numéro de série: 00:90:f5:cd:48:6a        taille: 100Mbit/s        capacité: 1Gbit/s        bits: 64 bits        horloge: 33MHz        fonctionnalités: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A latency=0 link=yes multicast=yes port=MII speed=100Mbit/s        ressources: irq:46 portE/S:d000(taille=256) mémoire:f2104000-f2104fff mémoire:f2100000-f2103fff
```and the file 

```
cat  /etc/network/interfaces
```gives me 
```
auto lo iface lo inet loopback
```I tried many things like changing the cable. It doesn't work.

I tried to connect wth liveUSB ubuntu, ethernet does work.

So now i have no idea on how to resolve this trouble.

If you could help me, that would be very kind of you.
Thanks in advance.

---

### Post by SushiAddiction on 2012-09-13
Sorry no answer but this sounds like what is happening to me. About 2 weeks ago eth worked perfectly. Then one day it stopped working sometimes when I boot.

When I plug in a usb wifi modem eth starts working.... and the strangest thing is, it's not using the usb wifi for the connection, it uses eth.

Why would plugging in a usb wifi modem make eth work :/

Since I've done nothing, I'm assuming an update broke eth. Probably something to do with Realtek. I've got a SMC2-1211TX that has never died.

Update>  I found that my eth0 was pointing to 0.0.0.0. [right click network> Connection Information]
Fixed by deleting network connection (I hope) and creating a new one.
Update> ethernet reset again 0.0.0.0 Might be because of suspend.

---

