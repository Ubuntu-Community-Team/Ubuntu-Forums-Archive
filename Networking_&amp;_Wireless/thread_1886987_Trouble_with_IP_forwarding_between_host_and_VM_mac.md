---
title: "Trouble with IP forwarding between host and VM machines"
date: 2011-11-26
forum: Networking &amp; Wireless
---

### Post by TeeRev on 2011-11-26
I've been trying to figure this out by searching, but most results I am finding are much more complicated than what I need so I figured I'd make a post.

I have 2 Ubuntu 10.04 servers inside VMware workstation, and a host Windows 7 64bit machine.  The host machine is connected through VMNet 1 on the 192.168.65.0 network and is 192.168.65.1

Ubuntu VM1 has 2 NICs with the first NIC on the 192.168.65.0 network addressed 192.168.65.2, and the second NIC is on the 10.20.0.0 network addressed 10.20.0.1

Ubuntu VM2 is on the 10.20.0.0 network as 10.20.0.2.


I have enabled IP forwarding on VM1 by uncommenting the line "net.ipv4.ip_forward = 1", and doing cat /proc/sys/net/ipv4/ip_forward returns 1 which should mean that is working as far as I can tell.

I can ping from the Win7 machine to 192.168.65.1, and to 10.20.0.1, and I can ping from VM2 to 192.168.65.2 and 10.20.0.1, but the Win7 and VM2 machines can not ping each other.  

I have tried adding various routes on the host and VM2 machines, using different interfaces as gateways, but nothing lets connectivity through.  I have also cleared the firewall.

Not sure what I am missing here...  Any help please?

Thanks

---

