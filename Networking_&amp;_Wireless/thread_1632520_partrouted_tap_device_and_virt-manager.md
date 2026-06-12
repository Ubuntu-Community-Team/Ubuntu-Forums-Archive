---
title: "partrouted tap device and virt-manager"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by rldsoftware on 2010-11-28
Hi there. I have the following problem. I have a computer which is ocnnected to the network with a wireless nic. On this computer i have kvm virtual machines. I want to connect those virtual machines to my network via a bridge and not nat.

Now i can't bridge my wireless device via the bridge utils. So i have a workaround which uses parprouted and a tap device.

I do the following:

$ sudo /usr/sbin/tunctl -t tap0 -u `whoami`
$ sudo /sbin/ip link set tap0 up
$ sudo /sbin/ip addr add 192.168.1.100/24 dev tap0
$ sudo /usr/sbin/parprouted wlan0 tap0
$ sudo sysctl net.ipv4.ip_forward=1

and then start my VM with

kvm -hda /dev/sdb -m 512 -net nic,macaddr=DE:AD:BE:EF:90:26 -net tap,ifname=tap0,script=no

And this works perfectly. My wlan device is bridged with the tap device and my vm is connected to my local network.

But now for the problem part. I use virt-manager to manage my domains. And virt-manager has no option to make use of the "-net tap,ifname=tap0,script=no" options i can specify in the command line version of kvm.

If I just add an network card in virt-manager and say it's a bridged card with tap0 (or wlan0) it fails to start with the error "tap0 (or wlan0) is not a bridged device."

How can i make this work with virt-manager? Can i modify my /etc/libvirt/qemu/vm.xml to add the tap device? Does libvirt support options for the tap device? What do i add?

---

### Post by rldsoftware on 2010-12-14
bump

---

### Post by The Foz on 2011-02-11
This post is very useful. Also found the [related post]("http://www.rldsoftware.nl/index.php/Bridging_wireless_for_use_with_KVM") on the RLD Software site.

I have been searching for a solution to get a A KVM VM connected to the Internet via Wireless LAN for quite a while. Can't wait to try this out when I get home (supposed to be working now).

I have no idea about your problem with virt-manager - sorry.

---

### Post by leo_m on 2012-06-21
> If I just add an network card in virt-manager and say it's a bridged  card with tap0 (or wlan0) it fails to start with the error "tap0 (or  wlan0) is not a bridged device."

I know this is way too old and you would have arrived at a few ways of achieving this, but the simplest thing which comes to mind is:  if libvirt is expecting a bridge interface, well create one in your /etc/network/interfaces and make only the tap0 a part of that bridge (bridge-ports tap0); then use that bridge as the bridge device in virt-manager instead of tap0 or wlan0.

---

