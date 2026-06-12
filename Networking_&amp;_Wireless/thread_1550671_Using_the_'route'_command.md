---
title: "Using the 'route' command"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by Kerubu on 2010-08-11
I'm just trying to learn a little more about networks and have been reading about the 'route' command to display the kernel's routing table however I get results which I did not expect:

> Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.2.0     *               255.255.255.0   U         0 0          0 wlan0
link-local      *               255.255.0.0     U         0 0          0 wlan0
default         .               0.0.0.0         UG        0 0          0 wlan0


I use a wireless network/internet connection provided by a combined wireless base/route & ADSL modem. I know for a fact that the wireless base station IP is 192.168.2.1 and it also runs a DHCP server to allocate IP addresses on my local network. So how come 192.168.2.1 is not showing up in the route table but 192.168.2.0 is?

Also why does the default show up as a '.' ?

If anyone can explain what this routing table means I'd be much obliged.

---

### Post by Sunseeker.ch on 2010-08-11
Try route -n, then it should be clear.

---

### Post by Kerubu on 2010-08-11
> **Sunseeker.ch said:**
> Try route -n, then it should be clear.

Thanks Sunseeker.ch

---

### Post by Iowan on 2010-08-11
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") or are there other questions a (somewhat) rookie can answer?

---

### Post by Kerubu on 2010-08-12
No.. thread marked as solved now

---

