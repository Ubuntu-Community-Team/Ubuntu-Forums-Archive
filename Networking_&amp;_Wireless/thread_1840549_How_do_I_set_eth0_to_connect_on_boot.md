---
title: "How do I set eth0 to connect on boot?"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by pirattrev on 2011-09-07
I'm currently running 10.04 LTS server on a TS130 ThinkServer. Unfortunately because I have the new 82579LM gigabit network card, in order to connect I had to compile the module separately and modprobe it to enable eth0.

Because I'm using this as a remote server on a static IP, I routinely need to SSH to it, but whenever it needs to be reset, I must run
```
sudo dhclient
``` after logging in locally on the box, or else it cannot connect to the internet.

Is there anyway I can automate the box to auto-connect eth0 by running dhclient as root on startup?

---

### Post by praseodym on 2011-09-07
You can add

```
dhclient eth0
```
into the /etc/rc.local [COLOR="Red"]before[/COLOR] the phrase "exit 0" via:

```
sudo nano /etc/rc.local
```

CTRL+x to save & exit

---

### Post by papibe on 2011-09-07
It is mainly done on /etc/network/interfaces. Could post yours ?
Regards.

---

### Post by Iowan on 2011-09-07
Are you getting a static lease from the DHCP server?  Otherwise, I'm confused why you need **dhclient** with a static address. As mentioned (especially on a server - without Network Manager) */etc/network/interfaces* is the place to start.

---

### Post by pirattrev on 2011-09-07
> **Iowan said:**
> Are you getting a static lease from the DHCP server?  Otherwise, I'm confused why you need **dhclient** with a static address. As mentioned (especially on a server - without Network Manager) */etc/network/interfaces* is the place to start.

I'm running the box behind a proxy router so the box need only make a request and the proxy decides the IP.

---

