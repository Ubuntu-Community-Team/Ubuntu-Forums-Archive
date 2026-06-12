---
title: "Changed IP of backend, now cannot get anything to connect?"
date: 2013-08-22
forum: Mythbuntu
---

### Post by drifting on 2013-08-22
I am in a mess, and very confused as to what is going on.

Let me explain. This Myth server has run fine for years, in fact it belongs to my Gran would you believe. It was .22 and an earlier version of Ubuntu. So finally I had time to upgrade it all. Now before the upgrade I changed the IP of the server from 192.168.2.2 to 10.0.0.36 so that I could be lazy and do the upgrades via a desktop machine. Anyway, all the upgrade to Ubuntu 12.04 LTS went without a hitch. Went ahead and upgraded Myth to .25 checked all was happy after it did the upgrade to the database. Then did the upgrade to .26, so far so good. All working fine after a tuner rescan.

Just about to take the server back after setting the IP back to where it was 192.168.2.2 and lo and behold myth frontend (on the server backend) says it cannot find the IP? Neither can Mythweb (It actually reports 10.0.0.36?) I have of course ran the myth backend setup, and have all the correct address in both boxes.

I have also checked the /etc/my.cnf and changed the localhost entry to the dedicated servers address. Mysql seems to be running fine?

Any ideas, I am lost now.

Paul.

---

### Post by drifting on 2013-08-24
Bump, anyone ? I need to try and get this done before I have to go, suggestions even ?

---

### Post by drifting on 2013-08-26
Given up, wiped the machine and started again.

Now see other post about tuners not working in the latest Myth / Mythbuntu 

Sigh...

---

