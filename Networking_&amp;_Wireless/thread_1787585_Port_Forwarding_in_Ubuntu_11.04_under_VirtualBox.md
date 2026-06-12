---
title: "Port Forwarding in Ubuntu 11.04 under VirtualBox"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by hypercalm on 2011-06-21
[If this does not require any configuring in Ubuntu, please ignore the post or it may be deleted by the admins.
I am new to this, but the problem may have to do with my modem, virtualbox, and Ubuntu. Any help would be really appreciated.]

I am running Ubuntu 11.04 using VirtualBox on a Win XP machine. A certain server that I am running inside Ubuntu needs to be accessible
from the outside on port 27080. I've chosen "bridged adapter" option through VirtualBox.

So, the IP's are like:
Windows (Host) IP: 192.168.1.11
Ubuntu (VM) IP: 192.168.1.3

The server running on port 27080 is accessible from the Windows system. The problem lies with forwarding the ports so that outside users can access it.

I use a Beetel 220x ADSL modem. I've tried using port-forwarding (virtual server option in my modem config), where I put my Linux VM's IP as the destination to forward the specific port. I've even tried configuring my modem in DMZ mode putting the Linux VM's IP as the DMZ host IP address. Nothing has worked so far!

I believe that Ubuntu does not run a firewall by default, but is there any specific settings inside my Linux VM that need to be done to make this work?

Thanks!

VirtualBox:

Devices-->Network Adapters

Attached to: Bridged Adapter
Name: Broadcom 440x 10/100 Integrated Controller

Linux:
eerie@V-Machine:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr **********  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe84:de3b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:320762 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150458 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23431384 (23.4 MB)  TX bytes:11969188 (11.9 MB)


Windows:
Windows IP Configuration

        Host Name . . . . . . . . . . . . : Singularity
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Hybrid
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Broadcom 440x 10/100 Integrated Cont
roller
        Physical Address. . . . . . . . . : **********
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.1.11
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 202.56.215.54
                                            202.56.215.55

Ethernet adapter VirtualBox Host-Only Network:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : VirtualBox Host-Only Ethernet Adapter
        Physical Address. . . . . . . . . : *********
        Dhcp Enabled. . . . . . . . . . . : No
        IP Address. . . . . . . . . . . . : 192.168.56.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

---

