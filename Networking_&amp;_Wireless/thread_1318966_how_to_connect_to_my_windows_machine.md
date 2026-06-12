---
title: "how to connect to my windows machine"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by stvdel on 2009-11-08
I am currently using Ubuntu 9.10 and I would like to set up everything to be able to remote control my Windows 7 machine. Could someone explain the process, settings and programs to use on both machines. Thanks for the help.

---

### Post by squenson on 2009-11-08
Personally, I use [RealVNC]("http://www.realvnc.com") on Windows XP. Once the server module is installed, I can access the desktop of my machine with the remote desktop program located in the Internet menu. You may need to configure your firewall and if your Windows 7 machine is not behind a router (it's IP address is not 192.168.x.y) then I suggest that you put a password on RealVNC to prevent any unauthorized access.

---

### Post by stvdel on 2009-11-08
Ok, thanks for that information. If I wanted to use the Terminal server client and the windows computer is behind a router, what ip address would I enter to connect to it?

---

### Post by squenson on 2009-11-08
If both machines are on the same side of the router (e.g. both have IP like 192.168.x.y) then it is no problem. If you want from the external world to access your machine, then you need to use a tool like [LogMeIn]("http://en.wikipedia.org/wiki/Hamachi") which will allocate additional IP addresses that are directly accessible.

---

### Post by stvdel on 2009-11-08
I am sorry, I don't really understand. My Ubuntu box is behind a router in one place and I want to access my Windows box and control it and that is behind a router in another place. I don't know what is the best program to use. What should I use on my linux box and what should I use on my windows box? How to set them up? Does anyone know of any good tutorials or can explain it to me.

---

### Post by squenson on 2009-11-08
In such case, you need a tool to create a virtual network, so both machines can see their IPs. LogMeIn does exactly that. Once you have both machines with visible IP addresses, then use RealVNC to connect to the desktop of the other one.

---

### Post by stvdel on 2009-11-09
Ok I will try that, thank you.

---

