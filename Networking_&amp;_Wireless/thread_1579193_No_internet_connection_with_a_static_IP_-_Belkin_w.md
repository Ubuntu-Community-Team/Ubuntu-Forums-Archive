---
title: "No internet connection with a static IP - Belkin wireless"
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by themusicalduck on 2010-09-21
edit: Nevermind, I found the right details to use on here - [http://www.belkin.com/support/kb/kb.asp?a=2824](http://www.belkin.com/support/kb/kb.asp?a=2824)

I'm trying to setup a static IP for my PC through a wireless connection.

I edit the connections for the wireless through the network manager. Put 192.168.2.100 for the Address 255.255.255.0 for the Netmask and 0.0.0.0 for the Gateway. I then put the DNS servers as what is listed on my router control panel 194.168.4.100, 194.168.8.100.

The network will connect, but I cannot view any websites or connect to the router home page again unless I re-enable DHCP.

According to 'Internet Settings' on my routers home page, it says Subnet mask is 255.255.248.0 and default gateway is 82.32.32.1. I tried those instead of the other IPs, but still got no luck. The website will appear to be loading, but get stuck on 'Resolving host' and eventually time out. However, with the first settings, it just says that it cannot find the page instantly.

I also tried using Google's DNS servers 8.8.8.8, 8.8.4.4 but got the same result.

I managed to get this to work fine on another modem with a wired network in the exact same way, so I'm not sure why it refuses to work this time.

I have a Belkin wireless dongle and a Belkin router model F5D7231-4 2000. I have Ubuntu 10.10.

---

