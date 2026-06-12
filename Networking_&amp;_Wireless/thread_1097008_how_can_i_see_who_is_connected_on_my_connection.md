---
title: "how can i see who is connected on my connection?"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by chriskin on 2009-03-15
i need to know if someone else is connected through my connection

how can i check it?

---

### Post by .nedberg on 2009-03-15
Do you mean if someone is using your wireless network?

Log in to your router (usually 192.168.1.0, but depends on your setup) and check dhcp leases.

---

### Post by chriskin on 2009-03-15
it seems to be 192.168.1.1

i couldn't find any dhcp anywhere though

---

### Post by .nedberg on 2009-03-15
What kind of router do you have?

Any status page?

---

### Post by bukwirm on 2009-03-15
It's probably under something like "Router Status" or "Connected Devices".

---

### Post by Crafty Kisses on 2009-03-15
To my knowledge in newer versions of the Linksys firmware, if that's even what kind of router you have, there's an option in the firmware called "MAC Clients" and from there you can see what computers are connected to your router via wireless. You can usually access the router by running the following in the Firefox navigation bar:
```
192.168.1.1
```
The alternative as already stated I believe is to use a DHCP connection table, to see who is accessing your connection.

---

### Post by chriskin on 2009-03-15
thank you, it was at router status.

someone was connected like i though, i changed that password and will check once every some days if there were any other attempts

thanks again :)

---

### Post by chriskin on 2009-03-15
> **Codename said:**
> To my knowledge in newer versions of the Linksys firmware, if that's even what kind of router you have, there's an option in the firmware called "MAC Clients" and from there you can see what computers are connected to your router via wireless. The alternative as already stated I believe is to use a DHCP connection table, to see who is accessing your connection.

it's a pirelli router, not linksys.

---

### Post by Crafty Kisses on 2009-03-15
Oh OK, it seems like you got everything sorted out. Glad it worked out for you. ;)

---

### Post by lisati on 2009-03-15
The best place to check who's connected can vary between routers.

On the Thomson router provided "free" by my ISP, it's on the "Home network" tab, and on its predevessor (one by Netgear that I purchased myself) it's under "attached devices"

 I'm not familiar with routers by pirelli.

---

