---
title: "dhcp3 server question"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by ripeart on 2010-01-15
Hello,

I have a mixed wired/wireless LAN. Ubuntu 9.1 Desktop is running off a G5 and I would like to use it as a DHCP server and eventually have it become a firewall and internet proxy.

Equipment:

Cable modem --> WRT54G --> Switch

The WRT54G is for wireless clients and the switch connects my wired clients (printers, network media server, etc.)

The problem I am facing is that I have wired and wireless clients that need to get their IPs from the server. The G5 is connected to the network via ethernet and I do not have a wireless adapter for it. Is there any way to circumvent using the Ubuntu box for DHCP? I can't think of any since the wireless clients need to get their IP info wirelessly.

Any thoughts would be appreciated.

Thanks!
[B]
edit1: Oh wait! Can my WRT54G be a DHCP client?!

[/B]edit2: Please tell me if this would work:

Cable modem --> [WAN IP] **WRT54G** [LAN IP 200.1.1.1] --> **G5** [IP 200.1.1.2] DHCP server --> [200.1.1.3 - 31]/27 - however in that configuration, how would the wireless clients get their IPs?

---

### Post by ripeart on 2010-01-18
[SIZE=3]So no one kno[IMG]http://ubuntuforums.org/images/editor/menupop.gif[/IMG][/SIZE][SIZE=3]ws? I would really appreciate some guidance before tearing apart my network. I don't intend to sound like I am entitled to guidance however I believe that Ubuntu Forums exists for this very reason.

[/SIZE]:-?

---

### Post by CharlesA on 2010-01-18
Are yer IP addresses really 200.x.x.x??

Anyway, if you disable the DHCP server on the wireless router, wireless clients should be able to be assigned an IP address from the wired server, if it's on the same subnet.

Example:

WAN----AP---Switch---DHCP

AP would be 192.168.1.1
DHCP server is 192.168.1.2
Scope of IP addresses would be 192.168.1.3 to 192.168.1.10.

EDIT: The router cannot be a DHCP client, as it needs a static IP.

---

### Post by ripeart on 2010-01-20
Thank you! I'll give that a go.

re:IPs - they aren't yet, but I was playing around with a subnet calculator and 200.x.x.x works. I'm so tired of 10. 192. 172. plus I'm trying real hard to be a non-conformist.:|

---

### Post by Iowan on 2010-01-20
> **ripeart said:**
> ... I'm trying real hard to be a non-conformist.:| Keep it in mind if you have strange DNS problems later... :D

---

### Post by ripeart on 2010-01-20
hah! I will.

but what like, internal DNS issues?

---

### Post by adam814 on 2010-01-20
I think by definition home routers like that are DHCP clients.  Mine pulls an IP from my cable modem.

If you want to use the Ubuntu machine for a firewall/router you should be able to connect it like this:
Cable modem -> Ubuntu box -> WRT54G -> switch

Then connect everything else as usual (except disable DHCP on the router).  Of course that assumes you already have it functioning as a router with a suitable firewall.

---

