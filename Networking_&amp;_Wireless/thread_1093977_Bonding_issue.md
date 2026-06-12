---
title: "Bonding issue"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by SteveO77 on 2009-03-12
Hi,

I'm having really weird issues with a bonded network configuration.

eth0 + eth1 are bonded using ifenslave to bond0

bond0 is then bridged to xenbr71 (this server runs Xen 3.2 and hosts about 8 vm's)

eth0 and eth1 go to different switches which have an uplink between them, giving the most redundant configuration we could think of, with either an interface or a switch failure.

This runs fine for a few hours, but then I start getting weird messages in syslog/dmesg [ 3169.558196] bond0: received packet with  own address as source address  and start getting timeouts on pings and lose connectivity with the host and the vm's

interfaces file: cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#Bonded Fail-Over interface
auto bond0
iface bond0 inet manual  
post-up ifenslave bond0 eth0 eth1 
pre-down ifenslave -d bond0 eth0 eth1

auto eth2
iface eth2 inet manual
  up ifconfig eth2 up

auto xenbr71
  iface xenbr71 inet static
  address 192.168.71.30
  netmask 255.255.255.0
  pre-up ifup bond0
  pre-up brctl addbr xenbr71
  pre-up brctl addif xenbr71 bond0
  post-down brctl delif xenbr71
  post-down brctl delbr xenbr71
  post-down ifdown bond0

auto xenbr74
  iface xenbr74 inet static
  address 192.168.74.30
  netmask 255.255.255.0
  gateway 192.168.74.2
  pre-up ifup eth2
  pre-up brctl addbr xenbr74
  pre-up brctl addif xenbr74 eth2
  post-down brctl delif xenbr74 eth2
  post-down brctl delbr xenbr74
  post-down ifdown eth2


/etc/modules:cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
bonding
options bonding mode=1 miimon=100

loop
options loop max_loop=255



Any help really appreciated, the same setup works in fedora-core-5 (GROAN), I'm currently upgrading all corporate servers to Ubuntu 8.04-LTS but my boss is now giving me a hard time ubuntu can't do what fedora was doing... 

Cheers

---

