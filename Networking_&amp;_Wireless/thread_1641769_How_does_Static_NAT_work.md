---
title: "How does Static NAT work?"
date: 2010-12-09
forum: Networking &amp; Wireless
---

### Post by Amivit on 2010-12-09
Hi.

I have a few questions about Static NAT as I will hopefully soon be getting additional public IPs and want to utilize them. 

If I have a regular 192.168.1.0/24 network, and configure a static NAT rule assigning 173.194.35.104 to 192.168.1.20 - would that be the virtual equivalent of setting up this device directly to the internet with that public IP? 

How will static NAT affect open ports etc., if I host an ftp on 192.168.1.20 and assign him 173.194.35.104, there will be no need for portforwarding? 

Also - will using static NAT, assigning 192.168.1.20 the public ip 173.194.35.104 affect the way other local devices in the 192.168.1.0/24 network communicate with 192.168.1.20, or will it still be the same?

Finally, NAT and VPN can be a bit tricky, but will doing a static NAT rule eliminate all these problems or is there anything I need to know here?

You may also wonder why I don't just try for myself and see what happens, but that would involve purchasing the additional IP's and a more advanced router as the current one does not support multiple WAN-ip's. So would like to make sure everything I want is possible before I take the dive and order the stuff I need :)

Thanks, and I understand this is many questions but please do know how much I will appreciate an answer - and after a lot of googling with very limited documentation, I am sure an answer will help others in the future aswell! Best regards, Amivit

edit: please dont answer, I just got all the info required and will post my own update to hopefully help someone else in the future :)

---

### Post by Amivit on 2010-12-09
> **Amivit said:**
> I have a few questions about Static NAT as I will hopefully soon be getting additional public IPs and want to utilize them.

If I have a regular 192.168.1.0/24 network, and configure a static NAT rule assigning 173.194.35.104 to 192.168.1.20 - would that be the virtual equivalent of setting up this device directly to the internet with that public IP? 

Yes.

> **Amivit said:**
> How will static NAT affect open ports etc., if I host an ftp on 192.168.1.20 and assign him 173.194.35.104, there will be no need for portforwarding?

No, no need. Any packet destined to 64.64.64.64:344 are sent to 192.168.1.64:344

> **Amivit said:**
> Also - will using static NAT, assigning 192.168.1.20 the public ip 173.194.35.104 affect the way other local devices in the 192.168.1.0/24 network communicate with 192.168.1.20, or will it still be the same?

It will still be the same, the local ip's will still be able to communicate.

> **Amivit said:**
> Finally, NAT and VPN can be a bit tricky, but will doing a static NAT rule eliminate all these problems or is there anything I need to know here?

No, it will work fine.

Additionally I asked my source of help what happens when the local ip with the static-nat doesnt receive a packet but transmits one out to the internet. What will the source IP be, the public IP of the static NAT or the public IP of the router's dynamic NAT. The answer is the static-nat's ip address.

Big thanks to bobdole369 at ##networking on FreeNode for helping me out :)

---

