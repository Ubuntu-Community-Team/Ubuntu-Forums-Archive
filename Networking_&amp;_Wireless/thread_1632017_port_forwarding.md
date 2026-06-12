---
title: "port forwarding"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by BSOD64 on 2010-11-27
I'v got a Motorola 2210-02 modem connected to a switch witch goes to all the computers on my network. all the computers on my network also have static IPs. I want to have a server running on my computer but I cant figure out how to port forward.

---

### Post by NoNameWill on 2010-11-27
type in 191.168.2.1 or 191.168.0.1 or .....1.1 this should take you to the setup page for your router. If that doesn't work go to the company that made the router's page and get the manual. Once you get to the setup page it's pretty self explanatory.

However once inside go to something like virtual server. Then set up port forwarding from there. Set up the ports needed to forward to the computer's network IP to the port your sever is set up on. Which you will find in the client list. More than likely it will start with 191.168.x.x  The x=your network setup.

---

### Post by BSOD64 on 2010-11-27
when I type "192.168.1.254" into my web browser I get a configuration page but theres nothing about port forwarding anywhere.:-|

---

### Post by NoNameWill on 2010-11-27
> **BSOD64 said:**
> when I type "192.168.1.254" into my web browser I get a configuration page but theres nothing about port forwarding anywhere.:-|

Nothing on that page about the firewall? I am assuming your router has a NAT firewall?

Also have you set up the firewall on your sever to accept requests?

---

### Post by BSOD64 on 2010-11-27
I've fixed this problem with hamachi but thanks anyway!;)

---

