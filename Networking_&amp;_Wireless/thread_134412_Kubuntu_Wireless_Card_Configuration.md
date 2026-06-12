---
title: "Kubuntu Wireless Card Configuration?"
date: 2006-02-21
forum: Networking &amp; Wireless
---

### Post by nmatheis on 2006-02-21
Hello

I have a Linksys WPC11 v4 wireless card for my Gateway 1200 Solo laptop.  I d/l-ed the drivers (NET8180.INF) and installed them with ndiswrapper - driver and hardware detected.  Did the modprobe stuff and added ndiswrapper to startup configuration file.

So the problem is I now need to configure and activate the wlan0 connection.  I go into System Settings and click on the Network Settings icon.  I then go into Administrator Mode and disable the eth0 connection (and unplug it).  

Then I select the wlan0 connection and click on "Configure".  Invariably, the KDE Crash Handler comes up with "The application of KD Control Module (kcmshell) crashed and caused the signal 11 (SIGSEGV).  

I just ran an apt-get update and upgrade and installed the 686 kernel to see if that would make any difference, and it didn't - still can't configure the card.  I tried to just "Enable" it, but it immediately toggles back to "Disabled".

I'd really like to get wireless up and running on this laptop and am hoping someone can help me out either by letting me know how to fix this problem or with a work-around.

Thanks!
Nikolaus

---

### Post by Lambert on 2006-02-21
remove the ndiswrapper module

```
 sudo modprobe -r ndiswrapper
```

Then reinsert it

```
sudo modprobe ndiswrapper
```

run this command and post the output of the last 10 or so lines that look associated with ndiswrapper.

