---
title: "Freeradius server 2.1.0 Installation help"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by sai438 on 2009-02-26
Hi,
   I installed a freeradius server using apt-get install freeradius. Now when i'm trying to start the server it is saying ok but its not starting. I checked for logs in /var/log/freeradius/radius.log but its empty. I don't know how to proceed. All the documentation is talking about normal Linux based (redhat/suse,etc). please help me out in setting up radius server.

Thanks in advance,
sairam

---

### Post by sai438 on 2009-02-26
Now i installed freeradius-mysql, and tried 'freeradius -X', its working fine. but when i tried to start the service /etc/init.d/freeradius start its not working. i don't have mysql-server.

---

### Post by sai438 on 2009-02-26
when i was searching the logs, its saying /var/run/radiusd server doesnot exists. After creating that directory and tried to start the radius server, then it started.

---

### Post by shazbut on 2009-03-26
Thanks, your thread pointed me in the right direction to solving the issue I was having: freeradius not loading at boot.  I found the complete answer to why freeradius was failing to start here: [http://www.howtoforge.com/forums/showthread.php?t=29325]("http://www.howtoforge.com/forums/showthread.php?t=29325")

To fix it I had to edit /etc/freeradius/radiusd.conf
and change
```
run_dir = ${localstatedir}/run/radiusd
```
to
```
run_dir = ${localstatedir}/run/freeradius
```
and also
```
pidfile = ${run_dir}/radiusd.pid
```
to
```
pidfile = ${run_dir}/freeradius.pid
```
Now freeradius should start at boot (and restart) properly.

---

### Post by sai438 on 2009-03-30
Good Update, i forgot to update this post. I did the same thing what you did. This is really a useful information.

---

