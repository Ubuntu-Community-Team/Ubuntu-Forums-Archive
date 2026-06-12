---
title: "Ubuntu 10.10 no network at all"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by netz1010 on 2011-06-11
Hello all,
Please if somebody can help...
I installed Ubuntu 10.10 to my old ASUS Z9200 notebook. install was ok, but no network at all... LAN is not working and WLAN is not working. ( I have light on wifi LED)

COMMAND
 lshw -c network

RESULT
*-network:0 DISABLED    
           description: Ethernet interface
           product: 88E8001 Gigabit Ethernet Controller
           vendor: Marvell Technology Group Ltd.
           physical id: 0
           bus info: pci@0000:01:00.0
           logical name: eth0
           version: 13
           serial: ff:ff:ff:ff:ff:ff
           width: 32 bits
           clock: 66MHz
           capabilities: bus_master cap_list rom ethernet physical
           configuration: broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=64 maxlatency=27 mingnt=23 multicast=yes
           resources: irq:20 memory:fa9f8000-fa9fbfff ioport:a800(size=256) memory:fa9c0000-fa9dffff
      *-network:1 UNCLAIMED
           description: Network controller
           product: Ricoh Co Ltd
           vendor: Ricoh Co Ltd
           physical id: 1
           bus info: pci@0000:01:01.0
           version: b3
           width: 64 bits
           clock: 33MHz
           capabilities: bus_master cap_list
           configuration: latency=0 maxlatency=3 mingnt=128
      *-network:2 UNCLAIMED
           description: Network controller
           product: Primex Aerospace Co
           vendor: Primex Aerospace Co
           physical id: 1.4
           bus info: pci@0000:01:01.4
           version: b3
           width: 64 bits
           clock: 33MHz
           capabilities: bus_master cap_list
           configuration: latency=0 maxlatency=3 mingnt=128
           resources: iomemory:4000-3fff
     
   COMMAND
ifconfig


RESULT

    lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:16436  Metric:1
              RX packets:252 errors:0 dropped:0 overruns:0 frame:0
              TX packets:252 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:19728 (19.7 KB)  TX bytes:19728 (19.7 KB)
     
   COMMAND
iwconfig


RESULT

    lo        no wireless extensions.
        eth0      no wireless extensions.
        eth1      no wireless extensions.
    

My WIFI card should be wlan intel 2200

file etc/network/interfaces

auto lo
iface lo inet loopback

Please can anyone help. i've been playing with this for days....tried forums, drivers etc...

Thank you!!!

---

### Post by Neoxhadowespio on 2011-06-11
The top Gnome Panel should have a small, wireless indicator on the top. Click on it and that should give you a list of available networks. Click on the one at your home. If it has some code, a small box will appear asking for it once you do.

---

### Post by netz1010 on 2011-06-11
I know, that is a problem it's got ! next to it and shows 2 times WIRED NETWORK Marvell 88E8001 Eth Controler, but it say DISCONNECTED and you cannot click on it....

---

### Post by Joe of loath on 2011-06-11
Your card should be supported. Are you sure it's seated correctly? It doesn't seem to show up on your lshw dump.

---

### Post by netz1010 on 2011-06-11
It seated ok... (notebook) works under windows.... lan and wlan...:(

---

### Post by netz1010 on 2011-06-11
Just to add some info....

  lspci -knn|grep -i eth -A 4
    01:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller [11ab:4320] (rev 13)
              Subsystem: ASUSTeK Computer Inc. Device [1043:133c]
              Kernel driver in use: skge
              Kernel modules: skge
    01:01.0 Non-VGA unclassified device [0000]: Ricoh Co Ltd Device [1180:0076] (rev ff)


    lspci -knn|grep -i netw -A 4
    01:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev ff)
              Kernel modules: ipw2200
    02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility X700 (PCIE) [1002:5653]
              Subsystem: ASUSTeK Computer Inc. Device [1043:11b2]
    [FONT=&quot]          Kernel driver in use: radeon[/FONT]

---

