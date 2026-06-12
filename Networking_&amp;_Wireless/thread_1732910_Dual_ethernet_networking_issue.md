---
title: "Dual ethernet networking issue"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by kerryhall on 2011-04-18
I have a server with two ethernet ports. I configured eth0 to be static, set at 10.1.10.148. I plugged in another router into the other ethernet port in order to configure that router. I configured eth1 to use dhcp. Using /etc/network/interfaces rather than gnome network manager. When I did this, I lost internet connectivity (internet routes through eth0 of course)

*Why did I lose internet connectivity?

In order to recover internet activity, I had to disconnect the new router on eth1 of course, and do sudo ifdown eth1. That wasn't enough however. After rebooting numerous times and pulling out my hair, I finally tried configuring eth0 as dhcp, rather than static, and this fixed the problem.

*Why didn't sudo ifdown eth1 solve the problem? What information was saved between reboots that somehow remembered that I plugged in the new router? Because my thinking was if /etc/network/interfaces was identical, and the network topology was identical, after a reboot everything should be restored, but it wasn't. 

Thanks!

---

### Post by Iowan on 2011-04-18
It's probably a bit too late to check (which is good - if it's now working), but kinda sounds like routing got messed up. The DHCP address probably allowed the machine to get routing information from DHCP server.

---

### Post by Helios747 on 2011-04-18
This happened to me once in Ubuntu server.

My problem was that I forgot to set the gateway in /etc/network/interfaces. (although I was using static addresses)

Is it defined in your interfaces?

---

### Post by kerryhall on 2011-04-19
> **Iowan said:**
> It's probably a bit too late to check (which is good - if it's now working), but kinda sounds like routing got messed up. The DHCP address probably allowed the machine to get routing information from DHCP server.

Hmmm interesting! So what is the correct way to set up one machine to connect to two routers?

---

### Post by kerryhall on 2011-04-19
> **Helios747 said:**
> This happened to me once in Ubuntu server.

My problem was that I forgot to set the gateway in /etc/network/interfaces. (although I was using static addresses)

Is it defined in your interfaces?

The gateway was defined for eth0, the static connection. It wasn't defined for eth1, but that was dhcp

---

### Post by uncaspi on 2011-04-19
Perhaps you need to shut down network-manager or completely remove it.

---

### Post by Iowan on 2011-04-19
> **kerryhall said:**
>  So what is the correct way to set up one machine to connect to two routers?You can configure different IP ranges for each router - but only one should be a default gateway for "everything else". Kinda sounds like you already had it that way...

---

### Post by kerryhall on 2011-04-22
> **uncaspi said:**
> Perhaps you need to shut down network-manager or completely remove it.

I was having issues with the network manager in Lucid, so I have already removed it and have been using manual configuration. (or whatever is the proper way to refer to "non gnome network manager configuration")

---

