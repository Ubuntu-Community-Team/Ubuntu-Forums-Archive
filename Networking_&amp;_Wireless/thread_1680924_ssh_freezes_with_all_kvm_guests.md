---
title: "ssh freezes with all kvm guests"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by flickerfly on 2011-02-03
I've recently setup a Ubuntu virtual server. On it I have 4 guests which are stored on iscsi shares. Almost any time I use ssh to get into any of them, they freeze up within a couple minutes. I can immediately ssh in again in another terminal tab and then experience the same thing. 'apt-get upgrade' will almost always trigger the problem, but sometimes it will happen when the cursor is just sitting waiting for input. The cursor will continue to blink during the freeze, but not respond to key presses. Eventually, it will report "Write failed: Broken pipe" and dump me back out.

On one guest machine I'm on my 6th ssh session this morning and haven't accomplished anything.

I do not have any physical servers that do this to me. The host machine for these vm guests also does not act in this way.

[INDENT]Any ideas why ssh is freezing and how to get this situation resolved?[/INDENT]

Here is the network config for the virtual network they are on:
```
<network>
  <name>open_access</name>
  <uuid>130507cb-e392-5251-2971-25e755555555</uuid>
  <forward mode='route'/>
  <bridge name='virbr1' stp='on' delay='0' />
  <ip address='192.168.15.1' netmask='255.255.255.0'>
    <dhcp>
      <range start='192.168.15.10' end='192.168.15.20' />
    </dhcp>
  </ip>
</network>
```

Here is the bridge that config works with.
```
virbr1    Link encap:Ethernet  HWaddr fe:54:00:45:bf:2b  
          inet addr:192.168.15.1  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::fd:b6ff:fe7f:b98e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2048 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:302297 (302.2 KB)  TX bytes:857746 (857.7 KB
```

Here is the NIC that connects to the rest of the world.
```
eth0      Link encap:Ethernet  HWaddr 84:2b:2b:69:f5:d0  
          inet addr:192.168.5.50  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::862b:2bff:fe69:f5d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:893760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:705793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:837450931 (837.4 MB)  TX bytes:186608315 (186.6 MB)
          Interrupt:36 Memory:da000000-da012800 
```

Here is the routing table on the vm host.
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.4.0     0.0.0.0         255.255.255.252 U     0      0        0 eth1
192.168.15.0    0.0.0.0         255.255.255.0   U     0      0        0 virbr1
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
192.168.5.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.5.1     0.0.0.0         UG    100    0        0 eth0
```

Here is the routing table on a vm guest. These are on the 192.168.15.0 net. The host knows where 192.168.5.0 traffic should go.
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.15.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.15.1    0.0.0.0         UG    100    0        0 eth0
```

Here is the routing table on the machine I'm running ssh on. It is on the 192.168.5.0 net. The router at 192.168.5.1 knows to point 192.168.15.0 traffic at 192.168.5.50.
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.5.0     0.0.0.0         255.255.255.0   U     0      0        0 br0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 br0
0.0.0.0         192.168.5.1     0.0.0.0         UG    100    0        0 br0
```

---

### Post by rtmie on 2012-05-01
flickerfly,
Did you ever resolve this?

I've encountered this with a new kvm setup and it's driving me nuts

Rob

---

### Post by flickerfly on 2012-05-02
I don't recall how, but this did get resolved. Sorry, I know that isn't much help. Now I'm annoyed at myself for not updating this when I figured it out. 

I seem to recall (I think) that I had to play with the default router's understanding of the network, but this may have been for an entirely different problem.

---

