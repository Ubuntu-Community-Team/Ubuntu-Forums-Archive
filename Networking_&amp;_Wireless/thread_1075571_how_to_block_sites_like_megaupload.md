---
title: "how to block sites like megaupload"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by shan23 on 2009-02-20
Hi,

I'm the admin in my hostel's computer lab. The problem is, some folks use the lab machines to download big files ( 100 mb and above ) almost all the time , thereby using up almost all the bandwidth allocated to the hostel. I want to ensure that people can't open certain sites like megaupload from the lab...Is there any way to do that ? 

The machines all have Hardy installed...i googled the problem, only to find solutions to block certain particular ips/sites...but i want to block a generic class of sites, say all links containing the word "megaupload". If someone has any idea, pls help...

---

### Post by superprash2003 on 2009-02-20
well that would be tough to find.. you could start blocking site by site..monitor the traffic and find out where people are downloading from!!

---

### Post by shan23 on 2009-02-20
> **superprash2003 said:**
> well that would be tough to find.. you could start blocking site by site..monitor the traffic and find out where people are downloading from!!
Thats actually not a very bad idea....but the thing is, i would prefer a solution that would not involve me editing the blacklisted sites on a daily basis... :) If there could be a solution in which i could add a line in the iptables instructing it to drop all connections containing a specific word ( or regular expression !!) in the link , that would be ideal !!!

---

### Post by karthick87 on 2009-08-18
Use squid proxy server,it will do it..

---

