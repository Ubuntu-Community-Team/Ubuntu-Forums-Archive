---
title: "Help With Forwarding Ports for Apache"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by tehroflmaoer on 2009-11-14
I've been having trouble with getting ports forwarded for my server and other computers after I moved. Before I moved, everything was working fine, but when I got here, my ports would not forward. My router is connected to a modem, but I'm pretty sure the modem is not the problem because I've tried forwarding with another router.
I can verify that apache is running, because I can access it from computers within my network. A thread I read in another forum said that DHCP servers in the modem and the router can conflict, which can mess up forwarding, but I did not know what to make of that.

I have a linksys WRT310N and my computers are running 9.10 and 8.10, if that's any help.

Thanks in advance.

---

### Post by SGAZ on 2009-11-14
If you changed Internet companies when you moved your new ISP may be blocking the port you are/were serving on - Especially if it was the default port 80.  You can change the port you are serving on in Apache and that might help.

Good luck.

---

### Post by tehroflmaoer on 2009-11-15
> **SGAZ said:**
> If you changed Internet companies when you moved your new ISP may be blocking the port you are/were serving on - Especially if it was the default port 80.  You can change the port you are serving on in Apache and that might help.

Good luck.
I have the same ISP as before. SSH and setting up torrents on a random port doesn't work either.

---

### Post by Iowan on 2009-11-15
> **tehroflmaoer said:**
> A thread I read in another forum said that DHCP servers in the modem and the router can conflict, which can mess up forwarding, but I did not know what to make of that.Does your server get a DHCP address? The external address has probably changed - or do you have a static address?

---

### Post by tehroflmaoer on 2009-11-15
> **Iowan said:**
> Does your server get a DHCP address? The external address has probably changed - or do you have a static address?

My server/other computers get internal IPs from the router, and I have an external address which I check every time I test (It's dynamic).

---

### Post by Iowan on 2009-11-15
A dynamic address on the server will complicate port forwarding. Your router is *probably* capable of issuing a "static lease" (fixed address) based on MAC address. I have a server and printer set up that way.

---

### Post by tehroflmaoer on 2009-11-15
> **Iowan said:**
> A dynamic address on the server will complicate port forwarding. Your router is *probably* capable of issuing a "static lease" (fixed address) based on MAC address. I have a server and printer set up that way.
I've actually already set up a DHCP reservation for my server, but I forgot about that, so it always has the same internal IP. My external IP is still dynamic though, if that's any help.

---

### Post by Iowan on 2009-11-15
How did you access the machine before? Did you have account with dyndns.com or no-ip.com (or something similar)?

---

### Post by tehroflmaoer on 2009-11-15
> **Iowan said:**
> How did you access the machine before? Did you have account with dyndns.com or no-ip.com (or something similar)?
Yea, I used dyndns with ddclient on my server, but I could just get to it by checking my external IP at a site like whatismyip.com.

---

