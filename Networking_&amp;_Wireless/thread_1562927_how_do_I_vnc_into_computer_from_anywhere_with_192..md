---
title: "how do I vnc into computer from anywhere with 192."
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by coolman98 on 2010-08-28
how do I vnc into computer from anywhere with a 192.168.1.106 in ubuntu.
thanks in advance

---

### Post by BkkBonanza on 2010-08-28
If by "anywhere" you mean from the internet, and you have a router between the net and your ubuntu system, then, you need to forward port 5900 on your router to your ubuntu system (192.168.1.106). Then you can use your public IP not your 192.168.1.106 one to get there.

Make sure VNC is set with a strong password first as once you open the router anyone can get to your VNC port, and will likely try sometime.

---

### Post by coolman98 on 2010-08-28
huh? im nube with networking.

---

### Post by BkkBonanza on 2010-08-28
If above sounds like what you need, then read up router manual or google for "make/model# port forwarding" to find out how to "forward a port" on your router.

Otherwise more detail on what you want to do is needed.

---

### Post by coolman98 on 2010-08-28
is that what I have to do could I just get a static ip that is public

---

### Post by coolman98 on 2010-08-28
hmmmmmmm.

---

### Post by BkkBonanza on 2010-08-28
No. Static or dynamic IP doesn't matter. 

I'm assuming you have a typical home router setup but you haven't really indicated anything about how you connect to the internet. 

Your router gets assigned an IP from your service provider. Your router also assigns private IPs to computers on your network. That is what the 192.168.* addresses are. These private IPs are not routeable on the internet - every other local network also has private addresses so the internet could never know where to send data.

Your router translates the connections from the itnernet to it's public IP to your local network addresses. This is called NAT (Network Address Translation). When you send a connection out it remembers where it came from and know where to send data back to. But when a connection arrives from the internet it doesn't know where to send it.

To get to your local computer your router needs to know where to send the VNC connection request it gets. This is called "Port Forwarding". Most applications have a default port they listen for connections on. VNC happens to be port 5900. When you start VNC as a server on your computer it listens on port 5900. But your router gets connection requests on it's port 5900 and they don't get to your computer. By forwarding the port you direct those public requests to your computer where VNC gets them.

Hence, to get access to VNC from the internet you need to "port forward 5900 to your local computer ip 192.168.1.106". There is guides online about how to do this for each router make/model. Which is where google comes in.

---

