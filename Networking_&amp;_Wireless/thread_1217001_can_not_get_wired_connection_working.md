---
title: "can not get wired connection working"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by old_dos_guy on 2009-07-18
I just installed ubuntu 9.04 on an old Toshiba Satellite.  The built-in wireless connection worked without any effort, but I have been trying for three days to get the wired ethernet connection up.  I am using a Linksys wrt54g router and DHCP is enabled (the wireless is using it w/o problem).  With the default settings (DHCP automatic) the ubuntu machine will not connect.  If change to Manual in Network Connections and enter appropriate IP addresses, etc., then I can "connect" to the router (I get notification that I am connected) - but I can not access the internet or my home network (again I can do both with wireless).  I am wondering if I have the wrong driver or if I have the NIC configured incorrectly or if it is damaged.  This is the relavent section from lshw

*-network
                description: Ethernet interface
                product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 42
                serial: 00:08:0d:3a:0e:01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6

---

