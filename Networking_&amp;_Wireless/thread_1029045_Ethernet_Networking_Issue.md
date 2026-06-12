---
title: "Ethernet Networking Issue"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by DarthGrim017 on 2009-01-03
Hello, i am new to Ubuntu and linux in general, and have just finished installing. I am having problems getting my Ethernet Connection working.

here are the results for: sudo lshw -C network

*-network DISABLED
    description: Ethernet interface
    product: 82801DB PRO/100 VE (LOM) Ethernet Controller
    vendor: Intel Corporation
    physical id: 8
    bus info: pci@000:02:08.0
    logical name: eth0
    version: 81
    serial: 00:03:47:f3:da:8f
    size: 100MB/s
    capacity: 100MB/s
    width: 32 bits
    clock: 33MHz
    capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
    configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

*-network DISABLED
    description: Ethernet interface
    physical id:1
    logical name: pan0
    serial: ea:dd:ca:af:d5:5a
    capabilities: ethernet physical
    configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

any help will be greatly appreciated... i have spent hours searching for some clues to the problem.

---

### Post by DarthGrim017 on 2009-01-03
Nevermind, problem solved. Reboot. I have no idea what was causing the problem, any enlightenment there would be great. Somehow rebooting corrected the problem.

---

### Post by superprash2003 on 2009-01-03
please mark thread as SOLVED under thread tools

---

