---
title: "Server stopped responding to name"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by cackles on 2010-02-24
For what I can see as no reason my server has stopped responding on http/putty by its name.

I can still use its IP to get in via putty and use web apps, but for some reason when I [http://boxname](http://boxname) it does not respond and the page times out.

When I putty in via the IP it tells me its Linux name.

I havent changed any settings.

I dont even know where to start to fix this.

---

### Post by Iowan on 2010-02-24
What does your system use for local DNS? Ping by name probably doesn't work either?

---

### Post by cackles on 2010-02-25
Just checked ping by name, it works. 32ms response time, 0% loss. Ping by IP is 0ms.

Im using Ubuntu server with a D-Link router, but haven't altered any settings.

---

### Post by Iowan on 2010-02-25
> **cackles said:**
> Just checked ping by name, it works.That's a bit of a surprise... 
I presume you use PuTTY for SSH...

---

### Post by cackles on 2010-02-25
Yea I use putty. It doesnt connect by name either, just IP.

---

### Post by n0dix on 2010-02-25
Do you have the ip machine with their domain main in your hosts file?

---

### Post by cackles on 2010-02-26
This is just a simple setup on a LAN. There is no Apache test page, no Azureus GUI page and no MediaTomb page. I can get to them using the [http://IP:port](http://IP:port) but not [http://boxname:port](http://boxname:port).

---

### Post by cackles on 2010-10-13
Im still getting this and the box needs rebooted to get it to come back up.

Samba keeps working fine.

---

