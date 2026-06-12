---
title: "network problem"
date: 2009-12-10
forum: Networking &amp; Wireless
---

### Post by TroyStachnik on 2009-12-10
I have Ubuntu 9.10, and i have a   loptop running windows XP with ICS but when i connect my ubuntu to it all i get is the shared files no internet connection, how can i fix this problem?

---

### Post by Iowan on 2009-12-10
How do you connect to it? In particular, IP address settings, gateway, and DNS settings. Are you using crossover cable, or wireless?

---

### Post by TroyStachnik on 2009-12-10
i have wireless on the XP (shared) i connect to the XP via Ethernet, ip settings not sure, DNS i think would be my laptop with XP and ICS enabled.

---

### Post by Iowan on 2009-12-11
Hmmm... if you can access the shared files, it'd seem that the connection is there.  How does XP geet to Internet - router, modem, etc? Can Ubuntu **ping** that machine (bu name or IP address)? If so, can it **ping** internet (by IP address)?

---

### Post by TroyStachnik on 2009-12-12
my xp connects through a wireless router then to a modem then to DSL (AT&T) i can connect to the wireless router configuration but nowhere else on the internet

---

### Post by Iowan on 2009-12-12
So... Ubuntu can see XP's shared files, and can access router through XP? How is Ubuntu's IP address set up - static/manual? What is Ubuntu using for a gateway address? What is in */etc/resolv.conf*?

---

### Post by TroyStachnik on 2009-12-12
if i set ubuntu to automatically receive ip address and configuration it won't connect bit of o set up an ip address it connects and gets the shared files but no internet connection, what should i do? also i ran the netsetup.exe file i created on XP in Ubuntu but that didn't do squat.

---

### Post by Iowan on 2009-12-12
I'm not familiar with XP's ICS. I dunno if it has a DHCP server built in (sounds like it does not). When you set up the manual address, you *should* be able to specify gateway and nameserver  addresses. The gateway would be the XP address. The nameserver(s) either XP or (more likely) your ISP's.

---

