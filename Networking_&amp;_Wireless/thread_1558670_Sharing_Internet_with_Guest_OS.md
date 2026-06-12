---
title: "Sharing Internet with Guest OS"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by anieruddha on 2010-08-22
Hi,

I have installed debian and rhel as guest os. My host machine in Ubuntu 10.04. I connected to the internet through 'wvdial' utility.
 I manage to connect both guest os with host machine and I can ping them from host to guest and vice versa. 
My problem is I am not able to share the internet. Is there any way, so I could connect to the internet from guest.

---

### Post by Iowan on 2010-08-22
I've been wrong before, but I'm not sure the guest OS should have a bearing on ICS. [Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for ICS, but it may need some tweaking to work with **wvdial**.

---

### Post by anieruddha on 2010-08-25
I installed Squid (Proxy Server) on Host OS and from Guest OS, I configure the proxy settings. And It works.
Thanks for Reply.

---

