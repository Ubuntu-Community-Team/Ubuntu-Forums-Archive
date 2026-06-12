---
title: "Running KVM in Ubuntu Server 12.04 on machine with multiple NICs"
date: 2013-01-14
forum: Networking &amp; Wireless
---

### Post by crankyoldbugger on 2013-01-14
Hi All,

I'm still fairly new to Ubuntu so I wanted to ask a question here about setting up VMs in Ubuntu Server 12.04.

I have a machine with 3 NIC cards (eth0, 1 & 2).  I've installed Ubuntu Server 12.04.

I want to set up virtual machines on this box using KVM.  How do I set up the NICs for this?  I've assigned static IPs in /etc/network/interfaces but these were designed for non-VM work.  I'm really not sure how to set up the NICs for VMs.  I've found plenty of tips online for one-NIC machines, but how to set up three NICs?

I know if this was Windows Hyper-V (which I'm trying to get away from!), I would have one NIC for management, then the other two to be shared by any future VMs that I create.

Thanks!

---

