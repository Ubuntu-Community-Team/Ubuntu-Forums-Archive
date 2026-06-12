---
title: "Static nat on ubantu.. possible?"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by amit888 on 2009-08-20
Hello Experts
 
I am new bee for ubantu and I am more likely networking and security guy so having question related to that field for ubantu..
 
Is it possible to configure STATIC nat in ubantu 9.0?
 
What all steps I need to do? how ?
 
Could you pls help me?

---

### Post by Iowan on 2009-08-21
Static address? There's an option for a manual configuration under Network Manager. It's also possible to set up a static address under */etc/network/interfaces*. Finally, you can (probably) set up a static *lease* (based on MAC address) in your DHCP server.

---

### Post by amit888 on 2009-08-21
thanks for the info. info can be usefull but not enough buddy...:(
 
I could not find any such think called network manager.
 
IF I should configure /etc/network/interface than what would be the syntax?

---

### Post by Iowan on 2009-08-22
A couple of methods for setting up static address - both are for earlier versions - but the procedure is the same:
[via Network Manager]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html")
[via /etc/network/interfaces]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html")

---

### Post by amit888 on 2009-08-24
well both the documents describes how to configure static ip address on ubantu... whereas i m looking for static nat.... ip to ip natting.. 1 to 1 natting.....:(

---

