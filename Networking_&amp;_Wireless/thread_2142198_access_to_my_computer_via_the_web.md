---
title: "access to my computer via the web"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by Pedroski55 on 2013-05-04
Hi, I have used apache2 to turn my laptop into a server. I can call up my webpage in Firefox. My page works fine.

My machine has at the moment ip 192.168.1.4 but my (WAN) ip is 114.XXX.XXX.145 (blanked out the correct no.) 

When I try to access my computer from another computer, I arrive at my router, which requests username and password. I get the page I would get if I entered 192.168.1.1 However, I don't want to access the router, I want get through it to my computer, to my webpage.

What do I have to do??

---

### Post by sanderj on 2013-05-05
Does it work if you access your server from *Internet* using hte public IP address?

---

### Post by Pedroski55 on 2013-05-05
What would that be? How many ips do I have??

---

### Post by sanderj on 2013-05-05
> **Pedroski55 said:**
> What would that be? How many ips do I have??

Your "WAN" IP address

---

### Post by Pedroski55 on 2013-05-05
That's what I used
Apparently I need 'port forwarding', but I have no idea how to enable that, or where.

---

### Post by sanderj on 2013-05-05
> **Pedroski55 said:**
> That's what I used
Apparently I need 'port forwarding', but I have no idea how to enable that, or where.

It's not a Ubuntu question; you have to set it up in your router/modem/NAT-device. Consult [http://portforward.com/](http://portforward.com/) or your routers/modem manual

HTH

---

### Post by Pedroski55 on 2013-05-05
On my router is a useradmin password, so I can call 192.168.1.1 and enter useradmin and the password. Then I am 'inside'  the router. But this is not the full access that the Chinatelecom technician has. This huawei HG8245 router has another user 'telecomadmin' and another password. I do not know that password, so I can't get at anything to change it. The password is not the default admintelecom as it says on the portforward.com webpage.

So I am stuck!

---

### Post by lisati on 2013-05-05
> **Pedroski55 said:**
> On my router is a useradmin password, so I can call 192.168.1.1 and enter useradmin and the password. Then I am 'inside'  the router. But this is not the full access that the Chinatelecom technician has. This huawei HG8245 router has another user 'telecomadmin' and another password. I do not know that password, so I can't get at anything to change it. The password is not the default admintelecom as it says on the portforward.com webpage.

So I am stuck!

According to [http://portforward.com/english/routers/port_forwarding/Huawei/HG8245/defaultguide.htm](http://portforward.com/english/routers/port_forwarding/Huawei/HG8245/defaultguide.htm) the default user name is telecomadmin, which has a default password of admintelecom

---

### Post by Pedroski55 on 2013-05-05
Got the telecomadmin password from the technician, but: The page where  one might set port forwarding does not exist on my router. I will buy a  new router, and see if that works.

---

