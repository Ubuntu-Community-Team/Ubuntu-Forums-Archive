---
title: "Configure static IP address"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by bazsl on 2009-06-21
Ubuntu Desktop 9 running in a VMware 5.5.6 virtual machine hosted on XP Pro SP3 using VMware bridged networking.

Ubuntu can connect to my local network and the Internet as long as I use DHCP using the default Automatic setting. However, when I try to edit the eth0 adapter using Network Manager and change to a static IP address on my LAN I cannot connect. Can someone point me to instructions for configuring a static IP address?

Note that I am very new to Linux. Thanks.

---

### Post by tmht on 2009-06-23
You can not connect to the internet or you can not connect to any machines at all on the network?

Try connecting and typing in ping 74.125.45.100 and see if it gives you anything back.  If it does it could be a DNS of some kind.

---

### Post by jhannah on 2009-06-24
Are you also configuring your name servers and default route when setting up the interface manually? After setting it up, please post the results of the below commands:

```

ifconfig eth0
route -n
cat /etc/resolv.conf

```

If you don't see a route with a destination of '0.0.0.0', that is indeed the problem. If so, go ahead and run DHCP on the interface and run the same commands and that should tell you what exactly you need to set.

Let me know what you find.

---

