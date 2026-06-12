---
title: "mobile broadband: DNS resolution failure"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by Nycticorax on 2010-09-13
I've bought a USB mobile broadband modem (UK, 3 network). It works on the Windows side of my machine proving that my account is active etc. Under Ubuntu (Maverick beta) it is almost working, but it seems I have a DNS problem. skype IM works, but "ping www.google.com" is not working, nor are web browsers. However "ping 173.194.36.104" (a google.com IP address) does work.

Anyone able to suggest how to fix this?

Thanks very much,

dan

---

### Post by MaindotC on 2010-09-13
Post the output of /etc/resolv.conf - this is where the ip addresses of your namesevers should reside.  When you connect your device to the mobile broadband service provider, it should request this information via dhcp and store it in /etc/resolv.conf.

---

### Post by Nycticorax on 2010-09-14
OK, I was doing something stupid. There was an entry for a different provider (Orange) already present in network-manager, and I used that. Creating an entry for the correct provider solved the DNS problems.

---

### Post by MaindotC on 2010-09-14
K glad I could do nothing to help you :D  Please mark the thread as solved.

---

