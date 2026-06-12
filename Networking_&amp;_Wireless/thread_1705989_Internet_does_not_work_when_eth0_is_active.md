---
title: "Internet does not work when eth0 is active"
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by thing2b on 2011-03-13
I am running the latest ubuntu and I am having trouble getting networking sorted. I have 2 networks, one wired (eth0) and one wireless (wlan0). I connect to the internet using wireless. 

The problem is that I can only successfully connect to the internet if I disconnect from eth0. I have hit this problem with Windows machines and the solution was to adjust the "interface metric" in "Advanced TCP/IP Settings" so that the wireless was the preferred connection.

How can I achieve something similar in Ubuntu?

---

### Post by thing2b on 2011-03-13
Well I solved it myself, even though I have spend quite some time on it. In Network Connections, I edited "auto eth0" and under IPv4 - Routes, there was a tick box "use this connection only for resources on its network".

---

