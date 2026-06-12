---
title: "Relative Noob - need help with wired connection"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by randalotto on 2008-12-16
So I'm having some rather odd problems...

First of all - the router and modem are definitely working. Every other computer connects just fine - wired or wireless.

**My computer refuses to connect to the internet.** It worked fine for the last 4 weeks. Before that, I had similar problems that just disappeared.

I've tried automatic DHCP settings, DHCP address only settings, and what I always use, manual settings. 

Oddly enough, VMware running in Ubuntu can connect to the internet. I'm posting from an XP install from within VMware, so some form of virtual ethernet port is working. No applications running "in Ubuntu" connect though. I can, however, connect to the router's configuration page in Firefox.

I have no idea where to begin or how to fix this. Any help would be greatly appreciated.

---

### Post by swat-leader on 2008-12-17
hey randalotto,
               im quite new to ubuntu 2 but you could try this 

open teminal (alt+F2)  and type

sudo /etc/inted.d/networking restart

or do 

ifconfig and fine network number should look like (eth0)

and the do 

ipup (interface name here e.g eth0)

and that should work 

Swat Leader
"team Move"

---

### Post by cubeist on 2008-12-17
just a small typo in above post, should be:
```
sudo /etc/init.d/networking restart
```

---

### Post by swat-leader on 2008-12-17
> **cubeist said:**
> just a small typo in above post, should be:
```
sudo /etc/init.d/networking restart
```

Thanks Small typo but would that be right???

---

### Post by randalotto on 2008-12-17
No go.

Tried restarting networking, (which I've done lots of times before,) and of course, it doesn't work. 

Also, "ipup" isn't a recognized command...

---

### Post by MulletMan on 2008-12-17
It's "ifup" not "ipup"

Can you ping websites? Try pinging google.ca

Also, try
nslookup google.ca

and see what happens.

---

### Post by randalotto on 2008-12-17
Trying ifup eth0 gives me
"ignoring unknown interface eth0=eth0"

Pinging gives me
"ping: unknown host google.com"

nslookup:
";; connection timed out; no servers could be reach"

:(

---

### Post by Iowan on 2008-12-17
Uh-oh, not a good sign... I suspect **ifconfig -a** will show no (IPv4) address for eth0.

---

### Post by randalotto on 2008-12-17
Actually, everything looks good there (to me at least...)

I'm having troubles pasting it, but it shows:


inet addr:192.168.2.129  Bcast: 192.168.2.255  Mask: 255.255.255.0
(then lots of other stuff...)

---

### Post by MulletMan on 2008-12-17
Can you ping your own computer?

Try ```
ping 127.0.0.1
```

Also, try pinging your router's IP.

And can you post the results of ```
cat /etc/resolv.conf
```

---

### Post by einstein on 2008-12-17
resolvconf was messing me up on this front - kept writing strange and useless info to /etc/resolv.conf.  The 'puter had no way of doing a DNS lookup (even though the puter is running a DNS).  I could ping other devices on the local network but nothing the other side of my router.

I uninstalled resolvconf, manually edited /etc/resolv.conf with something sensible (like a nameserver or two) and life is good.

---

