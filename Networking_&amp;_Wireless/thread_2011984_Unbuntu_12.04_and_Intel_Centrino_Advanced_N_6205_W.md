---
title: "Unbuntu 12.04 and Intel Centrino Advanced N 6205 Wireless adapter not detected"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by bhaskar27in on 2012-06-28
Hi,

I have a HP ProBook 6460b and I have installed Ubuntu 12.04 on my Virtual Machine as a guest OS. The host is Windows 7.

I have Intel Centrino N 6205 Wireless card. This device is not recognized by Ubuntu.

dmesg | grep iwl rfkill list all[FONT=monospace]
Shows nothing.

[/FONT]iwconfig
[FONT=monospace]Shows

[/FONT][FONT=monospace]lo        no wireless extensions.

eth0      no wireless extensions.[/FONT] 
[FONT=monospace]Also
[/FONT]route -n
[FONT=monospace]
shows

[/FONT]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.195.2   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.195.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0
[FONT=monospace]
[/FONT]ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0c:29:65:40:9a  
          inet addr:192.168.195.129  Bcast:192.168.195.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe65:409a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9558 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7289 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9460220 (9.4 MB)  TX bytes:861159 (861.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69212 (69.2 KB)  TX bytes:69212 (69.2 KB)


[FONT=monospace]
lshw -C network

Shows:

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82545EM Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0c:29:65:40:9a
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom ethernet physical logical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A ip=192.168.195.129 latency=0 mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:19 memory:d8920000-d893ffff memory:d8900000-d890ffff ioport:2000(size=64) memory:dc400000-dc40ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

I am not sure what is it that I am missing. Please help.

Thanks,
-Bhaskar
[/FONT]

---

### Post by wildmanne39 on 2012-06-28
Hi, this is an internal card correct? if so a guest in a virtual environment will not see it nor be able to use it the guest will run off of the internet of the host.
Thanks

---

