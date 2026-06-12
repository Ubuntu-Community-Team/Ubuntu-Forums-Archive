---
title: "Bridging and still use DHCP"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by jcb081584 on 2009-05-15
I'm trying to bridge my wireless and my ethernet connection in 9.04 and am running into problems.  I setup the interfaces file for bridging it and it doesn't work.  I also have a problem where I use two different networks daily and would like dhcp to be enabled to discover all the information since it changes between the networks and having to edit the interfaces file would get a bit tedious.  Could anyone tell me how to do this or point to a guide online or another thread that discusses this please?  Thanks in advance.

---

### Post by superprash2003 on 2009-05-15
are you trying to do something like ICS?

---

### Post by jcb081584 on 2009-05-15
By saying ICS I assume you mean Internet Connection Sharing.  I guess it'd be a yes.  I'm trying to get Virt-Manager to use my wireless connection and the only thing I've found online that says how to do it is to bridge the wireless to the ethernet.  Seeing as I only use the ethernet once in a blue moon it doesn't do me much good to have just it working.  Even when I plug it in with the ethernet it still doesn't work though.  I don't know if it's the virtual machine manager or something with my interfaces.  I use two different networks daily so I'd ultimately have dhcp enabled for the bridge though.  Editing the file everytime I change locations is a bit cumbersome and seeing as the only thing I've accomplished that way is to lock up my internet to where I have to revert the interfaces file and reboot my machine.  Any help you can give me would be wonderful.  Thanks in advance.

---

### Post by superprash2003 on 2009-05-16
try this , if ICS is what you want [http://www.prash-babu.com/2009/02/internet-connection-sharing-in-ubuntu.html](http://www.prash-babu.com/2009/02/internet-connection-sharing-in-ubuntu.html)

---

