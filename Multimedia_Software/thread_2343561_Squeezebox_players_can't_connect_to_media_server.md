---
title: "Squeezebox players can't connect to media server"
date: 2016-11-17
forum: Multimedia Software
---

### Post by FarNorthRod on 2016-11-17
I recently carried out a clean install of 16.04LTS and installed Logitech Media Server. My players (Squeezebox Touch & a Squeezebox Radio) will no longer connect to the server. From what I can gather online it seems likely to be a firewall issue but that is a dark art as far as I'm concerned.

The players connect to the network (I can see them connected on my hub admin page) but they do not connect to my 'home-desktop' where the LMS is installed and running.

Any help would be gratefully received.

---

### Post by bernard2 on 2016-11-19
At the risk of asking the obvious, are you sure the server is running properly? Connect your browser to localhost:9000 to check...

---

### Post by FarNorthRod on 2016-11-21
> **bernard2 said:**
> At the risk of asking the obvious, are you sure the server is running properly? Connect your browser to localhost:9000 to check...

Thanks and yes it is running my browser loads it and I can see my scanned music etc, it seems to be a problem with the payers connecting so maybe a network problem? I may attempt to connect them with firewalls disabled and see if that works. Thanks for your reply.

---

### Post by bernard2 on 2016-11-21
I have several assorted squeezeboxes (almost one of every type they made!) and what they mostly have in common is fragility of WiFi ... so, if you haven't already, try them with a wired connection to eliminate WiFi as an issue.

After that, yes it could be a firewall issue - I can't now recall the ports that the slim protocol uses but I'm sure they're out there somewhere...

---

### Post by FarNorthRod on 2016-11-22
Thanks again bernard2, yes I'm going to try hard wiring them to see if they work then. In the meantime I have read vague suggestions that the BT Hub5 could be the problem but it all seems very confused.

---

### Post by FarNorthRod on 2016-12-09
Just an update, hardwiring into the hub presents the same problem. Player connects to network but then cant connect to host-name computer where LMS is running. At a loss now.

---

### Post by FarNorthRod on 2016-12-11
Simple after all, allowing appropriate ports in firewall solved the problem, thanks to all.

---

