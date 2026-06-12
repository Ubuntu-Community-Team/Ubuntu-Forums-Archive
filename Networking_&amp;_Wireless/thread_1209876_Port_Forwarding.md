---
title: "Port Forwarding"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by growden92646 on 2009-07-10
Using 9.04 as a router.  Eth0 is lan, Eth3  is Wan.
Using Firestarter.
All works correctly a this point.

I have several appliances that have built in web pages.  I need to be able to see them externally.  I went to Firestarter on Outbound events and created a policy for each one.
Such as <service>unknown <port>49152  forward  IP (my.static.ip) port 80.

I can access each of the appliances from the lan just fine.  I cannot connect externally.
using my.domain.com:49152  I get a server can't connect error.

Kinda stuck, looked through documentation and threads but evidently my google-fu is weak today.


TIA,

Gerald

---

### Post by XCan on 2009-07-10
Wouldn't that be inbound events? What you want is to open the ports so that someone from the outside can access your computer through those ports.

---

### Post by growden92646 on 2009-07-13
edit edit edit!... Yes, they are inbound events, I meant to type in that outbound events are set to permissive.  

Sorry for the confusion,

~Gerald
"The fact that married couples live with each other every day is a miracle that the Vatican has overlooked"- Bill Cosby

---

### Post by superprash2003 on 2009-07-13
have you opened the port on your router?

---

### Post by growden92646 on 2009-07-13
I am using this machine as the router, and firewall w/NAT enabled.  I scanned the ports from one of the websites posted here and the desired ports are reading open.  I can access the appliances from the Lan, just keep getting the server is taking too long to respond error.

---

### Post by growden92646 on 2009-07-13
Further informatin, hopefully useful.
For troubleshooting, I allowed port 80 connections (inbound)
Set policy to forward port 80 to 192.168.x.x Port 80
Still cannot connect, "Server is taking too long to respond"


Thanks,

~Gerald

---

### Post by XCan on 2009-07-13
Since you're using firestarter, what does the log window show? Does it show any blocked events?

---

### Post by growden92646 on 2009-07-14
Yes, they are being blocked in the events log.

~Gerald

---

