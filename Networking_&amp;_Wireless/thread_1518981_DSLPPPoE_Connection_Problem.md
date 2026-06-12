---
title: "DSL/PPPoE Connection Problem"
date: 2010-06-27
forum: Networking &amp; Wireless
---

### Post by life015 on 2010-06-27
[SIZE=4]i installed Ubuntu 10.04 in my Asus F80L laptop through Wubi installer. I am Facing connection problem which is DSL/PPPoE.i am using that connection in windows7.i tried with Network manager & terminal-[SIZE=2]sudo pppoeconf[/SIZE][/SIZE] .[SIZE=4]but still i have not got any connection.it always shows [COLOR=Red]connection disabled-you are offline[/COLOR][/SIZE].[SIZE=4] please help me to use internet in my ubuntu.[/SIZE]

---

### Post by dineshs on 2010-06-28
pl refer this
[http://ubuntuforums.org/showthread.php?t=1512925](http://ubuntuforums.org/showthread.php?t=1512925)
If you are using NM and need DSL/PPPoE connection,pl read post #5 of 
[http://ubuntuforums.org/showthread.php?t=1518748](http://ubuntuforums.org/showthread.php?t=1518748)

---

### Post by life015 on 2010-06-29
Thx for the reply. but i have not get internet (dsl connection) fix in my laptop yet. i used both network manager and pppoeconf. but no luck yet. please any1 have the solution>?

---

### Post by dineshs on 2010-06-29
what do you get for
```
ifconfig -a
```
and
```
sudo lshw -C network
```

---

