---
title: "VPN weirdness with [X]ubuntu in VirtualBox and NAT"
date: 2012-06-06
forum: Networking &amp; Wireless
---

### Post by jabalsad on 2012-06-06
Hi all

I'm seeing some extremely strange behaviour, can anyone tell me what may be causing this?

I am running two VM's: Ubuntu 10.04 and Xubuntu 12.04. The host operating system is Windows 7 and is connected to a VPN. Both VM's are using NAT so all traffic should be routed through the VPN.

I shouldn't be able to see my local network at all, but I'm getting this weird mix of VPN and non-VPN traffic. For example, the DNS requests are correctly going through to the DNS server on the VPN, but the response to the DNS query gives me a host, say 10.0.2.2 (which happens to be a host on my home network) and requests then get sent to the machine on the home network.

When pinging 10.0.2.2 on the host machine, it correctly sends traffic to the target host on the VPN. So I'm guessing the VirtualBox NAT is bypassing the VPN somehow? (But this doesn't make sense)

I'm not sure this matters, but the VPN software is Cisco AnyConnect.

I'll appreciate any feedback

---

