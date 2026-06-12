---
title: "routing outgoing traffic to different interfaces"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by alesi_27 on 2011-06-30
Hi, Im quite experienced in using Linux and Ubuntu but still cant find a clean solution to a little problem.

Im usually at work and I have to use an internet proxy to reach internet. Sometimes I'd like to reach internet without using proxy, so I tought to buy an internet key with a flat rate.

Now when I'll connect with internet-key, I will hopefully have another network interface, alongside wlan0 and eth0.

Since there are still lots of machine inside the local network, I would like to use eth0 for some ranges of IPs and the new broadband connection for "the rest of the world".

Enterprise DHCP gives me 172.16.x.x/255.255.252.0 IP, so I need to reach machine in this network through eth0, but also 192.168.x.x are to be routed on eth0. Any other connection not in these rages of IP, must go on the broadband connection.

Is there an easy and clean way to do this ?

Thank you

---

### Post by Cheesehead on 2011-06-30
man route

---

### Post by helgman on 2011-06-30
> **Cheesehead said:**
> man route

If your company only uses "private addresses" (RFC 1918) in the network then you point them (10/8, 172.16/12, 192.168/16) out eth0 and then make a default route pointing the other way. Anything not pointing out eth0 will then go out the other way.

Just make sure that you remove the default route handed to you by the DHCP-server (you might have to go back and remove from time to time). Or you could try to make the cost of the other default route lower than the one handed to you from the DHCP.

Regards,
Helgman

---

### Post by Cheesehead on 2011-06-30
Helgman said that much better than I could.

---

