---
title: "Ubuntu Server 13.04 - static IP on a VM?"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by leejayd on 2013-05-04
Hi,

I've trying to assign a hostname and static IP to Ubuntu Server running in a VM.

After installing I edited the etc/network/interfaces :


# The loopback network interfaceauto loiface lo inet loopback
# The primary network interface

auto eth0iface eth0 inet static

address  192.168.242.0 (from VMWARE)
netmask 255.255.255.0 (from VMWARE)
network 192.168.0.0 (I guessed this as I can't find)
broadcast 192.168.242.255 (this was found in VM DHCP settings)
gateway 192.168.242.2 (from VMWARE)
dns-nameservers 8.8.8.8 8.8.4.4

I restarted the network with :/etc/init.d/networking restart

I then edited the etc/hosts file :

127.0.0.1       localhost.localdomain   localhost
192.168.242.0   server1.example.com      server1

Then ran :

echo server1.example.com > /etc/hostname
/etc/init.d/hostname restart

I can ping the server from the host with IP 192.168.242.0

However, from the VM I can't ping the host nor can I get online or ping a public site.I tried turning off the firewall in the host but this no no effect. Any ideas ?

---

### Post by TheFu on 2013-05-04
You can't use a 192.168.242.0 IP address on that subnet.  From teh other information posted, it appears that any unused IP from  192.168.242.4-  192.168.242.254 would be fine.

Also, you didn't describe the sort of networking selected on the VM host for this client. If bridged, then you should be fine.  For NAT, you may or may not be ok.

Change the IP in the interfaces file, restart networking and see if that doesn't fix it.

---

