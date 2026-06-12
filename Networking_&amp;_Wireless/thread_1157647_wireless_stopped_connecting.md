---
title: "wireless stopped connecting"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by applesauce51 on 2009-05-12
I have kubuntu 9.04 and my wireless internet wouldn't connect today. It had been working fine the past few days, and it works with vista. I have a dell studio 15, and there is a switch on the side that enables/disables wifi, it is highlighted when enabled. It is not highlighted when im on kubuntu. In wireless settings, I have connect automatically enabled and KDE wallet is rembering my wep key. Thanks for any help.

---

### Post by Peter09 on 2009-05-13
Can you post the output of

```
ifconfig
```

and

```
route
```

---

### Post by djurny on 2009-05-13
output of /var/log/syslog can also help in debugging here..

---

### Post by applesauce51 on 2009-05-13
> **Peter09 said:**
> Can you post the output of

```
ifconfig
```and

```
route
```

I do not know how to do this. I'm still pretty new to linux, do you go though the command prompt? I try to get to the command prompt by pressing alt+ctrl+f2 and it asks for my name and password. I think I know both my name and pass word, but at the password, nothing show up and when I press enter, it goes to an empty line. 

As for the syslog, I saved a text file in vista, then was able to open in linux, I copied and pastes some network management info and saved it, but when I opened it in vista, there was no change.

---

### Post by Peter09 on 2009-05-13
The simplest way is to do

Applications->Accessories->Terminal

then either cut and paste the command if its complicated or just type it.

---

### Post by applesauce51 on 2009-05-15
ifconfig:
   

  eth0      Link encap:Ethernet  HWaddr 00:21:70:6f:c2:dd
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:17
   
  lo        Link encap:Local Loopback
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:54 errors:0 dropped:0 overruns:0 frame:0
            TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:3388 (3.3 KB)  TX bytes:3388 (3.3 KB)
   
   
  route:
  Kernel IP routing table
  Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


   output of /var/log/syslog:
  May 13 08:06:48 t-laptop NetworkManager: <info>  (eth0): bringing up device. 
  May 13 08:06:48 t-laptop nm-system-settings: Added default wired connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_21_70_6f_c2_dd
  May 13 08:06:48 t-laptop kernel: [   20.888621] tg3 0000:09:00.0: irq 2297 for MSI/MSI-X
  May 13 08:06:48 t-laptop kernel: [   21.036211] ADDRCONF(NETDEV_UP): eth0: link is not ready
  May 13 08:06:48 t-laptop NetworkManager: <info>  (eth0): preparing device. 
  May 13 08:06:48 t-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
  May 13 08:06:49 t-laptop console-kit-daemon[2476]: WARNING: Couldn't read /proc/2475/environ: Failed to open file '/proc/2475/environ': No such file or directory 
  May 13 08:07:00 t-laptop NetworkManager: <WARN>  list_connections_cb(): Couldn't retrieve connections: No such method 'ListConnections' in interface 'org.freedesktop.NetworkManagerSettings' at object path '/org/freedesktop/NetworkManagerSettings' (signature '').  Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.79 BogoMIPS (lpj=7979592)

---

### Post by applesauce51 on 2009-05-17
bump

---

### Post by Peter09 on 2009-05-17
Let us see if the system is even seeing that there is a device there

```
lshw -C network
```

---

### Post by applesauce51 on 2009-05-18
taylor@t-laptop:~$ lshw -c network
  WARNING: you should run this program as super-user.
    *-network UNCLAIMED
         description: Network controller
         product: BCM4312 802.11b/g
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:0c:00.0
         version: 01
         width: 64 bits
         clock: 33MHz
         capabilities: bus_master cap_list
         configuration: latency=0
    *-network
         description: Ethernet interface
         product: NetLink BCM5784M Gigabit Ethernet PCIe
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:09:00.0
         logical name: eth0
         version: 10
         serial: 00:21:70:6f:c2:dd
         width: 64 bits
         clock: 33MHz
         capabilities: bus_master cap_list ethernet physical
         configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 module=tg3 multicast=yes
    *-network DISABLED
         description: Ethernet interface
         physical id: 1
         logical name: pan0
         serial: 9a:f1:ac:cd:73:ae
         capabilities: ethernet physical
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by mkrahmeh on 2009-05-18
not sure but it seems your OS cannot find the wireless card, to check further, please post the output of
```
lspci | grep -i wireless
```

---

### Post by applesauce51 on 2009-05-18
taylor@t-laptop:~$ lspci grep -i wireless
  Usage: lspci [<switches>]
   
  Basic display modes:
  -mm             Produce machine-readable output (single -m for an obsolete format)
  -t              Show bus tree
   
  Display options:
  -v              Be verbose (-vv for very verbose)
  -k              Show kernel drivers handling each device
  -x              Show hex-dump of the standard part of the config space
  -xxx            Show hex-dump of the whole config space (dangerous; root only)
  -xxxx           Show hex-dump of the 4096-byte extended config space (root only)
  -b              Bus-centric view (addresses and IRQ's as seen by the bus)
  -D              Always show domain numbers
   
  Resolving of device ID's to names:
  -n              Show numeric ID's
  -nn             Show both textual and numeric ID's (names & numbers)
  -q              Query the PCI ID database for unknown ID's via DNS
  -qq             As above, but re-query locally cached entries
  -Q              Query the PCI ID database for all ID's via DNS
   
  Selection of devices:
  -s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]   Show only devices in selected slots
  -d [<vendor>]:[<device>]                        Show only devices with specified ID's
   
  Other options:
  -i <file>       Use specified ID database instead of wireless
  -p <file>       Look up kernel modules in a given file instead of default modules.pcimap
  -M              Enable `bus mapping' mode (dangerous; root only)
   
  PCI access options:
  -A <method>     Use the specified PCI access method (see `-A help' for a list)
  -O <par>=<val>  Set PCI access parameter (see `-O help' for a list)
  -G              Enable PCI access debugging
  -H <mode>       Use direct hardware access (<mode> = 1 or 2)
  [FONT=&quot]-F <file>       Read PCI configuration dump from a given file[/FONT]

---

### Post by Peter09 on 2009-05-18
Try installing Linux-Restricted Modules.

-You may need to enable backports in synaptic-

Look at this
[https://bugs.launchpad.net/ubuntu/jaunty/+source/linux-restricted-modules/+bug/292450](https://bugs.launchpad.net/ubuntu/jaunty/+source/linux-restricted-modules/+bug/292450)

---

