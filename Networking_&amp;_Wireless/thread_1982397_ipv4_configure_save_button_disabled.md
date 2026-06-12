---
title: "ipv4 configure save button disabled"
date: 2012-05-18
forum: Networking &amp; Wireless
---

### Post by holiday on 2012-05-18
Trying to set up static ip but the save button will not enable. I see no option to start the network app as root. 

One hope is that I can start it from console with sudo but I do not know the command. 

$ sudo network-manager tells me that the command is not find but then

$ sudo apt-get install network-manager tells me that network-manager is already the latest!

A bit baffled here. Thinking of rolling back to 10.04

---

### Post by praseodym on 2012-05-18
Try
> gksu nm-connection-editor

---

### Post by holiday on 2012-05-18
Thanks praseodym, but no joy.

I've tried Mint, Classic, Unity, even XUbuntu... Even XUbuntu! XUbuntu now looks like a hacked Mac! And I'm the guy who was so glad when my MacBook Pro burned out.  

It seems like life was easier before people started trying to make it easier for me. 

I'm going back to 10.04 and I'm staying there until these bugs get worked out. 10.04 is great. I love it. I'm very much looking forward to 15.04.

---

