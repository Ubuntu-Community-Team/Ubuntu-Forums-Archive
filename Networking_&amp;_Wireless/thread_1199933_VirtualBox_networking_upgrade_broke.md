---
title: "VirtualBox networking upgrade broke"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by swells5 on 2009-06-29
I am using virtualbox (2.2.4) downloaded from Vbox site.
My host is Jaunty.
I have a virtual ubuntu lamp server with 3 web sites, all of which have been working and accessable from the internet and my LAN for about one year.
Recently, jaunty was updated.
Then next time I started Vbox- I had to upgrade the vboxdrv module which I did.
Now my Ubuntu server will not connect to the internet, and the internet cannot connect to my server!
I also have XPpro in a virtual machine and it still works fine, no problem connecting. It is connected by Vbox default PCnet-FastIII(NAT). And this is also the way my ubuntu LAMP server was/is connected .
I think something happened during the upgrade but I can't figure it out. I have tried multiple combinations of Vbox network cards and settings with no luck.
Dlink router address 192.168.0.1
Virtual server static ip set to 192.168.0.128

ifconfig (guest)
eth0    correct MAC address
ip 192.168.0.128 as expected
mask 255.255.255.0
Bcast 192.168.0.255
etc.

Anyone else have this trouble?
Anyone have any suggestions?

Thanks
Steve W.

---

### Post by jhannah on 2009-06-30
It looks like the interface you have setup in VirtualBox is setup to NAT traffic. As such, you should be able to change it to use DHCP and VirtualBox will had out a different RFC1918 local IP address and handle NATing traffic out from your VM to the rest of the network. That being said, since you are running a server, you probably want to switch over to use the Host Interface option which will allow you to bridge the VM NIC with one of your host interfaces and at that point, you can statically assign IP information and reach it from the rest of the network. Just edit the VM's network properties, select host interface for the type and pick the NIC you want to bridge it with and that should be it.

---

### Post by swells5 on 2009-07-01
thanks I'll try that today.
steve

---

### Post by swells5 on 2009-07-03
i tried above and for awhile i could reach my server from the internet and my lan...but not the other way around...could not get to internet from my server?
so I followed a few more tutorials and am now totally broken again.
So this am, I uninstalled vbox 2.2.4 and installed from the repos vbox 3.0.
i read the manual and it said that bridge-network only required in virtual machine setup to - choose the bridge adapter and the network card of the host.
this did not work for me.
I tried nat still no luck.
host interfaces.
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
(router set to reserve 192.168.0.x for this mac)
guest ( ubuntu server ) interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 192.168.0.x
netmask 255.255.255.0
gateway 192.168.0.1

network restart = error no such device, failed to bring up eth1.
also tried nat - no internet access from guest
also tried guest interfaces set to dhcp - no such device.

lost - need guidance
thanks again in advance.
steve

---

### Post by superprash2003 on 2009-07-03
post output of** route -n** from the terminal

---

