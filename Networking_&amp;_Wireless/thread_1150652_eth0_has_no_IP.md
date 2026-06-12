---
title: "eth0 has no IP"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by scott29 on 2009-05-06
When my system starts up, eth0 is "not ready" and it has 0.0.0.0 for an IP address (IPv4).  I have a br0 interface for OpenVPN, and that has the correct IP address as issued by my router.

When I start Firestarter, it always complains that eth0 is not ready, but it eventually starts.  

The system gets out to the internet, but it seems incorrect for eth0 to not have any IP. 

I entered the following in /etc/network/interfaces, but eth0 still has no IP after booting:

auto lo eth0
iface lo inet loopback
iface eth0 inet static
address IP_ADDR
netmask MASK
gateway GTWY

What am I doing wrong?

Thanks.

---

### Post by chili555 on 2009-05-06
Your interfaces file is a bit rough. Please amend it to:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address IP_ADDR
netmask MASK
gateway GTWY
```Post back and let us know.

---

### Post by scott29 on 2009-05-06
> **chili555 said:**
> Your interfaces file is a bit rough. Please amend it to:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address IP_ADDR
netmask MASK
gateway GTWY
```Post back and let us know.

Hi,

Thanks for the reply.  I actually pasted the wrong item.  What you suggested is exactly what I have in place.

The only other thing of potential interest is I am trying to assign the same IP to eth0 as is assigned to br0 (the bridge for OpenVPN).  I am not sure if that would cause an issue or not.

Also, I've uninstalled the gnome network manager as well...It seems it causes issues with static IP's and I thought that may be the issue, but still no  luck.

---

### Post by chili555 on 2009-05-06
> I am trying to assign the same IP to eth0 as is assigned to br0That is probably the problem. Please try another address for br0, perhaps one number higher.

---

### Post by scott29 on 2009-05-06
What would be the benefit or need to allow br0 and eth0 to have different IP addresses?  I can try this out and report back, but I'm just curious what it would mean if those interfaces end up with different IP's.

As I said, things "seem" to work now - I can get to the internet, and the VPN works.  Perhaps this isn't worth the trouble, but it does seem odd to me that eth0 ends up with 0.0.0.0

Thanks
scott29

---

### Post by scott29 on 2009-05-06
Trying another IP address didn't do anything...After reboot, eth0 says 0.0.0.0.  Once gain, if I restart networking, it gets an IP address as specified in the interfaces file.

I may have left out some valuable information.  I looked in more detail at my network settings and Firestarter, and I'm not sure exactly what everything is here.  

I have the following showing up in the Firestarter connections:

tap0 (VPN Tunnel)
eth0 (Internet)
pan0 (unknown)
br0 (unknown)

pan0 never shows any activity.  eth0 and br0 seem to move in lock step with each other and have the same general activity.  tap0 shows activity only when I have an active VPN connection.

Like I said, even with 0.0.0.0 I have internet connectivity and the VPN works.  I have no idea if this is simply a display issue or what.  It doesn't make any sense to me how if eth0 had no IP, how I could access the internet.

---

### Post by chili555 on 2009-05-06
> I have no idea if this is simply a display issue or what.Me, too. I suggest that if everything is working as expected, that you do nothing.

---

### Post by Carl Filby on 2009-05-06
auto lo iface lo inet loopback  auto eth0 iface eth0 inet static address IP_ADDR netmask MASK gateway GTWY  ---   comment out "auto eth0"   auto is setting to dynamic   but on next line you try to set static to read:  auto lo iface lo inet loopback  #auto eth0 iface eth0 inet static         address xxx.xxx.xxx.xxx         netmask xxx.xxx.xxx.xxx         network xxx.xxx.xxx.xxx         broadcast xxx.xxx.xxx.xxx         gateway xxx.xxx.xxx.xxx         dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx         dns-search

---

### Post by scott29 on 2009-05-06
Didn't work...still has 0.0.0.0 after startup.  

The only way to get eth0 to get an IP is to restart networking.  And eth0 has to have an IP address or Firestarter will not start.

I don't know if this issue is because of the 9.04 upgrade or what.

---

