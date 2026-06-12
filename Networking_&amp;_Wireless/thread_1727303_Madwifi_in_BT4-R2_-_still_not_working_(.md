---
title: "Madwifi in BT4-R2 - still not working :("
date: 2011-04-12
forum: Networking &amp; Wireless
---

### Post by Vampyer on 2011-04-12
**Ok, first off I know these are the Ubuntu Forums but I had no luck in any of the other forums :(**

So, I'm running BT4-R2 but can't seem to get the madwifi drivers to work at all. Does anyone know how to get them working? 

I have been trying for days now and would really appreciate any help.

---

### Post by josephmills on 2011-04-12
what is your wireless card?

---

### Post by josephmills on 2011-04-12
when you get a chance please copy and paste all ```
iwconfig 
``````
lspci
``` ```
rfkill list
``````
lshw -C network
``` Also I know that this sounds dumb but did you go to wicd and open it yet?(```
network-start
```)

---

### Post by Vampyer on 2011-04-12
iwconfig Output:

```


lo        no wireless extensions.

eth0      no wireless extensions.


```

iwconfig AFTER modprobe ath_pci Output:

```


lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:18739  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wifi1     no wireless extensions.

ath1      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:19 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:50324  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



```

lspci Output:

```


00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 09)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
16:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)


```

lshw -C network Output:

```


*-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:11:22:33:44:55 <<< Modified for obvious reasons
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 duplex=full firmware=0.5-1 ip=192.168.1.19 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:11:22:33:44:55 <<< Modified for obvious reasons
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11b
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:16:00.0
       logical name: wifi1
       version: 01
       serial: 00:11:22:33:44:55 <<< Modified for obvious reasons
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11b


```

I can run Wicd just fine. It picks up my wired network and that's how I'm using it now :)

---

### Post by josephmills on 2011-04-12
how about ```
rfkill
```

---

### Post by Vampyer on 2011-04-12
rfkill didn't return anything, I'll show you what I typed:

```


root@bt:~# rfkill
Usage:  rfkill [options] command
Options:
        --version       show version (0.4)
Commands:
        help
        event
        list [IDENTIFIER]
        block IDENTIFIER
        unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
        <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
root@bt:~# rfkill list
root@bt:~#                


```

---

### Post by josephmills on 2011-04-12
sorry about that ```
rfkill list
```

---

### Post by Vampyer on 2011-04-12
rfkill list returns a blank line :P

---

### Post by josephmills on 2011-04-12
try ```
rfkill unblock all
``` then rfkill list is it there now?

---

### Post by Vampyer on 2011-04-12
Nope, this is what I get:

```


root@bt:~# rfkill unblock all
root@bt:~# rfkill list
root@bt:~#


```

No output at all :(

---

### Post by josephmills on 2011-04-12
what repo's do you have open?

---

### Post by Vampyer on 2011-04-12
How do I check that in BackTrack 4?

---

### Post by josephmills on 2011-04-12
you know that ubuntu offers most of the tools that are on  bt4 in its own repo's  but to check your repo's in bt4 r2. Go to BTlogo-->System-->add/remove package manager, then where it says **show**scroll down go to all available applications do you see your driver do you remember ever putting in a code like apt-add rep or anything like that? Also where did you get the driver? link?

Edit: I don't know if all of the tools or any are in Ubuntu repo's out of the box. but it is possible.

---

### Post by Vampyer on 2011-04-12
I don't see it on the list...

I put this in:

```


svn checkout http://madwifi-project.org/svn/madwifi/trunk madwifi


```

but nothing like apt-add or anything like that

---

### Post by josephmills on 2011-04-12
check out [http://madwifi-project.org/wiki/UserDocs/Distro/Debian/MadWifi](http://madwifi-project.org/wiki/UserDocs/Distro/Debian/MadWifi)

---

