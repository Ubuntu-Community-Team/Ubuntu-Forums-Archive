---
title: "Need help setting up DHCP Server"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by gtbutler on 2010-07-09
I am trying to setup a router using Ubuntu 10.04 i386 Desktop and am having trouble understanding ip addressing using DHCP3.

I have a modem that is giving me a DHCP address 192.164.1.64 on ETH0 and I can connect to the internet. My problem is getting a subnet working on ETH1.

How do I assign an address to the subnet with lease addresses of about 20. I only have about 10 machines I want to be on the subnet.

I don't know how to set up the dhcp server.

Any help will be greatly appreciated.

Thanks

---

### Post by Iowan on 2010-07-09
I had a DHCP3 server before converting to DNSMasq when I upgraded from Breezy to Hardy. As I recall, the [dhcpd.conf]("http://manpages.ubuntu.com/manpages/karmic/man5/dhcpd.conf.5.html") file had pretty good examples. Is it a DHCP problem, or an [ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing") (connection sharing) issue?

---

### Post by capscrew on 2010-07-09
> **gtbutler said:**
> I am trying to setup a router using Ubuntu 10.04 i386 Desktop and am having trouble understanding ip addressing using DHCP3.

I have a modem that is giving me a DHCP address 192.164.1.64 on ETH0 and I can connect to the internet. My problem is getting a subnet working on ETH1.

How do I assign an address to the subnet with lease addresses of about 20. I only have about 10 machines I want to be on the subnet.

I don't know how to set up the dhcp server.

Any help will be greatly appreciated.

Thanks

I have to agree with Iowan here. You should decide what the device that is directly connected to the modem really is.  The description of which can be very blurry.  

In essence, if you are also using  the device (i.e the router you are creating) for destop duties then you need to look at Internet Connection Sharing.  I have never done that but it can't be too hard.  See [**_here _**]("https://help.ubuntu.com/community/Internet/ConnectionSharing")for some basic info.

If you are creating a dedicated router then convention says that you should create a separate subnet (such as 192.168.[COLOR="Red"]**2**[/COLOR].0/24).  The DHCP server should service *this subnet only*.  The pool of addresses is a configurable parameter, so you can set the range to what ever you want in that subnet.

With the router configuration like above, the MODEM should supply the IP address only to eth0.  This also means you need to go into syscntl and set IPtables to forward all IPv4 traffic.  In addition you can use NAT.  See [**_here  _**]("https://help.ubuntu.com/community/Router") for info.

---

