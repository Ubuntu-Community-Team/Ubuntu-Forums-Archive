---
title: "linksys router configuration"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by Hansmc on 2009-05-02
I have a dsl modem, a printer, & two computers all connected with a hub. And they all work fine. However now I am trying to add a WRT54G Linksys wireless router to the network. So I unplugged one of the computers and plugged that cable into the Internet port on the router. Then I used another cable to plug the computer into one of the LAN ports on the router. The router was able to get an IP, etc from the modem.

Login Type: Automatic Configuration - DHCP
IP Address: 192.168.1.44
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.1.1
DNS 1: 192.168.1.1

And my computer got an ip address from the router:

IP Address: 192.168.1.100
Subnet Mask: 255.255.255.0

The problem: No Internet access. What configurations do I need to be changed to make it work with this set up? Also how can I get to our printer that is on the other side of the wireless router? One other thing; it will not work to place the router between the modem and hub, because they are both at the wrong end of the place.

Thanks for your time.

---

### Post by chili555 on 2009-05-02
Have you tried this?


Modem
|
|
Router --> Printer
            |
            |------> Computer
            |
            |------> Computer


Hub---> eBay

---

### Post by freebeer on 2009-05-02
Until you run out of LAN ports on the router, you don't need to have the hub in the loop at all.  If it's a real hub as opposed to a switch, then you're best off taking it out.  Hubs are dumb and just broadcast traffic on all ports.  Switches actually direct traffic to the intended recipient.  The latter cuts down on network traffic.

If you want to keep the hub in the loop (for future expansion, or whatever), you would insert the router between the hub and the modem.

---

### Post by Hansmc on 2009-05-02
> **freebeer said:**
> If you want to keep the hub in the loop (for future expansion, or whatever), you would insert the router between the hub and the modem.

I can not do that with out running a bunch more wires. I know this splits our network up into two, but it should be able to work that way. Thanks for your input.

---

