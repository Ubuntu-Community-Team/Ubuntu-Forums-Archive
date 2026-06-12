---
title: "Network failover in Ubuntu Server 9.04"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by Jago6060 on 2009-08-03
My goal here is to have two nic cards, both active with cables plugged in so in the event that one network goes down, I still have access to the other network and the internet.  The reason for this is we're currently doing some network restructuring and either network is prone to go down for maintenance.

So my first question, is this possible to do without causing conflicts in the computer?
Second, how do I go about doing this?  Can I just add another entry in the interfaces file and be good to go?  Also, does anything need to be done in the resolv.conf file?  I.e. nic1 use dnsA and nic2 use dnsB?

---

### Post by Jago6060 on 2009-08-04
~Bump~

---

### Post by superprash2003 on 2009-08-04
it should work plug and play. when one goes down ( network unplugged) , then its pretty obv that the other one would work..

---

### Post by Jago6060 on 2009-08-04
So I don't really need another interfaces entry correct?  That one entry will work for either nic?

---

### Post by superprash2003 on 2009-08-05
you mean static ips? you would have to configure static ips on both interfaces

---

### Post by Jago6060 on 2009-08-05
> **superprash2003 said:**
> you mean static ips? you would have to configure static ips on both interfaces


I should probably elaborate one step further.  I don't know if its possible, but I'd like to be connected to both networks at the same time, as each network has programs and data that I use.  So I'm looking for a solution to prevent me from switching my cable all the time.

---

### Post by superprash2003 on 2009-08-06
you mean certain programs use one NIC and other programs use the other NIC?

---

### Post by Jago6060 on 2009-08-06
> **superprash2003 said:**
> you mean certain programs use one NIC and other programs use the other NIC?


Yeah, sort of.

ServerA(hosts)--->Project Managment Site
ServerB(hosts)--->Monitoring and Client Project Management Site

So with only one connection in my computer, I can only access one server(I didn't set up the network :-P).  I'd like to be able to access both servers so I can get to all active programs on both servers.

---

### Post by superprash2003 on 2009-08-07
yea , that is possible.. just configure one nice to connect to server A and the other noc to connect to server B . you do this by assigning static ips to each interface and this depends on the ips of the servers

---

### Post by Jago6060 on 2009-08-07
Do I need to define a MAC in the interfaces entries?  I was just wondering because if you have two active nics, both with cables in, how will traffic know which card to go through?  Or is the traffic direction something that just kind of happens?

---

### Post by superprash2003 on 2009-08-08
you dont need to define a MAC address.. you could use the route command for this . [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

