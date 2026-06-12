---
title: "Port Forwarding Problem"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by databoy2k on 2011-02-27
Hey All:

I had a system working earlier today, until I tried to set up OpenVPN. Somehow, I've broken my forwarding, and am seriously stuck on what is keeping it from working.

I've got Ubuntu Server 2.6.35-25 (IP 10.10.1.50), and a Windows 7 Desktop (IP 10.10.1.45). I'm trying to forward a remote RDC request made to port 6100 on the Ubuntu box to port 3389 on the Windows box. All connections are going through Eth0 on the Ubu box.

The IPTables entries that I'm inputting are as follow:
~# iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
~# iptables -t nat -A PREROUTING -p tcp -i eth0 -d 10.10.1.50 --dport 6100 -j DNAT --to 10.10.1.45:3389
~# iptables -A FORWARD -p tcp -i eth0 -d 10.10.1.45 --dport 3389 -j ACCEPT

Is anything striking you guys as off about those three commands? Shouldn't that do the trick?

Thanks for any help!
--Databoy2k

--EDIT--
Solved, more or less. It always helps to turn on your port forwarding:
echo 1 > /proc/sys/net/ipv4/ip_forward

Got it. Thanks!

---

### Post by databoy2k on 2011-03-16
I hate to bump, but... Anybody familiar with iptables?
--Databoy2k

---

