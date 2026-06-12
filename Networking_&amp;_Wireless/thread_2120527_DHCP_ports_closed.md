---
title: "DHCP ports closed"
date: 2013-02-26
forum: Networking &amp; Wireless
---

### Post by daKoolaid on 2013-02-26
I didn't know I was blocking ports 67-68 out with ufw. These are the ports for dhcp but I had no connection problems with internet. If I open them up, what will this do? I don't need new ip addresses from my router so should I just leave them blocked?

---

### Post by joeashcraft on 2013-02-27
Does this help?

DHCP uses the same two ports assigned by IANA for BOOTP: destination UDP port 67 for sending data to the server, and UDP port 68 for data to the client. DHCP communications are connectionless in nature. [via [wikipedia]("http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol#Technical_details")]

Try blocking only 67 in and out, and see what happens. Try it again with 68. Which one works?

---

### Post by daKoolaid on 2013-02-28
> **joeashcraft said:**
> Does this help?

DHCP uses the same two ports assigned by IANA for BOOTP: destination UDP port 67 for sending data to the server, and UDP port 68 for data to the client. DHCP communications are connectionless in nature. [via [wikipedia]("http://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol#Technical_details")]

Try blocking only 67 in and out, and see what happens. Try it again with 68. Which one works?
What am I looking for as a result of blocking one port or another? I already have full internet access and connecting to new wifi routers and receiving an ip address is no problem.

If I'm interpreting DHCP's use correctly, 'server' in its case would be my (or a) router, since it's what assigns the IP to the specific computer.

Is that correct?

---

