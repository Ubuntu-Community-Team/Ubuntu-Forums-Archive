---
title: "Desktop running debian no longer connects to my router"
date: 2013-05-12
forum: Networking &amp; Wireless
---

### Post by Stonecold1995 on 2013-05-12
I have a desktop computer connected to my router via Ethernet.  I changed routers a while ago though, and now the computer is unable to connect.

I had the comptuer set up (using dropbear, or something similar iirc) to connect to Ethernet automatically and wait for my other computer to SSH in and give it the encryption keys (I'm using full disk encryption).

When I start up manually (i.e. plug in a monitor and enter the encryption key via the keyboard instead of SSH) and log in, the internet STILL isn't connected.

The computer is running headless Debian stable.

Any ideas?

---

### Post by 2F4U on 2013-05-12
Are you using a fixed or dynamic IP address? I guess you are using a fixed one. Maybe this address is occupied by some other device after switching routers? Is the subnet correctly configured, e. g. routers often come with 192.168.0/24 preconfigured, if, for example, your fixed address is 192.168.3.2 you won't be able to connect.

---

### Post by Stonecold1995 on 2013-05-12
My external IP is dynamic, but it sounds like you're talking about internal, which is DHCP.

My old router used 192.168.0/24, but my new one does not.  That shouldn't be a problem for my desktop computer though, right?

My rotuer doesn't even detect my computer ([screenshot]("http://oi40.tinypic.com/x3z67d.jpg")).

---

### Post by Stonecold1995 on 2013-05-16
bump

---

### Post by Stonecold1995 on 2013-05-20
bump

---

