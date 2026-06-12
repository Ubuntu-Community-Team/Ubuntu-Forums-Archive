---
title: "help with ssh"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by cdog2800 on 2010-01-02
Hi I'm having issues with SSH on ubuntu 9.1 server. When I am on my home network I can successfully login via SSH from any of my linux laptops to my Ubuntu server. How do I use SSH to gain access to my home linux server from any remote location on the Internet? 

Any help would be greatly appreciated.

---

### Post by Warren Watts on 2010-01-02
You need to make sure that you forward port 22 (or whatever port you choose to use) in your router configuration, so that all outside SSH traffic gets routed to the server.

Just remember that your router may not assign the same local IP to you server each time your server connects to the router.  You can fix this by manually setting the IP of the server.  Most routers have a means of forcing an IP to a certain MAC address, so that when the server is attached to the router it will always give the router the same IP.

Once you have set the server's IP, you can set the router to forward your SSH port to that IP.

You should then be able to log into the server from over the internet by establishing an SSH connection to your ISP assigned IP.

---

### Post by Iowan on 2010-01-02
After you have your router port-forwarding the SSH connection, you will need a way to find your router on the internet using a service like [DynDNS.com]("http://www.dyndns.com/services/dns/dyndns/") or [no-ip.com]("http://www.no-ip.com/")... unless your ISP provides you with a static IP address.

---

### Post by Warren Watts on 2010-01-04
> **Iowan said:**
> After you have your router port-forwarding the SSH connection, you will need a way to find your router on the internet using a service like [DynDNS.com]("http://www.dyndns.com/services/dns/dyndns/") or [no-ip.com]("http://www.no-ip.com/")... unless your ISP provides you with a static IP address.


Ah yes.... I did leave that out.  I use no-ip.com myself.

---

### Post by CharlesA on 2010-01-04
Yup. Pretty much all you need to do is forward the SSH port and get DynDNS up if you have a dynamic IP.

Don't forget to add yerself to the whitelist if using DenyHosts or Fail2Ban.

---

