---
title: "Cant Access Server On Internal Network"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by aiharak on 2009-09-04
I currently have a server setup behind a router on my home network. When I try to connect to it from my laptop using the server's external address, I'm taken to my router's configuration menu. When I try the server's internal address, I time out. I've had several people connect successfully from outside of my network. What should I do so that I can access my server internally?

---

### Post by superprash2003 on 2009-09-04
are you able to ping the server's internal address? is the server running ubuntu server or the desktop version?

---

### Post by jonobr on 2009-09-04
Im a bit confued about the connection you noted by other people,
however, it sounds as if your not (and need to) forwarding ports on your router to your internal IP,

So for example, if you setup a server as a web server, and it was 192.168.1.10
You would need an entry to your router that said, anything hitting 
the router on port 80 forward to 192.168.1.10

Im also assuming that this works on the internal network using the direct IP.
Lastly, having the config of your router available for remote management on the Internet is probably a bad idea, 

This could invite attempts to hack your network.

---

### Post by aiharak on 2009-09-04
I'm running ubuntu server 9.04 with apache installed and running. I fail to ping the server's internal IP from my laptop. I'm pretty sure the router is configured properly. (My friends can access the server from its external ip address)

I just noticed that I can access the server from a computer directly connected to the network using its internal address. Looks like its just my laptop that can't connect to it. How would I fix this problem?

---

### Post by wojox on 2009-09-04
You can't ping from either address?
Internal 192.168.1.101?
External address from which your friends are connecting.

---

### Post by Iowan on 2009-09-04
How is your laptop connected? (wired/wireless?)

---

### Post by aiharak on 2009-09-04
I'm connected via wireless to my router. The external IP goes to the router config page, the internal IP times out. The server is connected to the router directly.

Also, I'm pretty sure I will be able to access the server if I get a wired connection with my laptop but I want to avoid this if possible.

---

### Post by superprash2003 on 2009-09-16
when connected via wireless its within the same LAN right? in that case you should be trying ONLY with internal and not external ip.. do you run firestarter, ufw or anything similar?

---

### Post by ChumleyEX on 2009-09-16
Does the notebook have a antivirus/firewall? Normally that is the problem, if it's a windows machine.

---

### Post by badger_fruit on 2009-09-16
Please post the IP addresses of:-
- laptop Wifi connection
- laptop wired connection
- apache connection

Please also try a wired connection to your router and see if problem persists.

---

