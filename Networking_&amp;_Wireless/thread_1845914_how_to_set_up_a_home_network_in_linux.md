---
title: "how to set up a home network in linux"
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by Metul Burr on 2011-09-18
How can i set up a home network with all PC's have linux. I want a laptop to have access to my main computer to watch movies off of it

---

### Post by nothingspecial on 2011-09-18
Hi,

Install openssh-server on your computer.

```
sudo apt-get install openssh-server
```

Right click the network icon, choose "connection information" and make a note of the computers ip address.

Back at your laptop open the file browser and in the menu choose File > Connect to server.

In the top box choose ssh, then fill in the rest and click connect.

---

