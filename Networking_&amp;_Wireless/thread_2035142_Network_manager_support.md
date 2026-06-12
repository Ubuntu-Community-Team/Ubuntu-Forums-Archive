---
title: "Network manager support"
date: 2012-07-30
forum: Networking &amp; Wireless
---

### Post by kavi123 on 2012-07-30
Hi,
       How  to update the network manager in ubuntu 11.04, since that provides the automatic network wireless connection to the specific access point, but if the connection is established through user space program, without the involvement  of the driver, how to tell the network-manager that the connection is ready...


Since even after the connection establishment by the user space application the connection state is 
"wireless network disconnected"

How to change the state from disconnected to connected state using user space application....


Kindly help me in solving this issue...

Thanks

---

### Post by bakegoodz on 2012-07-30
From the information given I could tell you just to wireless applet select the wireless network to connected to it. Or is there more to it? Like scripting a connection?

---

### Post by kavi123 on 2012-07-30
Thanks a lot for your reply...

Yeah i wanted to know how to do scripting a connection.

Since for the case of wireless connection, whenever you click or select the wireless applet , many management frames for association would be exchanged between station and access point...

Instead of driver sending those frames, user program exchanges the frame , and i do not want to make use of application of  selecting  those wireless network from the wireless applet, hence the network manager still will be in the disconnected state, how to  move it to the connected state, or else how should i update the network manager, such that there is a working wireless network connection..


Thanks...

---

