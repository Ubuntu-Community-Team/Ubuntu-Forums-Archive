---
title: "Load Balancing Multiple Servers"
date: 2010-07-11
forum: Networking &amp; Wireless
---

### Post by StolerTech on 2010-07-11
I have looked into crossroads and it seems like the perfect solution to load balancing my future web servers. The only thing I am thinking about now is how do I keep all the files and MySQL in perfect sync 100% of the time on all the servers?

---

### Post by tgalati4 on 2010-07-12
You could set up your database on a network attached storage, or simply put the database on a "Master" server and then use remote mounts for the "Slave" servers so that all instances of mysld are reading/writing to the same database.  I'm not sure how well mysql can handle this.  The "Master" machine will handle file locking and I/O, but the performance hit for the "Slaves" for SQL queries may be unacceptable.  It depends on your workload and what else you are serving (such as HTML, PHP, and AJAX).

The alternative method is to use rsync between the machines to keep the databases syncronized.  How often you perform rsync and how much inter-server traffic it generates and its impact on serving SQL queries can only be discovered through testing.

The rsync method will give you some redundancy (which is good) by having copies of the database on each server.  But, if you have a 500 MB database file that needs to be rewritten every 30 seconds to each machine, then you could run into I/O or network traffic problems.

The simpler solution is to get a faster machine (with more cores) or stick in another blade to deal with the workload.

---

