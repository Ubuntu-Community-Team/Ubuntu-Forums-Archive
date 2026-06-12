---
title: "ubuntu within a public lan"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by BRooNiE on 2009-09-28
Hello,
i am a new user to ubuntu on my msi wind netbook.

I'm going to use this netbook for college work etc and the college itself has a wireless LAN which i can connect to for network resources internet etc.

im wondering if there is any way that someone else on the wireless lan can get into my system? im not well aware of how good the security is, and that i have to take measures to protect my files from anyone accessing them over the network.

thanks

---

### Post by Iowan on 2009-09-28
Security is generally good with Ubuntu - and it comes with a firewall that you can configure (**ufw**). Dunno if *anything* is completely bullet-proof...

---

### Post by BRooNiE on 2009-09-28
so generally they wont be able to access my files over the network?

---

### Post by Iowan on 2009-09-28
In general, they would need to log into your machine with a valid username and password.

---

### Post by BRooNiE on 2009-09-28
> **Iowan said:**
> In general, they would need to log into your machine with a valid username and password.
is that from the computer itself or from a different location?

if so can i disable logging in from a different location and only from the machine itself?
also with sharing files/folders, can i disable sharing of all files and folders?

---

### Post by Iowan on 2009-09-28
Ordinarily, you'd need to install something (a server) to share files or permit remote access (like SSH, VPN, etc.).

---

### Post by Jazzy_Jeff on 2009-09-28
You should be fine as long as you have not set up sharing. If you are that worried about it you could also encrypt your home partition.

---

