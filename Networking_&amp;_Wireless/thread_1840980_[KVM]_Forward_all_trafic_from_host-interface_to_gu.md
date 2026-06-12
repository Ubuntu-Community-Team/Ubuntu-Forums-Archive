---
title: "[KVM] Forward all trafic from host-interface to guest-vm"
date: 2011-09-08
forum: Networking &amp; Wireless
---

### Post by Skyo on 2011-09-08
Hi forum!


Think of the following situation. My Host machine has 2 interfaces: eth0 & eth1. 
Both connected to the internet with static ips. Now I want to forward _all_ incoming traffic on eth1 to my guest-Vm. I virtualize with qemu-kvm. Host and Guest: Ubuntu 11.04

So far, I tried to create a public bridge with this tutorial:
[http://www.linux-kvm.org/page/Networking#public_bridge](http://www.linux-kvm.org/page/Networking#public_bridge)

Unfortunately, connecting on the eth1-ip, I still was not able to reach the guest.
I conncted to the host. :/)


As far as I understood after doing some research, I have to establish the following chain:

[eth1] -> [software-bridge] -> [tap-interface] -> [guest-vm]

But how? Shall I configure by ifup and ifdown-scripts? Shall I use dhcp or do it manualy?
Do you have some tutorials, which succeeded in doing such networking eventually?

Thank you very much.
Skyo :KS

---

### Post by Skyo on 2011-09-09
Shameless bump. Thanks forum.

---

