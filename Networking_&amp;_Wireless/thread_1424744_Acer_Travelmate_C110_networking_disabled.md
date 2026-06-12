---
title: "Acer Travelmate C110 networking disabled"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by wickyd on 2010-03-08
Dear members

I have just finished installing 9.04 via USB onto an Acer Travelmate C110. 

For the record, 9.10 refused to even boot on this laptop. I used universal-usb-installer and unetbootin, both without success.

The installation completed successfully, except that wireless networking is not enabled. 

Can someone please point me to the correct resource whereby I can get the wireless nic working.

Thank you.

Kind regards,
wickyd

---

### Post by wickyd on 2010-03-08
sudo lshw -class network -sanitize:

  *-network:0             
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth1
       version: 04
       serial: [REMOVED]
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 link=no maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: [REMOVED]
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by alenis on 2010-03-08
Hello 
I have a C100. When I want to use the wireless I enable it as default network adapter in the Bios. I don't think it can be activated once the system is running.

---

### Post by wickyd on 2010-03-08
Dear alenis

Thank you for your reply! Your recommendation worked perfectly. Wireless networking is now working.

Kind regards,
wickyd

---

