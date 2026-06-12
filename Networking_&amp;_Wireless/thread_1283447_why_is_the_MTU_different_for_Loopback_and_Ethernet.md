---
title: "why is the MTU different for Loopback and Ethernet?"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by eival on 2009-10-05
i noticed theres 2 different MTU settings in the Network Tools

the Loopback has 16436 MTU, where as Ethernet is set to 1500

i tried to configure the Ethernet settings but it says 

"The Interface Doesnt Exist"

so my question is, is there a way to change the Ethernet MTU to match the Loopback? if so, how do i get to it

---

### Post by chili555 on 2009-10-05
There sure is such a tool, but then your internet connection probably won't work. MTU of 1500 is the standard for ethernet V2. Please see: [http://en.wikipedia.org/wiki/MTU_(networking](http://en.wikipedia.org/wiki/MTU_(networking))

In case you want to prove it to yourself, please do:```
sudo ifconfig eth0 mtu 98742
```...or whatever number you like. Now can you surf the web, send email, IM, etc. without problems? 

Loopback does not use ethernet, so it can use a higher MTU.

---

