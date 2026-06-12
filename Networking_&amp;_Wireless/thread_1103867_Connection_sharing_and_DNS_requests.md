---
title: "Connection sharing and DNS requests"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by mpcengineering on 2009-03-23
Hi guys,

So I have just spent the weekend setting up an 8.10 desktop ubuntu box as a gateway to the rest of my home network using firestarters internet connection sharing ability, the setup is as follows:

Internet -> Gateway -> Access Point -> LAN

I have setup DHCP on firestarter to serve IP's to the boxes attached to the access point, and given one machine access to the gateway directly for admin and all seems good apart from DNS.

On the gateway machine eth0 is DHCP and is the WAN/internet connectivity and eth1 is static IP and points at the access point and thus LAN.  This machine can resolve DNS names with no problems, but none of the machines connected to the access point can (we are talking external here not internal DNS names).  I have set my ISP DNS server addresses on eth1 but this hasnt worked and machines on the access point cant resolve names even tho they can ping fine.

If I set the DNS per machine, then it all works fine, but I want firestarter to serve DNS servers along with the IP and subnet information as you'd expect from any DHCP setup.  At the moment there is no DNS server server setup on the gateway machine, do I need to setup bind9 or similar and set forwarding to the ISP's DNS servers for names it cannot handle?  If I do this, will bind9 automatically pick up requests being sent at the moment to firestarter (I guess same IP, just different port right)?  I may have missed something but I dont see that firestarter allows you to do this?!?

Thanks in advance

Jon

---

### Post by phantombengi on 2009-05-10
bump

---

### Post by Iowan on 2009-05-10
Dunno if it directly answers your DNS questions, but...
Have you seen [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page on ICS?

---

### Post by superprash2003 on 2009-05-11
what you could do is disable dhcp in firestarter , and manually run a dhcp server separately in ubuntu and specify DNS servers there [http://www.prash-babu.com/2009/05/how-to-enable-dhcp-server-in-ubuntu.html](http://www.prash-babu.com/2009/05/how-to-enable-dhcp-server-in-ubuntu.html)

---

