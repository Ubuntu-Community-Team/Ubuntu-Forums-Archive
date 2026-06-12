---
title: "Monitoring Online Time"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by Deluro on 2011-01-03
hey guys,

first of all, this is my first post in ubuntuforums.org. I appreciate all of you guys, you save my butt a hundred times xD

But now I'm stucked. I'm looking for a tool that logs the time a client is online in my network.
Let me put it to you this way... I have a handful clients which are connected on a ubuntu server (dnsmasq,gateway,fileserer, bla bla bla). Now I need a Monitoring Tool which logs the time a client is turned on.

It is not necessary to log the network traffic or other stuff (wouldn't hurt if it does). I just want know how long a pc was turned on in a specific period.

I already checkout Darkstat and some other tools. But none of them logged the time of any local clients :/

The prog schoul be console-based and if possible but not necessary have a webfrontend.

Thx for reading and thx for your advice.

Dear regars, from Germany

---

### Post by PatchesTheCaveman on 2011-01-03
You can probably configure something like NAGIOS to do this.

[http://www.nagios.org/](http://www.nagios.org/)

---

### Post by Deluro on 2011-01-04
Thx for your help. I already looked at nagios, but for my little purpose its a bit oversized.

Any other suggestions?

---

### Post by Deluro on 2011-01-10
Hey everybody,

i've solve the problem by myself. here is the script (quick and dirty)

```

#!/bin/bash
for ((i=100; i<=150; i++));do
ping -q -c1 192.168.1.$i &> /dev/null
if [ "$?" == 0 ]; then
MAC="`/usr/sbin/arp -a 192.168.1.$i | awk '{print $4}'`"
IP=192.168.1.$i
RESULT=`/usr/bin/mysql -uname -ppassword<<SQL 
use dbname 
insert into access (mac,ip,created) values ('$MAC','$IP', NOW() ); 
quit 
SQL`
fi
done

```

---

