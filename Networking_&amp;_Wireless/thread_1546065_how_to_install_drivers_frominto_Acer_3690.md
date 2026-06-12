---
title: "how to install drivers from/into Acer 3690"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by lbcopas on 2010-08-04
Could not access wireless Netgear WNR2000, www after installing Ubuntu onto Acer Aspire 3690 - worked fine w/windows, before. Figured I needed drivers so went to Acer and put them on thumb drive. I've now, got them on the desk-top of the Acer but don't think that's where they shoud be. Where should they be and how to do it, please?  explicit steps, please.    .... this is my first time, - be gentle   THANKS. larry

---

### Post by chili555 on 2010-08-04
The Netgear WNR2000 is a router. Is the method you are trying to connect to the router wired ethernet or wireless? Please open Applications > Accessorries > Terminal and do:```
lsusb
sudo lshw -C network
```Post the result and we'll have a better idea how to proceed.

What is the exact name of the file you downloaded?

Gentle is my middle name.

---

### Post by lbcopas on 2010-08-06
Chili, thank you for responding - now, I don't feel I'm drowning. The files (drivers, I think) are: Wireless(802bg)         and      Wireless(802bg)
       Broadcom_4,102.15               Atheros_7.2.0.127
       63_Vistax 86. lnk                    Vistax 86.lnk
I'm trying to connect wireless. It worked fine w/Windows before installing Ubuntu 10.04 LTS.  And my Windows desk top is still doing fine on it.  That's what I'm using, now.
I ran your query and am trying to figure how to copy and paste it for you  -  if fact, I have been for two hours.  It's a good thing I can't find my baseball bat !  Tnx a lot for your help.

---

### Post by lbcopas on 2010-08-06
lbcopas@lbcopas-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
lbcopas@lbcopas-laptop:~$ sudo lshw -c network
[sudo] password for lbcopas: 
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:d0000000-d0003fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: 00:16:d4:df:5d:70
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:21 memory:d0100000-d0101fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7e:77:aa:40
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
lbcopas@lbcopas-laptop:~$ lbcopas@lbcopas-laptop:~$ lsusb
lbcopas@lbcopas-laptop:~$: command not found
lbcopas@lbcopas-laptop:~$ Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
lbcopas@lbcopas-laptop:~$ Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
lbcopas@lbcopas-laptop:~$ Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
lbcopas@lbcopas-laptop:~$ Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
lbcopas@lbcopas-laptop:~$ Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
lbcopas@lbcopas-laptop:~$ lbcopas@lbcopas-laptop:~$ sudo lshw -c network
lbcopas@lbcopas-laptop:~$: command not found
lbcopas@lbcopas-laptop:~$ [sudo] password for lbcopas: 
[sudo]: command not found
lbcopas@lbcopas-laptop:~$   *-network               
*-network: command not found
lbcopas@lbcopas-laptop:~$        description: Network controller
description:: command not found
lbcopas@lbcopas-laptop:~$        product: BCM4311 802.11b/g WLAN
product:: command not found
lbcopas@lbcopas-laptop:~$        vendor: Broadcom Corporation
vendor:: command not found
lbcopas@lbcopas-laptop:~$        physical id: 0
physical: command not found
lbcopas@lbcopas-laptop:~$        bus info: pci@0000:05:00.0
The program 'bus' is currently not installed.  You can install it by typing:
sudo apt-get install atm-tools
lbcopas@lbcopas-laptop:~$        version: 01
version:: command not found
lbcopas@lbcopas-laptop:~$        width: 32 bits
width:: command not found
lbcopas@lbcopas-laptop:~$        clock: 33MHz
No command 'clock:' found, did you mean:
 Command 'clock' from package 'xview-clients' (universe)
clock:: command not found
lbcopas@lbcopas-laptop:~$        capabilities: pm msi pciexpress bus_master cap_list
capabilities:: command not found
lbcopas@lbcopas-laptop:~$        configuration: driver=b43-pci-bridge latency=0
configuration:: command not found
lbcopas@lbcopas-laptop:~$        resources: irq:19 memory:d0000000-d0003fff
resources:: command not found
lbcopas@lbcopas-laptop:~$   *-network
*-network: command not found
lbcopas@lbcopas-laptop:~$        description: Ethernet interface
description:: command not found
lbcopas@lbcopas-laptop:~$        product: BCM4401-B0 100Base-TX
product:: command not found
lbcopas@lbcopas-laptop:~$        vendor: Broadcom Corporation
vendor:: command not found
lbcopas@lbcopas-laptop:~$        physical id: 1
physical: command not found
lbcopas@lbcopas-laptop:~$        bus info: pci@0000:06:01.0
The program 'bus' is currently not installed.  You can install it by typing:
sudo apt-get install atm-tools
lbcopas@lbcopas-laptop:~$        logical name: eth0
logical: command not found
lbcopas@lbcopas-laptop:~$        version: 02
version:: command not found
lbcopas@lbcopas-laptop:~$        serial: 00:16:d4:df:5d:70
serial:: command not found
lbcopas@lbcopas-laptop:~$        size: 10MB/s
No command 'size:' found, did you mean:
 Command 'size' from package 'binutils' (main)
 Command 'size' from package 'binutils-multiarch' (universe)
size:: command not found
lbcopas@lbcopas-laptop:~$        capacity: 100MB/s
capacity:: command not found
lbcopas@lbcopas-laptop:~$        width: 32 bits
width:: command not found
lbcopas@lbcopas-laptop:~$        clock: 33MHz
No command 'clock:' found, did you mean:
 Command 'clock' from package 'xview-clients' (universe)
clock:: command not found
lbcopas@lbcopas-laptop:~$        capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
capabilities:: command not found
lbcopas@lbcopas-laptop:~$        configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
configuration:: command not found
lbcopas@lbcopas-laptop:~$        resources: irq:21 memory:d0100000-d0101fff
resources:: command not found
lbcopas@lbcopas-laptop:~$   *-network DISABLED
*-network: command not found
lbcopas@lbcopas-laptop:~$        description: Wireless interface
description:: command not found
lbcopas@lbcopas-laptop:~$        physical id: 2
physical: command not found
lbcopas@lbcopas-laptop:~$        logical name: wlan0
logical: command not found
lbcopas@lbcopas-laptop:~$        serial: 00:19:7e:77:aa:40
serial:: command not found
lbcopas@lbcopas-laptop:~$        capabilities: ethernet physical wireless
capabilities:: command not found
lbcopas@lbcopas-laptop:~$        configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
configuration:: command not found
lbcopas@lbcopas-laptop:~$ lbcopas@lbcopas-laptop:~$ 
lbcopas@lbcopas-laptop:~$: command not found
lbcopas@lbcopas-laptop:~$ ^C
lbcopas@lbcopas-laptop:~$ 
    Chili,  don't ask me how I did it, but here it is.  I sure hope this gives you a clue as to what I need to do. THANK  YOU

---

