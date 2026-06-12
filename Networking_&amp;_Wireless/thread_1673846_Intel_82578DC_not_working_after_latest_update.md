---
title: "Intel 82578DC not working after latest update"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by dave945 on 2011-01-23
Solved by rebooting locally attached HUB between this PC and the Verizon router / firewall.

Hello,
After the latest set of updates, my network connection no longer works.
Here's the most recent set of updates, applied yesterday:
Upgraded the following packages:
bsdutils (1:2.17.2-0ubuntu1) to 1:2.17.2-0ubuntu1.10.04.1
fuse-utils (2.8.1-1.1ubuntu2.1) to 2.8.1-1.1ubuntu2.2
libblkid1 (2.17.2-0ubuntu1) to 2.17.2-0ubuntu1.10.04.1
libfuse2 (2.8.1-1.1ubuntu2.1) to 2.8.1-1.1ubuntu2.2
libuuid1 (2.17.2-0ubuntu1) to 2.17.2-0ubuntu1.10.04.1
mount (2.17.2-0ubuntu1) to 2.17.2-0ubuntu1.10.04.1
util-linux (2.17.2-0ubuntu1) to 2.17.2-0ubuntu1.10.04.1
uuid-runtime (2.17.2-0ubuntu1) to 2.17.2-0ubuntu1.10.04.1
xserver-common (2:1.7.6-2ubuntu7.4) to 2:1.7.6-2ubuntu7.5
xserver-xorg-core (2:1.7.6-2ubuntu7.4) to 2:1.7.6-2ubuntu7.5


dbus (1.2.16-2ubuntu4) to 1.2.16-2ubuntu4.1
dbus-x11 (1.2.16-2ubuntu4) to 1.2.16-2ubuntu4.1
libdbus-1-3 (1.2.16-2ubuntu4) to 1.2.16-2ubuntu4.1

Here's what syslog looks like:

Jan 23 00:16:18 bedrock2 NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  dhclient started with pid 1635
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 23 00:16:18 bedrock2 dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan 23 00:16:18 bedrock2 dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jan 23 00:16:18 bedrock2 dhclient: All rights reserved.
Jan 23 00:16:18 bedrock2 dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Jan 23 00:16:18 bedrock2 dhclient: 
Jan 23 00:16:18 bedrock2 NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Jan 23 00:16:18 bedrock2 dhclient: Listening on LPF/eth0/70:71:bc:5c:34:91
Jan 23 00:16:18 bedrock2 dhclient: Sending on   LPF/eth0/70:71:bc:5c:34:91
Jan 23 00:16:18 bedrock2 dhclient: Sending on   Socket/fallback
Jan 23 00:16:22 bedrock2 dhclient: DHCPREQUEST of 192.168.1.11 on eth0 to 255.255.255.255 port 67
Jan 23 00:16:30 bedrock2 dhclient: DHCPREQUEST of 192.168.1.11 on eth0 to 255.255.255.255 port 67
Jan 23 00:16:43 bedrock2 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Jan 23 00:16:51 bedrock2 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Jan 23 00:17:00 bedrock2 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Jan 23 00:17:01 bedrock2 CRON[1652]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 23 00:17:04 bedrock2 NetworkManager: <info>  (eth0): DHCP transaction took too long, stopping it.
Jan 23 00:17:04 bedrock2 NetworkManager: <info>  (eth0): canceled DHCP transaction, dhcp client pid 1635
Jan 23 00:17:04 bedrock2 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Jan 23 00:17:04 bedrock2 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
Jan 23 00:17:04 bedrock2 NetworkManager: <info>  (eth0): device state change: 7 -> 9 (reason 5)
Jan 23 00:17:04 bedrock2 NetworkManager: <info>  Marking connection 'Auto eth0' invalid.
Jan 23 00:17:04 bedrock2 NetworkManager: <info>  Activation (eth0) failed.
Jan 23 00:17:04 bedrock2 NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Jan 23 00:17:04 bedrock2 NetworkManager: <info>  (eth0): device state change: 9 -> 3 (reason 0)
Jan 23 00:17:04 bedrock2 NetworkManager: <info>  (eth0): deactivating device (reason: 0).

Here's lshw -C network:

dtabor@bedrock2:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82578DC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: 70:71:bc:5c:34:91
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=half firmware=0.12-5 latency=0 link=yes multicast=yes port=twisted pair speed=10MB/s
       resources: irq:31 memory:fe400000-fe41ffff memory:fe427000-fe427fff ioport:f020(size=32)

Here's lspci:

lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset PT IDER Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82578DC Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06)

I don't see anything in the latest set of updates that necessarily points to the network, but I was definitely online before, and not after, the reboot that came with the latest set of updates.  I hope I've provided the right amount of relevant info.

Thanks for any suggestions and for all who contribute.

Dave

PS: modprobe -- list shows
kernel/drivers/net/e1000/e1000.ko
kernel/drivers/net/e1000e/e1000e.ko

---

