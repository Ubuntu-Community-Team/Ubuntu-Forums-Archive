---
title: "Unable to ping anything besides localhost on Ubuntu Server 10.04"
date: 2011-09-11
forum: Networking &amp; Wireless
---

### Post by BBBThunda on 2011-09-11
Ok I've bee searching forums all day with no luck.  I'm in a real mess, although one that might possibly have an easy fix.

On my network I have a bunch of machines running either Windows or some version of Ubuntu.  All of these machines can connect to my router via wireless.

I also have a machine running Ubuntu Server 10.04.2.  This machine does not have a wireless card and is connected directly by ethernet cable to the router.

All of the above machines have been configured in the router as having static IP addresses.

Recently, on the Ubuntu Server, after a combination of trying to get KVM to work and also installing 2 additional ethernet cards (which have since been removed)  I lost the ability to ping external IP addresses.  DNS seemed to be still working (hostnames would resolve when pinging, but ping would fail), and I could ping internal machines with no problems.

After a bunch of troubleshoting, I also lost the ability to ping the gateway or any internal machines.  Not to mention I also stupidly removed dhcp-client (although dhclient wasn't helping before)

Despite DNS no longer working, resolv.conf looks fine.  Routing tables had default routes pointing to the correct gateway for both eth0 and br0 (not sure whether br0 should be involved or not)

As of the latest update, I'm no longer getting an ipv4 address despite having set a static one up in /etc/network/interfaces

I tried blacklisting ipv6 in /etc/modprobe.d/blacklist but still getting ipv6 addresses only.

My interfaces are br0, eth0, lo and virbr0.  I'm pretty sure br0 ad virbr0 showed up after I installed KVM.  eth0 is my ethernet.

I would just reinstall the whole system, but I'm hesitant to do so since I had backed up so much stuff onto this machine before this happened.

Currently I'm in the process of trying to set up an offline repository so I can attempt to get dhclient back, but in the meantime, what else can I do to troubleshoot this? 

Is there a recommended config I can try?  Or a script/wizard that could automatically configure it?

Would it be helpful to disable kvm or remove br0/virbr0?  (if so, how?)

Are there any logs I can provide?  (copy/paste won't be helpful but maybe I can output to a file and get it onto a usb drive or something)

---

### Post by BBBThunda on 2011-09-12
UPDATE:

I managed to get dhclient back, but despite getting:

```
bound to #########.18 renewal in 37260 seconds.
```

I still can't ping the gateway #########.1 or any external ip's

I can still ping localhost.

And here's the output of all my config (with 1st 3 octets of IP's masked, not sure if I needed to do that, but oh well.  :)

```

route:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
#########.0     *               255.255.255.0   U     0      0        0 eth0
#########.0     *               255.255.255.0   U     0      0        0 br0
default         #########.1     0.0.0.0         UG    0      0        0 br0
default         #########.1     0.0.0.0         UG    0      0        0 eth0



resolv.conf:
nameserver #########.1
domain home
search home



interfaces:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address #########.18
	netmask 255.255.255.0
	network #########.0
	broadcast #########.255
	gateway #########.1

# Bridged interface for virtual guests
auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off




ifconfig:
br0       Link encap:Ethernet  HWaddr 6c:62:6d:ba:35:b6  
          inet addr#########:.18  Bcast:#########.255  Mask:255.255.255.0
          inet6 addr: fe80::6e62:6dff:feba:35b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:439181 (439.1 KB)  TX bytes:4866 (4.8 KB)

eth0      Link encap:Ethernet  HWaddr 6c:62:6d:ba:35:b6  
          inet addr:#########.18  Bcast:#########.255  Mask:255.255.255.0
          inet6 addr: fe80::6e62:6dff:feba:35b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2759 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:480539 (480.5 KB)  TX bytes:17481 (17.4 KB)
          Interrupt:25 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4732 (4.7 KB)  TX bytes:4732 (4.7 KB)

virbr0    Link encap:Ethernet  HWaddr c6:be:fe:04:7e:fa  
          inet6 addr: fe80::c4be:feff:fe04:7efa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:18718 (18.7 KB)

```


Any ideas???

---

### Post by BBBThunda on 2011-09-12
Also, don't have it on me at the moment, but I'm pretty sure my iptables setup is default/standard.

Any linux network gurus out there that can figure out if I've mistyped something or forgot about a config?

---

### Post by BBBThunda on 2011-09-17
UPDATE:

So I realized that when I tried to do an nslookup on the server's IP #########.18, I got a timeout.  So everything to this point seemed to point to a DNS issue.

So I decided to first go back to dynamic dhcp.

I changed /etc/network/interfaces to define eth0 as dhcp.

I also went into the router's dhcp console and found the lease for .18 and killed it.  I  also removed the static lease definition for my server's mac address.

After this I could ping local addresses again, but still no external addresses.  The funny thing is since then, I've added the static lease definition and it works the same.  Maybe something got corrupted in the dhcp server on the router?

Anyway, signs point to maybe a routing issue now?

route -n gives me the same 2 routes for both eth0 and br0.

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
#########.0      0.0.0.0         255.255.255.0   U     0      0        0 br0
#########.0      0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         #########.1      0.0.0.0         UG    0      0        0 eth0
0.0.0.0         #########.1      0.0.0.0         UG    0      0        0 br0

```

Any ideas what I might be missing?

---

### Post by BBBThunda on 2011-09-17
UPDATE:

Ok, so I was about to start messing with the routes and I decided I should try doing a network restart first before doing so.  I just did a ```
/etc/init.d/networking restart
``` and now I can ping everything!!!

The strange thing now is the routing table now looks like this:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
#########.0     0.0.0.0         255.255.255.0   U     0      0        0 br0
0.0.0.0         #########.1     0.0.0.0         UG    100    0        0 br0

```
I figured there would have to be routes for eth0 if my ethernet card was to work, but I guess that's not the case.

If anyone can explain why, that would be fantastic.

I'm going to make sure rebooting doesn't somehow break it again before marking this thread as solved.

---

### Post by drdos2006 on 2011-09-17
Hi there. 
There is no need to hide your internal LAN addresses.
My home server  "/etc/network/interfaces"  file looks like this because I do not have wireless.
auto lo
iface lo inet loopback
iface eth0 inet static
	address 192.168.0.111
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1

I have found that IPv6 causes me a few problems so this is what I have added to the bottom of my "/etc/sysctl.conf" file. 

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

After rebooting your server, from your server terminal, type

"cat /proc/sys/net/ipv6/conf/*/disable_ipv6"

They should all be 1.

Hope that helps.

regards

---

### Post by BBBThunda on 2011-09-17
Restarting the server breaks it.  But restarting networking again fixes it again.

The routing tables are the same when broken/working as they were earlier in the thread except the following additional route exists now:

```
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
```

Restarting networking removes the eth0 interface's routes and then ping works.  To be extra sure, I also confirmed that doing a route del on the eth0 routes after startup also allows ping to work again.

So now my (hopefully) final questions are:

**Where during the network initialization (on startup) do routes get automatically added?**

**If there isn't one set place, how can I track it down? (logfiles, etc?)**

**And is there a config or script I can modify to get the correct routes to be added on startup, rather than having to manually delete the bad routes afterward?**

---

### Post by drdos2006 on 2011-09-18
I regret I can not assist you any further. Far too deep for me to know about. Hopefully someone will be able to make sense. Does KVM have a forum for you ask ??

regards

---

### Post by BBBThunda on 2011-09-20
I GOT IT!  (I think)  Turns out it was indeed an easy fix, although maybe a sneaky one.

Changing eth0 to use dhcp again was ALMOST the answer... but that left me with two bridged interfaces (eth0 and br0) both set to use dhcp.

I updated the interfaces file, changing br0 to static, rebooted, and BOOM!  Internet on startup!

/etc/network/interfaces:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
#iface eth0 inet static
	#address #########.18
	#netmask 255.255.255.0
	#network #########.0
	#broadcast #########.255
	#gateway #########.1

# Bridged interface for virtual guests
auto br0
iface br0 inet static
#iface br0 inet dhcp
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off

```

The routing tables now look like this after boot:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
#########.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
0.0.0.0         #########.1     0.0.0.0         UG    0      0        0 eth0
```

And I can now SSH to the server from another machine without having to log in from the console and restart networking first.:popcorn:

So my conclusion, which may or may not be correct (any network gurus that can confirm?), is that **it's either bad practice to have an ethernet and its bridged interface both configured for dhcp, or it's bad practice to have any bridged interface (br0, br1, etc.) configured to use dhcp.**

I hope this helps some other unfortunate victims of broken network interfaces due to automatic config changes from installing and removing of multiple ethernet cards.

---

