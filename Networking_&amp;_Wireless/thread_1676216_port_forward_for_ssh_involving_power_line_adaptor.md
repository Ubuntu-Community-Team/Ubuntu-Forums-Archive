---
title: "port forward for ssh involving power line adaptor"
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by mangoes on 2011-01-26
Hello,

A while ago, with the [help]("http://ubuntuforums.org/archive/index.php/t-722846.html") of other posters here, I set up my ubuntu box so I can ssh it from outside.  

Yesterday I moved the box to another spot in the house and connected it to the modem via [netgear powerline network adaptor]("http://www.netgear.com/products/home/powerline-and-coax/simplesharing/XET1001.aspx").  After that all ssh attempt into my box - from inside and outside my home network - have been denied.

I suspect that the presence of the powerline network adapter throws out the port-forwarding setup.  If anyone can suggest a way forward, even diagnostic tools to try (I'm really blind about them), it would be greatly appreciated.


cheers

---

### Post by gordintoronto on 2011-01-26
The command ifconfig will tell you your IP Address, such as 192.168.1.100

Then you need to look at your router's configuration to see where the port forwarding is to.

---

### Post by mangoes on 2011-02-02
> **gordintoronto said:**
> The command ifconfig will tell you your IP Address, such as 192.168.1.100

Then you need to look at your router's configuration to see where the port forwarding is to.

Thank you. The ifconfig did show the expected ip address (10.1.1.2), which I had made to be static beforehand. 

I checked the modem, and apparently each of the half pair of the netgear powerline adaptors are registered with their own ip addresses i.e. 10.1.1.3 and 10.1.1.8

Does it mean that if I open port 22 in these devices then this port will eventually be forwarded to my box?  (i.e. from 10.1.1.3 to 10.1.1.8 to 10.1.1.2)

---

### Post by gordintoronto on 2011-02-02
I'm sorry, you're going to need to read the manual that came with the devices. However, here's my guess: 10.1.1.3 is used to configure that device, but it doesn't relate to port forwarding. I can't guess what the device might need in the way of configuration, though.

In other words, my guess is that you should tell the router to forward the port to 10.1.1.2.

---

