---
title: "eth0 gone after 8.10 to 9.04 upgrade"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by silentwol on 2009-05-16
Hi, I've just upgraded to 9.04 (kubuntu). I'm having a few problems, the biggest being lack of internet connection.

"ls /dev | grep eth" shows no results.  I'm using my onboard ethernet port, mobo: gigabyte 965p-ds3.

Any ideas?

I will reboot and post my dmesg in a minute.

Thanks! :)

---

### Post by chili555 on 2009-05-16
> ls /dev | grep ethThat's the wrong place to look. How about showing us:```
sudo lshw -[SIZE="4"]C[/SIZE] network
```

---

### Post by silentwol on 2009-05-16
Sorry, here you go:
```
  *-network DISABLED
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 22
       serial: 00:16:e6:8e:9c:13
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair

```

DISABLED :O

Thanks for your help :)

EDIT: btw, sudo ifdown and ifup didn't help. Came up with an error along the lines of "no network connection" interspersed with the usual info.  Apologies for being vague, rebooting into windows again and again to connect to the internet is getting tiring!

---

### Post by silentwol on 2009-05-16
Sorry, here you go:
```
  *-network DISABLED
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 22
       serial: 00:16:e6:8e:9c:13
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair

```

DISABLED :O

Thanks for your help :)

EDIT: btw, sudo ifdown and ifup didn't help. Came up with an error along the lines of "no network connection" interspersed with the usual info.  Apologies for being vague, rebooting into windows again and again to connect to the internet is getting tiring!

EDIT2:
OK, here's ifup:
```
ifup eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

execve (/sbin/dhclient-script, ...): Permission denied
Listening on LPF/eth0/00:16:e6:8e:9c:13
Sending on   LPF/eth0/00:16:e6:8e:9c:13
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
```

Obviously running as root. Problem seems to be in "execve (/sbin/dhclient-script, ...): Permission denied"... time for a google.

---

### Post by silentwol on 2009-05-16
Silly me!

Turns out I'd selected 'No' when asked if I'd like to overwrite the grub menu.lst config, which meant I was running the old kernel, which screwed up apparmor, which was stopping access to the dhcp script.

All sorted now :)

---