[code dmesg[/code]

Also post the output of these commands

```
cat /proc/version
modinfo ndiswrapper
sudo lshw -C network

```

---

### Post by nmatheis on 2006-02-22
Lambert - thanks for the reply!

removed and inserted the ndiwrapper module as specified.

here are the results for the other commands..

```
nikolaus@kubuntu:~$ cat /proc/version
Linux version 2.6.12-10-686 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Feb 13 12:18:37 UTC 2006

```

```
nikolaus@kubuntu:~$ modinfo ndiswrapper
filename:       /lib/modules/2.6.12-10-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
version:        1.1
license:        GPL
vermagic:       2.6.12-10-686 686 gcc-3.4
depends:        usbcore
srcversion:     E21E28A177890611AE46391
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
```

```
nikolaus@kubuntu:~$ sudo lshw -C network
  *-network
       description: Realtek
       physical id: 0
       version: Rtl8139
       slot: Socket 0
       resources: irq:10
  *-network
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 51
       serial: 00:e0:b8:38:05:82
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1                                                              00bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=via-rhine driverve                                                              rsion=1.2.0-2.6 duplex=full ip=192.168.1.100 link=yes multicast=yes port=MII spe                                                              ed=100MB/s
       resources: ioport:e800-e8ff iomemory:f0000000-f00000ff irq:5
  *-network DISABLED
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@02:00.0
       logical name: wlan0
       version: 20
       serial: 00:12:17:47:b5:f0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper link=no multicast=yes wir                                                              eless=IEEE 802.11b
       resources: ioport:4000-40ff iomemory:7000000-70001ff irq:10
```

by the way, what's the lyric in your sig?  looks really familiar but can't quite recall... (edit - just remembered that it's nin)

nikolaus

---

### Post by Lambert on 2006-02-22
Before trying to activate, open a terminal and type in this command. This will output the last lines of the syslog

```
tail -f /var/log/syslog
```

Now try to activate and see if any new output appears in the terminal. If your system crashes then just run this command to get output

```
cat /var/log/syslog
```

Need to see if there is anything in the logs about this.

---

### Post by nmatheis on 2006-02-22
so when i went into network settings, the wlan0 connection wasn't listed.  i rebooted and the wlan0 connection made its way back into the network settings menu.  i deactivated the eth0 connection, went into a terminal and typed in the first line of code you provided, and then tried to configure the wlan0 connection with a kde crash error message as the result.  i then reopened the network settings and tried to enable the wlan0 connection.  it enabled for a second and then toggled to disabled again.

here's the syslog file contents, sorry it's so big.  didn't know how much you'd need...
```

Feb 22 18:24:08 localhost kernel: [4294760.220000] eth0: no IPv6 routers present
Feb 22 18:24:12 localhost hpiod: 0.9.5 accepting connections at 1025... 
Feb 22 18:24:12 localhost hp: unable to open /var/run/hplip/hpssd.port: No such file or directory: prnt/hpijs/hplip_api.c 84 
Feb 22 18:24:12 localhost hp: unable to connect hpssd socket 50002: Connection refused: prnt/hpijs/hplip_api.c 710 
Feb 22 18:24:12 localhost hpiod: invalid message:unable to connect hpssd socket 50002: Connection refused: prnt/hpijs/hplip_api.c 710 msg 
Feb 22 18:24:18 localhost kernel: [4294770.527000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Feb 22 18:24:18 localhost kernel: [4294770.527000] apm: overridden by ACPI.
Feb 22 18:24:19 localhost kernel: [4294770.835000] ip_tables: (C) 2000-2002 Netfilter core team
Feb 22 18:24:19 localhost kernel: [4294770.931000] ip_conntrack version 2.1 (895 buckets, 7160 max) - 248 bytes per conntrack
Feb 22 18:24:21 localhost cardmgr[6734]: watching 1 socket
Feb 22 18:24:22 localhost kernel: [4294773.693000] cs: IO port probe 0x100-0x4ff: clean.
Feb 22 18:24:22 localhost kernel: [4294773.696000] cs: IO port probe 0xc00-0xcf7: clean.
Feb 22 18:24:22 localhost kernel: [4294773.697000] cs: IO port probe 0xa00-0xaff: clean.
Feb 22 18:24:22 localhost cardmgr[6735]: starting, version is 3.2.5
Feb 22 18:24:28 localhost hcid[7208]: Bluetooth HCI daemon
Feb 22 18:24:28 localhost kernel: [4294780.342000] Bluetooth: Core ver 2.7
Feb 22 18:24:28 localhost kernel: [4294780.342000] NET: Registered protocol family 31
Feb 22 18:24:28 localhost kernel: [4294780.342000] Bluetooth: HCI device and connection manager initialized
Feb 22 18:24:28 localhost kernel: [4294780.342000] Bluetooth: HCI socket layer initialized
Feb 22 18:24:28 localhost kernel: [4294780.604000] Bluetooth: L2CAP ver 2.7
Feb 22 18:24:28 localhost kernel: [4294780.604000] Bluetooth: L2CAP socket layer initialized
Feb 22 18:24:28 localhost sdpd[7215]: Bluetooth SDP daemon 
Feb 22 18:24:28 localhost kernel: [4294780.659000] Bluetooth: RFCOMM ver 1.5
Feb 22 18:24:28 localhost kernel: [4294780.659000] Bluetooth: RFCOMM socket layer initialized
Feb 22 18:24:28 localhost kernel: [4294780.659000] Bluetooth: RFCOMM TTY layer initialized
Feb 22 18:24:29 localhost anacron[7274]: Anacron 2.3 started on 2006-02-22
Feb 22 18:24:30 localhost /usr/sbin/cron[7299]: (CRON) INFO (pidfile fd = 3)
Feb 22 18:24:30 localhost /usr/sbin/cron[7300]: (CRON) STARTUP (fork ok)
Feb 22 18:24:30 localhost anacron[7274]: Normal exit (0 jobs run)
Feb 22 18:24:30 localhost /usr/sbin/cron[7300]: (CRON) INFO (Running @reboot jobs)
Feb 22 18:24:31 localhost kernel: [4294782.992000] mtrr: no more MTRRs available
Feb 22 18:24:31 localhost kernel: [4294782.992000] mtrr: no more MTRRs available
Feb 22 18:24:45 localhost dhclient: sit0: unknown hardware address type 776
Feb 22 18:24:46 localhost dhclient: sit0: unknown hardware address type 776
Feb 22 18:24:46 localhost dhclient: Bind socket to interface: No such device
Feb 22 18:24:48 localhost kdm_greet[7377]: Can't open default user face
Feb 22 18:25:10 localhost kdm_greet[7377]: Internal error: memory corruption detected
Feb 22 18:30:15 localhost kernel: [4295126.864000] eth0: link down
Feb 22 18:30:35 localhost dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6013
Feb 22 18:30:35 localhost dhclient: killed old client process, removed PID file
Feb 22 18:30:35 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.2
Feb 22 18:30:35 localhost dhclient: Copyright 2004 Internet Systems Consortium.
Feb 22 18:30:35 localhost dhclient: All rights reserved.
Feb 22 18:30:35 localhost dhclient: For info, please visit http://www.isc.org/products/DHCP
Feb 22 18:30:35 localhost dhclient: 
Feb 22 18:30:35 localhost dhclient: sit0: unknown hardware address type 776
Feb 22 18:30:35 localhost dhclient: sit0: unknown hardware address type 776
Feb 22 18:30:35 localhost dhclient: Listening on LPF/eth0/00:e0:b8:38:05:82
Feb 22 18:30:35 localhost dhclient: Sending on   LPF/eth0/00:e0:b8:38:05:82
Feb 22 18:30:35 localhost dhclient: Sending on   Socket/fallback
Feb 22 18:30:35 localhost dhclient: DHCPRELEASE on eth0 to 192.168.1.1 port 67
Feb 22 18:35:16 localhost dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 0
Feb 22 18:35:16 localhost dhclient: Internet Systems Consortium DHCP Client V3.0.2
Feb 22 18:35:16 localhost dhclient: Copyright 2004 Internet Systems Consortium.
Feb 22 18:35:16 localhost dhclient: All rights reserved.
Feb 22 18:35:16 localhost dhclient: For info, please visit http://www.isc.org/products/DHCP
Feb 22 18:35:16 localhost dhclient: 
Feb 22 18:35:16 localhost dhclient: sit0: unknown hardware address type 776
Feb 22 18:35:17 localhost kernel: [4295429.057000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Feb 22 18:35:17 localhost dhclient: sit0: unknown hardware address type 776
Feb 22 18:35:17 localhost dhclient: Listening on LPF/eth0/00:e0:b8:38:05:82
Feb 22 18:35:17 localhost dhclient: Sending on   LPF/eth0/00:e0:b8:38:05:82
Feb 22 18:35:17 localhost dhclient: Sending on   Socket/fallback
Feb 22 18:35:17 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Feb 22 18:35:18 localhost dhclient: DHCPOFFER from 192.168.1.1
Feb 22 18:35:18 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Feb 22 18:35:18 localhost dhclient: DHCPACK from 192.168.1.1
Feb 22 18:35:18 localhost dhclient: bound to 192.168.1.100 -- renewal in 36221 seconds.
Feb 22 18:35:27 localhost kernel: [4295439.085000] eth0: no IPv6 routers present
Feb 22 18:36:28 localhost gconfd (nikolaus-7839): starting (version 2.12.0), pid 7839 user 'nikolaus'
Feb 22 18:36:28 localhost gconfd (nikolaus-7839): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Feb 22 18:36:28 localhost gconfd (nikolaus-7839): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Feb 22 18:36:28 localhost gconfd (nikolaus-7839): Resolved address "xml:readwrite:/home/nikolaus/.gconf" to a writable configuration source at position 2
Feb 22 18:36:28 localhost gconfd (nikolaus-7839): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Feb 22 18:36:28 localhost gconfd (nikolaus-7839): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Feb 22 18:36:28 localhost gconfd (nikolaus-7839): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Feb 22 18:36:28 localhost gconfd (nikolaus-7839): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Feb 22 18:36:28 localhost gconfd (nikolaus-7839): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Feb 22 19:04:07 localhost -- MARK --
Feb 22 19:17:01 localhost /USR/SBIN/CRON[7899]: (root) CMD (   run-parts --report /etc/cron.hourly)
```

---

