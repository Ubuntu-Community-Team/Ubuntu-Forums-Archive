---
title: "Block Service from network"
date: 2010-04-17
forum: Networking &amp; Wireless
---

### Post by themagicmanfromtrent on 2010-04-17
I have a service on a jaunty server which I want to keep running night and day, but which I want to disallow access to the internet (and not the network) at certain times during the day. How can I achieve this without killing the service?

---

### Post by Iowan on 2010-04-17
A **cron** job and **iptable** rules sounds like an option, but I don't have the necessary code for you :(
My DSL modem/router has options to set time limits.

---

