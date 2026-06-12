---
title: "VPN Question"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by josmcc on 2010-09-10
Hi, I have a pptp vpn server running from my home. I have a 1 client computer connected to it from hospital. I can view webcam running on their computer from the server. Can another client connect to the vpn server and also access the webcam on the other client. Just like a home network or can the clients only access services/shares on the server?. It's just a webcamxp server listening on the laptop (client 1 at :8080). Want to be able to connect from another client and still view the webcam but doesnt seem to be working very well. Firewall on the server is set up to allow INPUT GRE, etc. I don't know if I need masquerading or what? I'm not iptalbes expert or is this just a limitation in VPN software.

---

### Post by coutts99 on 2010-09-10
Expand on 'doesn't seem to work very well' please. Does it work at all?

---

### Post by josmcc on 2010-09-10
It will let me connect, maybe for a couple of seconds then timeout like its a firewall issue or something

---

### Post by coutts99 on 2010-09-10
Anything in your firewall logs?

---

### Post by josmcc on 2010-09-10
i got a few dropped broadcast netbios packets but thats it (from client to client).

---

