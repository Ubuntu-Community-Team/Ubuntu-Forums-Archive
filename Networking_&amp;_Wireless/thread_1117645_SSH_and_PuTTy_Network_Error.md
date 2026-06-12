---
title: "SSH and PuTTy Network Error"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by joehardflec on 2009-04-06
I have two machines, one is a desktop system running Ubuntu, the other a laptop dual-booting Ubuntu and Windows Vista.

I have set up the desktop system as an ssh server, and the router to forward port 22 to the desktop.

I can ssh in from my laptop when running Ubuntu fine, but when running PuTTY it only works if I use the external IP rather than the local IP address. 
Trying to connect PuTTY to the local IP makes PuTTY crash with a 'Network Error: Connection Refused' dialog. 
Why is this?

---

### Post by kpatz on 2009-04-06
Are you connecting using the desktop machine's IP address or a host name?  If you're using a host name, try the IP.

If the IP works but the host name doesn't, either something is amiss with your DNS or hosts file on your Vista install.  If the IP doesn't work, maybe you have a firewall running in Vista that's blocking the connection.

---

### Post by joehardflec on 2009-04-06
I found I could connect using the external IP, so I've rewritten my post.

Also; trying the hostname I get a host does not exist error instead.

---

### Post by kpatz on 2009-04-06
Do an **ipconfig /all** in Vista and **ifconfig -a** on both Ubuntus and post here.  Also, **cat /etc/resolv.conf** on the laptop's Ubuntu and post here.

---

### Post by joehardflec on 2009-04-06
Never mind; human error strikes again.  When I brought up the ipconfig; I realised I was getting the two local IPs mixed up. Durr. 

Still doesn't explain why the hostname doesn't work, but I can live with that.

Thanks anyway.

---

