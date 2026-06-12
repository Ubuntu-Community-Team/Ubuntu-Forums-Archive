---
title: "[Server 10.10] Help needed with: DHCP server, IP masquerading"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by Jimboland on 2011-05-01
Hello guys,

I'm trying to set up an Ubuntu server installation that i would like to  use as a DHCP server so it can assign IP addresses to all the 'client'  computers that i connect to it. (so it can function as a router) I  understand that i have to do something with 'IP Masquerading'. And i  found a guide that explains me what to do, but (i'm not a network  expert) i don't understand everything.

[https://help.ubuntu.com/10.04/serverguide/C/firewall.html](https://help.ubuntu.com/10.04/serverguide/C/firewall.html)

So far i found out that:

-Its not easy to do this
-DHCP server does not make the server a 'router'
-I have to adjust the NAT Tables in the 'conf' files.

The server is connecting via my router (which also functions as a DHCP server) but the on a different network. 
DHCP range of my router is 192.168.0.x
DHCP range of my Ubuntu server is 128.0.0.x

What i did so far is:

Assigned a static IP to my server

**Interfaces.conf**
[I]
# The loopback network interface
auto lo
iface lo inet loopback
  
# The primary network interface
auto eth2
iface eth2 inet static
address 192.168.0.192
netmask 255.255.255.0
gateway 192.168.0.1[/I]

Assigned a static DNS.

And wrote the DHCP's subnet declaration.
Which looks like this.

**dhcpd.conf**
[I]
# This is a very basic subnet declaration.
  
subnet 128.0.0.0 netmask 255.255.255.0 {
  range 128.0.0.100 128.0.0.200;
  option broadcast-address 128.0.0.255;
  default-lease-time 6000;
  max-lease-time 72000;     
}[/I]

And i wrote on which interfaces the DHCP server should listen for requests.
Its should listen for requests on eth2 and 'serve' on eth0 and eth1
Because 'eth2' is where i connect the internet, and 'eth0' and 'eth1' is where the other computers should connect to.

**dhcp3-server**

[I]# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts
  
#
# This is a POSIX shell fragment
#
  
# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#    Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth2"[/I]

But now i'm stuck. I can't get the server to assign ip addresses to  client computers. So none of the computers that i connect to the server  have internet connection.

Can somebody please help me?

Jimmy

---

