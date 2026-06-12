---
title: "How To Setup Multiple Working Bond Interfaces"
date: 2011-11-30
forum: Networking &amp; Wireless
---

### Post by KiLaHuRtZ on 2011-11-30
I see a lot of people asking how to do this and there is very crude documentation on this subject.  So, I thought I would share my expertise with everyone.

Ubuntu 10.04 and up uses Upstart so the traditional methods for bonding have to be changed to ensure the slaves come up before the bond.

This is not the "Ubuntu" documented method, but I find it is the easiest and best way for things to just work consistently across reboots.

The below is an example of a system with four NIC's wanting two bond groups configured as mode 1 (active-backup) with preempts enabled.

Step 1) Install 'ifenslave'.

```
sudo apt-get install ifenslave
```

Step 2) Setup your bonding options: '/etc/modprobe.d/bonding'.

```
# This file contains the bonding options used by ifenslave.
# See '/etc/network/interfaces' for bonding config parameters.

# Setup module aliases for all your bonds.
alias bond0 bonding
alias bond1 bonding

# Configure bonding options for all your bonds.
# BUG: You can only set one primary interface for one bond.
#      This is a limitation of the ifenslave package. :(
options bonding mode=active-backup miimon=100 max_bonds=2 primary=eth0

# Load the bonding module.
probe bonding
```

Step 3) Setup your bonding parameters: '/etc/network/interfaces'.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto bond0
iface bond0 inet static
address 10.0.0.2
netmask 255.255.255.252
gateway 10.0.0.1 # Only set one gateway!
network 10.0.0.0
broadcast 10.0.0.3
post-up ifenslave bond0 eth0 eth1
pre-down ifenslave -d bond0 eth0 eth1

# The secondary network interface
auto bond1
iface bond1 inet static
address 10.1.1.2
netmask 255.255.255.252
#gateway 10.1.1.1 # Only set one gateway!
network 10.1.1.0
broadcast 10.1.1.3
post-up ifenslave bond1 eth2 eth3
pre-down ifenslave -d bond1 eth2 eth3
```

You can also add VLAN or sub-inetfaces like so.

```
# Example of a VLAN interface. Must have 'bond0' from above!
auto bond0.2
iface bond0.2 inet static
address 10.2.2.2
netmask 255.255.255.252
#gateway 10.2.2.1 # Only set one gateway!
network 10.2.2.0
broadcast 10.2.2.3
```

```
# Example of a sub-interface. Must have 'bond1' from above!
auto bond1:3
iface bond1:3 inet static
address 10.3.3.2
netmask 255.255.255.252
#gateway 10.3.3.1 # Only set one gateway!
network 10.3.3.0
broadcast 10.3.3.3
```

Here is some sample output.

From 'dmesg'...

```
[    2.752636] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.284216] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.827096] e1000: eth2: e1000_probe: Intel(R) PRO/1000 Network Connection
[    4.456883] e1000: eth3: e1000_probe: Intel(R) PRO/1000 Network Connection
[   12.942537] bonding: bond0: enslaving eth0 as a backup interface with a down link.
[   12.945273] e1000: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[   12.982512] bonding: bond0: enslaving eth1 as a backup interface with a down link.
[   12.982573] bonding: bond0: link status definitely up for interface eth0.
[   12.982579] bonding: bond0: making interface eth0 the new active one.
[   12.985344] e1000: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[   12.992424] bonding: bond0: link status definitely up for interface eth1.
[   13.695960] bonding: bond1: enslaving eth2 as a backup interface with a down link.
[   13.698168] e1000: eth2 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[   13.706987] bonding: bond1: enslaving eth3 as a backup interface with a down link.
[   13.709514] e1000: eth3 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
[   13.768840] bonding: bond1: link status definitely up for interface eth2.
[   13.768854] bonding: bond1: making interface eth2 the new active one.
[   13.773541] bonding: bond1: link status definitely up for interface eth3.
```

From 'ifconfig -a'...

```
bond0     Link encap:Ethernet  HWaddr 08:00:27:00:00:00  
          inet addr:10.0.0.2  Bcast:10.0.0.3  Mask:255.255.255.252
          inet6 addr: fe80::a00:27ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:593 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:103534 (103.5 KB)  TX bytes:1836 (1.8 KB)

