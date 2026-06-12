---
title: "Wireless connects, disconnects, connects...."
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by Docaltmed on 2008-12-12
At random intervals, varying from 2 minutes to 20 minutes, my wireless will disconnect, and request the connection key before reconnecting. This happens with two different wireless networks, both with WEP.

Sometimes, after an hour or two of this, things will settle down and no disconnects will occur for an hour or so.

Signal strength is strong and there is no interference. The hardware is an HP TX2510us using a Broadcom 4322 wireless. This is not a hardware or network problem, as this problem did not exist previously under Vista. There have been no other changes except the migration to Intrepid.

The details are in the attached file. Any help would be greatly appreciated.

---

### Post by iponeverything on 2008-12-12
> **Docaltmed said:**
> At random intervals, varying from 2 minutes to 20 minutes, my wireless will disconnect, and request the connection key before reconnecting. This happens with two different wireless networks, both with WEP.

Sometimes, after an hour or two of this, things will settle down and no disconnects will occur for an hour or so.

Signal strength is strong and there is no interference. The hardware is an HP TX2510us using a Broadcom 4322 wireless. This is not a hardware or network problem, as this problem did not exist previously under Vista. There have been no other changes except the migration to Intrepid.

The details are in the attached file. Any help would be greatly appreciated.

A .doc  That's just wrong. 

What are using to connect with?

---

### Post by Docaltmed on 2008-12-12
Too funny! The forum wouldn't let me upload the file as a .txt, so I renamed it.

Wireless in my tablet is Broadcom 4322, I'm using the Broadcom-supplied drivers as the native drivers don't support the 4322. Routers are Linksys in one location and 2Wire in the other. Both routers are connected to DSL modems.

---

### Post by Docaltmed on 2008-12-12
Too funny. The forum wouldn't let me upload a .txt, I had to rename it.

Broadcom 4322 in the tablet pc, using the Broadcom proprietary driver as the native driver doesn't support the 4322. Routers are Linksys in one location, 2Wire in the other, both are connected to DSL modems.

---

### Post by iponeverything on 2008-12-12
network manager?

---

### Post by Docaltmed on 2008-12-12
> **iponeverything said:**
> network manager?

Yes. The applet doesn't indicate anything untoward, except disconnecting and then reconnecting. I don't know how to connect from the command line, though I'm willing to learn if Network Manager is the culprit.

---

### Post by iponeverything on 2008-12-12
A couple of things to try..

pop on the wicd deb see if it behaves any differently with it.

something else you could do is try locking your wireless router at 8.02.11g.

Next time it happens do:

```
echo messages > /tmp/debug.txt
tail -40 /var/log/messages >> /tmp/debug.txt
echo syslog >> /tmp/debug.txt
tail -40 /var/log/syslog >> /tmp/debug.txt
echo daemon.log >> /tmp/debug.txt
tail -40  /var/log/daemon.log >> /tmp/debug.txt

```

and attach /tmp/debug.txt with your next post.

---

### Post by Docaltmed on 2008-12-13
OK. This is weird. It stopped happening. On both networks. I have done nothing that, in my little mind, would have altered anything. There haven't been any upgrades, either.

Thanks for the help, though, iponeverything (as well as one of the best screen names I've seen). I really appreciated your fast response.

---

