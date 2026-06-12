---
title: "With net down, IP's dropped from NIC's, why?"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by whit on 2009-06-12
I've been running Linux on multiple systems since '94, and this one is new to me. Today I had a problem that in the course of resolving I rebooted my router for my ISP and the hub between it and three Ubuntu boxes. On 2 of the 3 boxes, the NIC which was on that hub dropped its IP assignments (a single assignment on one box, multiple assignments on the other). 

This is behavior I've never seen. Normally when an IP is assigned, it stays assigned regardless of the state of the connection outward from it. Doing "ifdown" and "ifup" restored these two NIC's - once I realized what had happened. But the interfaces were not down - ifdown was required before ifup - they just had lost their IP assignments.

If this can happen, that makes recovery from network outages tricky, since it will require having some process that monitors status and brings the interfaces down and up after IP's are dropped like this. What the heck could have triggered this behavior? Is it a known new "feature"? Is there a way to simply block it from happening again?

---

### Post by cariboo on 2009-06-12
If your router is running a dhcp server, and the router reboots, you are going to lose the assigned ip addresses, but the connected computers should pick up a new ip address once the router has finished booting.

---

### Post by whit on 2009-06-15
These are not addresses assigned by DHCP. These are fixed addresses assigned through /etc/network/interfaces settings. I just experienced it again. Unplugging three boxes to replace a hub with a switch, two of the three dropped their IPs from the interface plugged in there, only one kept its assignment. All are running flavors of Ubuntu. The ones that dropped their IPs required the "ifdown ethX; ifup ethX" sequence to restore them.

This is a serious concern. I have other Ubuntu servers on a switch, with failover set up. It turns out I need to power cycle that switch to clear its arp table. If cycling that switch is going to drop the fixed IPs of the Ubuntu boxes, now I have to monitor for that and put together a script to fix the situation.

This seems like work that shouldn't be required - a bug. But I'm not at all sure what package to file the bug against.

---

### Post by whit on 2009-06-16
> **whit said:**
> But I'm not at all sure what package to file the bug against.
Since this is happening on only 2 of 3 systems, could this be related to the kernel modules that handle the NICs? Would that be the right thing to file the bug against?

Or is there some higher level service that could be attempting to "clean up" by dropping the IPs assigned when connectivity's lost?

---

### Post by redmk2 on 2009-06-16
> **whit said:**
> Since this is happening on only 2 of 3 systems, could this be related to the kernel modules that handle the NICs? Would that be the right thing to file the bug against?

Or is there some higher level service that could be attempting to "clean up" by dropping the IPs assigned when connectivity's lost?

I would check your syslog files.  What errors related to the NIC do you see?

---

### Post by whit on 2009-06-16
> **redmk2 said:**
> I would check your syslog files.  What errors related to the NIC do you see?
Thanks. That was exactly what to do:

> Jun 16 14:02:36 green NetworkManager: <info>  (eth1): carrier now OFF (device state 3)
Jun 16 14:02:36 green NetworkManager: <info>  (eth1): device state change: 3 -> 2 
Jun 16 14:02:36 green NetworkManager: <info>  (eth1): deactivating device (reason: 0).
Jun 16 14:02:36 green NetworkManager: <WARN>  check_one_route(): (eth1) error -34 returned from rtnl_route_del(): Sucess

So the problem is that NetworkManager is a dangerous utility that should never be left enabled on a production server? Because if it was any good, it would bring the interface back up when it sees a good connection again. So it's another example of stuffing "features" into a distro that are useful to some set of users, but absolutely dangerous to others, and with no particular warning that the distro has been effectively booby trapped.

Pardon my not finding sufficient humor in this.

---

### Post by whit on 2009-06-16
It looks like Ubuntu is pretty dependent on having NetworkManager running. So the question is how to either disable it from trying to "help" by dropping IP assignments, or how to enable it to restore the assignments when it sees the interface operational again. The current, half-working state, is the worst of all possible worlds.

---

### Post by whit on 2009-06-16
Simply removing NetworkManager leaves Ubuntu in a state where on reboot it does not automatically bring up the interfaces. Also removing NetworkManager is tricky, because if you run /etc/init.d/NetworkManager stop it thinks you want it to shut down your interfaces too.

So far I can't find how to get Ubuntu to bring up the interfaces without NetworkManager in the boot sequence. Putting "/sbin/ifup eth0" etc. in /etc/rc.local isn't doing the trick. Surely there's a way to get Ubuntu working normally without NetworkManager (which after all is only beta software) mucking things up?

Plus even with NetworkManager not in the boot sequence, nm-system-settings starts itself up. There's no /etc/init.d/nm-system-settings init file responsible for that. There needs to be a clean way to clear out NetworkManager and return Ubuntu to behaving like a normal, sane Linux - assuming that not all of us are using it for laptops with DHCP, that some of us don't want automation that's fundamentally unaware of how a system's being used, and poorly documented at that.

---

### Post by whit on 2009-06-16
To really see how badly a project can be done, check out the NetworkManager homepage at [http://projects.gnome.org/NetworkManager/](http://projects.gnome.org/NetworkManager/) - there's absolutely zero documentation. The only content there is PR happy speak. Is there any motion in Ubuntu development to provide an alternative to this seriously compromised Red Hat-sponsored project?

Now, it looks like others have tried to work around this problem. For instance: [http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html/comment-page-1](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html/comment-page-1) - but trying to substitute /etc/init.d/networking doesn't work for me - fails to bring up both interfaces. I've also looked at the NetworkManager wiki and elsewhere, trying to find for instance the full syntax to nm-system-settings.conf. This stuff is absolutely not documented - at least not in the obvious places, like linked from the project's own homepage.

---

### Post by redmk2 on 2009-06-17
Whit,

Where do I begin?  Yes, Network Manager can be an evil beast.  No, it is not needed to maintain a static (manuallly configured) IP address.> Simply removing NetworkManager leaves Ubuntu in a state where on reboot it does not automatically bring up the interfaces. After removing NM you need to configure the IP address and setup a pointer to DNS manually.  Here is is my **/etc/network/interfaces** file:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.12
netmask 255.255.255.0
gateway 192.168.1.1

```

Note the first line of the primary interface stanza (auto eth0).  This is how you bring up the interface upon booting.

I setup my DNS to first try my local DNS server in my router.  if the request can't be resolved it is forwarded to my ISP DNS.  This is my **/etc/resolv.conf** file```
# Local DNS
nameserver 192.168.1.1

```

> This stuff is absolutely not documented.  It has been discussed to death on this forum.  The best description I have seen is [**_here_**]("http://www.arachnoid.com/linux/NetworkManager/index.html").  I caution you, this is for info only.  I believe that you should manually configure ANY IP address that is on host that is managed remotely.

Would I use NM?  Does it have a use?  Indeed it does.  If you have a netbook/notebook and you don't want to mess with setting up wireless at each coffee shop you visit, I would let NM have its way.  This also means it's not mission critical or remote from me.

One further thought to get rid of all that is Network Manager ```
sudo apt-get [COLOR="Red"]purge[/COLOR] network-manager
```

---

### Post by CDXX on 2011-04-28
So could someone walk a n00ber through how to properly disable NetworkManager and how to properly setup resolv.conf ?

*update
upon further review of the thread I believe I understand how to rid my system of NM but the proper setup of resolv.conf

---

