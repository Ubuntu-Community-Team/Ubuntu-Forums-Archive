---
title: "Kvm  networking"
date: 2012-10-05
forum: Networking &amp; Wireless
---

### Post by luciany on 2012-10-05
I have a local network with a dhcp router connected to ISP.
In a node I have few KVM virtual machines (working fine with NAT). In order to ssh them from the any node inside my local network I need to make bridge networking.
I followed [https://help.ubuntu.com/community/KVM/Networking](https://help.ubuntu.com/community/KVM/Networking), but no results. Modifying  /etc/network/interfaces I loose the net on node and all VMs.
Any better tutor or help, please.
thanks in advance

solution:

I run:
    sudo ifconfig eth0 0.0.0.0 up
    sudo brctl addbr br0
    sudo brctl addif br0 eth0
    sudo ifconfig br0 up
    sudo dhclient br0 &

if everything goes ok,
    run ifconfig and br0 might have an IP allocated

PS: if the router filters MACs don't forget add the new VM one
PS1:thanks to [http://askubuntu.com/questions/179508/kvm-bridged-network-not-working](http://askubuntu.com/questions/179508/kvm-bridged-network-not-working)

---

