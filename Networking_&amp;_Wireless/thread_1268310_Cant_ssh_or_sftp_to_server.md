---
title: "Cant ssh or sftp to server"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by k33bz on 2009-09-16
I can ssh and sftp to my server ONLY if I am connected to the same LAN. Did not know till now, first time I tried to access it away from home.

I have a feeling it has to do with my router. How do I configure it properly where I can ssh or sftp my server when I am away from home. This is critical.


Dont know if this is something worth saying or not, but I can see my website VIA web no matter where I am.

More than one computer is hooked up to this router.

---

### Post by wojox on 2009-09-16
Port Forward the port and ip of the computer you want to connect to via ssh.

Just like you did with your Web Server.

---

### Post by k33bz on 2009-09-16
I had already done that, or is there a special permission I need to do where it will enable any ip to access it as long as the right username and passwd is authenticated?

or can I use a mac address to authenticate it. I travel alot, but always have my laptop, I access it through my laptop

---

### Post by wojox on 2009-09-16
Try:

```
ssh login:password@the pc I want to get connected to
```

Or

```
login@the pc I want to get connected to
```

---

### Post by k33bz on 2009-09-16
nope, timeout still

---

### Post by AlexenderReez on 2009-09-16
i doubt that it use private ip...which you need to configure the router to access it, from normal ip point.

---

### Post by k33bz on 2009-09-16
> **AlexenderReez said:**
> i doubt that it use private ip...which you need to configure the router to access it, from normal ip point.

Its a Linksys router, how would I go about changing it?

---

