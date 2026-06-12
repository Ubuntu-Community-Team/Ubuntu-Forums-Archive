---
title: "attach 2 routers together"
date: 2011-12-19
forum: Networking &amp; Wireless
---

### Post by giuseppe105 on 2011-12-19
Hello everyone I have two routers. I have Internet coming in from the wall. Right now i have the second router taking internet from the first router as a wan. So this means that any device connected to router two cant ping any device from router one. I would like to solve this problem with an existing Ubuntu samba server i have running. I have three lan cards installed in the server already. 

I would like to have the internet go into eth0 and i would like to put it though both routers. I would then like to route packets from both router one and router two so that both routers can communicate with each other.

The idea above seems complicated could i make it simpler by having router one control the internet and have Linux route the packets between router one and router two?

If you had any information as to where to start it would be greatly appreciated.

Thank you.

---

### Post by Kralizec on 2011-12-19
So, the setup you want is one like in the picture I've attached, correct?

If this is the case, set up eth0 (or whatever interface on the routing computer receives the internet connection) to connect correctly.
Set up eth1 (or whatever connects to router 1) to be a static IP; something like 10.10.10.1. On router 1, there should be a way to set the WAN IP to a static IP; set this to 10.10.10.2.
Set up eth2 (whatever connects to router 2) to be a static IP; something like 10.10.20.2. On router 2, set the WAN IP to 10.10.20.2.

Next, you'll need to change the starting distribution point for the DHCP server on the routers to be different. Initially they probably both operate on the 192.168.1.x network; you'll have to make router 2 operate on the 192.168.2.x network (or something similar).

Once you've done that, you'll need to set up static routes on the routing computer in the middle. Assuming the IP scheme I laid out, route traffic to the 192.168.1.x network through the 10.10.10.1 interface, traffic to the 192.168.2.x network through 10.10.10.2 interface, and the default gateway to be eth0.

If you need help/clarification with any of these steps, let me know.

---

### Post by ddarsow on 2011-12-19
If all you want to do is utilize both routers for more ethernet ports, it is even easier.

Just set the both as dchp, feed router 2 from router 1, and make sure the starting ip is different on both: such as 192.168.1.1 & 192.168.2.1

---

### Post by giuseppe105 on 2011-12-19
ddarsow right now i have the network setup the way you mentioned. But it doesn't allow computers on 192.168.1.1 to see any computer from 192.168.2.1 and vice versa.

thank you Kralizec. This information iv helpful but what i need help with is what commands to do i use to accomplish this task? iv only every used /etc/network/interfaces to setup my internet connection.

---

### Post by Kralizec on 2011-12-19
You can set the interface IPs to static in /etc/network/interfaces. This might help: [http://codesnippets.joyent.com/posts/show/319]("http://codesnippets.joyent.com/posts/show/319")

I don't know the routers you're using so I can't help you set up the IPs there (I have to assume that you either know or can figure those out).

This article will tell you how to set up the routing (which is also done in /etc/network/interfaces): [http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html]("http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html")

Let me know if you need anything else.

---

### Post by giuseppe105 on 2011-12-19
Ahh this looks exactly like what i need. It has a similar syntax to the windows route command. Thank you

---

### Post by Kralizec on 2011-12-19
Yeah, it's almost the same. Keep in mind though, that if you want the settings to be consistent over restarts you'll need to add the requisite lines to the interfaces file. The route command will only last until next reboot.

---

