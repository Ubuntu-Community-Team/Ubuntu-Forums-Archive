---
title: "my ip alias doesn't behave as before after Jaunty upgrade"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by robertbub on 2009-05-17
After upgrading to jaunty, I discovered that my ip aliasing (eth0 and eth0:0, going from the same interface) no longer behaves as it did under intrepid.

I have 2 interfaces: eth0 and eth0:0.  I want eth0 to be very restrictive (I do this via Firestarter, which operates via iptables), and I want eth0:0 to be completely open.  Eth0 is auto configured via DHCP and eth0:0 is configured:> auto eth0:0
iface eth0:0 inet static
    address 192.168.2.51
    netmask 255.255.255.0
    gateway 192.168.2.1
In intrepid, a telnet, for example, would bind the source address interface to my DHCP address -- the more restrictive interface.  Now, telnet binds the source address as 192.168.2.51 -- the unrestricted interface.

Here's my route output:> $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth0This is what I would expect.  However, "ip route" output is not what I want:> $ ip route list
192.168.2.0/24 dev eth0  proto kernel  scope link  src 192.168.2.51 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.2.1 dev eth0  src 192.168.2.51  metric 100 
default via 192.168.2.1 dev eth0  metric 100

I tried creating a script in /etc/dhcp3/dhclient-enter-hooks.d :> if [ "x$reason" = xBOUND ]; then
	/sbin/ip route replace 192.168.2.0/24 dev eth0 proto kernel scope link src 192.168.2.101
fibut it never seems to get done.

Anyone else having this problem?  Is there a simple workaround?

---

### Post by robertbub on 2009-05-17
I gave up and decided to reverse the roles: the 192.168.2.51 will be the restrictive ruleset and my DHCP will be the unrestricted firewall.

The only downside is that my **tinyproxy** will have my DHCP ip address hard-coded in the config file (for "Bind" for the source address).  Just hope my router doesn't reassign my associated ip address :-(.

---