bond1     Link encap:Ethernet  HWaddr 08:00:27:00:00:02  
          inet addr:10.1.1.2  Bcast:10.1.1.3  Mask:255.255.255.252
          inet6 addr: fe80::a00:27ff:fe00:2/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10512 (10.5 KB)  TX bytes:992 (992.0 B)

eth0      Link encap:Ethernet  HWaddr 08:00:27:00:00:00  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:295 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51677 (51.6 KB)  TX bytes:1836 (1.8 KB)

eth1      Link encap:Ethernet  HWaddr 08:00:27:00:00:00  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:298 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51857 (51.8 KB)  TX bytes:0 (0.0 B)

eth2      Link encap:Ethernet  HWaddr 08:00:27:00:00:02  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5256 (5.2 KB)  TX bytes:992 (992.0 B)

eth3      Link encap:Ethernet  HWaddr 08:00:27:00:00:02  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5256 (5.2 KB)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

And here is some test output from a Nagios script I wrote...

```
Usage: -i [INTERFACE] (-m)
Version: 1.0.1

  -h ........ Help: display this message.

  -i ... Interface: pass a bond interface, defaults to 'bond0'.

  -l ........ List: list available bond interfaces.

  -m ..... Minimal: output in non-verbose mode, defaults to full verbosity,
                    use this option for limited character output, i.e. pagers.

  -v ..... Version: display the script version.
```

Testing with 'bond0'...

```
BOND OK: Interface bond0 is up and running in mode fault-tolerance (active-backup) with interface eth0 as the active slave.  Primary slave interface is eth0.  Slave interfaces are eth0 (status is up; fail count is 0) and eth1 (status is up; fail count is 0).

BOND WARNING: Interface bond0 is up and running in mode fault-tolerance (active-backup) with interface eth1 as the active slave.  Primary slave interface is eth0.  Slave interfaces are eth0 (status is down; fail count is 1) and eth1 (status is up; fail count is 0).

BOND WARNING: Interface bond0 is up and running in mode fault-tolerance (active-backup) with interface eth0 as the active slave.  Primary slave interface is eth0.  Slave interfaces are eth0 (status is up; fail count is 1) and eth1 (status is down; fail count is 1).

BOND OK: Interface bond0 is up and running in mode fault-tolerance (active-backup) with interface eth0 as the active slave.  Primary slave interface is eth0.  Slave interfaces are eth0 (status is up; fail count is 1) and eth1 (status is up; fail count is 1).
```

Testing with 'bond1'...

```
BOND OK: Interface bond1 is up and running in mode fault-tolerance (active-backup) with interface eth2 as the active slave.  Primary slave interface is none.  Slave interfaces are eth2 (status is up; fail count is 0) and eth3 (status is up; fail count is 0).

BOND WARNING: Interface bond1 is up and running in mode fault-tolerance (active-backup) with interface eth3 as the active slave.  Primary slave interface is none.  Slave interfaces are eth2 (status is down; fail count is 1) and eth3 (status is up; fail count is 0).

BOND WARNING: Interface bond1 is up and running in mode fault-tolerance (active-backup) with interface eth2 as the active slave.  Primary slave interface is none.  Slave interfaces are eth2 (status is up; fail count is 1) and eth3 (status is down; fail count is 1).

BOND OK: Interface bond1 is up and running in mode fault-tolerance (active-backup) with interface eth2 as the active slave.  Primary slave interface is none.  Slave interfaces are eth2 (status is up; fail count is 1) and eth3 (status is up; fail count is 1).
```

The script reports a CRITICAL when both slaves are down.

Hope this helps the community! :P

---

### Post by idleup on 2012-04-18
You are a life-saver. I think this post of yours is the only post on the internet about using multiple bonds with newer versions of Ubuntu. I have wasted countless hours trying to get multiple bonds to work. 

One other thing you may want to modify is in the bonding file to use 'alias netdev-bondX bonding' as the other way was depreciated and will give errors in dmesg.

Thanks again.

---

