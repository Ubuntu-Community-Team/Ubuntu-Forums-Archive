---
title: "[SOLVED] I broke my internet setting up ICS =["
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by willc0de4food on 2009-01-10
so yea, as the title says..was following a tutorial for setting up ICS and it didn't work. so i tried undoing what i did but i didn't have the internet for the tutorial so that i could see all of the steps i needed to undo and now my net just doesn't work =[ any ideas for getting it back up & running?
thanks

---

### Post by HunterThomson on 2009-01-10
> **willc0de4food said:**
> so yea, as the title says..was following a tutorial for setting up ICS and it didn't work. so i tried undoing what i did but i didn't have the internet for the tutorial so that i could see all of the steps i needed to undo and now my net just doesn't work =[ any ideas for getting it back up & running?
thanks

I glanced over this "How To"

[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html#more-182](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html#more-182)

It seems all you need to do is delet all your iptables rules.

```
IPTABLES -F
IPTABLES -t nat -F
IPTABLES -t mangle -F
IPTABLES -X
```

then 
```

sudo apt-get remove dnsmasq ipmasq
```

then remove this line 

```
net.ipv4.ip_forward = 1&#8243; to /etc/sysctl.conf
```

From

```
/etc/sysctl.conf
```

then you have to set up your network interface agin

..... One sec on that one.

---

### Post by HunterThomson on 2009-01-10
just a guess on how to undo this comand

```
ifconfig ethx 192.1xxx.xx.xx
```

```
sudo ifconfig ethx dhcp
```

Just to make it clear "ethx" is the interface name of the interface you changed.

.... Ya that command should do the trick it is not in the man pages though. i mite be wrong about the command to delete all your iptables rules but just Google "how to delete all iptables rules"

---

### Post by willc0de4food on 2009-01-11
thanks for the reply
i'll give that a try & post back on how it goes.

---

### Post by willc0de4food on 2009-01-12
yessssssssssssss :DDDDDDDD that did it !
thank you SO much. ^_^
i will no longer be forced to endure the disgusting beast a.k.a. winblows

---

### Post by superprash2003 on 2009-01-12
please mark this thread as SOLVED under thread tools

---

