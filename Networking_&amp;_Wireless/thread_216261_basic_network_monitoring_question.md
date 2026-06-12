---
title: "basic network monitoring question"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by verbatim210 on 2006-07-15
2 questions based on **ifconfig **and **uptime **command

1. how do u reset the values in ifconfig? eg. RX bytes:121515507 > RX bytes:0
2. what does 21:49:07 up 6 days,  **1:12**,  1 user,  load average: **0.00, 0.00, 0.00** mean?

---

### Post by MrHorus on 2006-07-15
> **verbatim210 said:**
> 2 questions based on **ifconfig **and **uptime **command

1. how do u reset the values in ifconfig? eg. RX bytes:121515507 > RX bytes:0[/code]

As far as I know this can't be reset manually although I am sure someone more knowledgeable than me will know an easy way of doing so.

[quote]2. what does 21:49:07 up 6 days,  **1:12**,  1 user,  load average: **0.00, 0.00, 0.00** mean?

It means the current time is 21:49, your computer has been up continually for 6 days, 1 hour and 12 minutes, you have one user logged on and your load averages (CPU load) for the last 5, 10 and 15 minutes are zero.

---

### Post by verbatim210 on 2006-07-15
thanks MrHorus the cpu load is very useful information.  instead of 1,5,15 minutes they should have made it 1 hour, 12 hours, 1 week so you know the average weight your sever is carrying.

if anyone know how to set the ifconfig meter, be very helpful!

---

### Post by verbatim210 on 2006-08-03
does anyone know how to reset the **TX/RX **values in ifconfig?

---

### Post by phitoo on 2006-08-04
> **verbatim210 said:**
> does anyone know how to reset the **TX/RX **values in ifconfig?

Try ethtool. (apt-get install ethtool). It probably has an option for that.

---

### Post by stormblue on 2006-08-04
When I run the uptime command it says there are two users.  How can I check what these two users are?

---

### Post by phitoo on 2006-08-04
> **stormblue said:**
> When I run the uptime command it says there are two users.  How can I check what these two users are?

users

or

w 

w gives both uptime and users.

---

### Post by stormblue on 2006-08-04
Thanks.  Here's my output.  Anything weird about it?

```
 14:33:12 up 2 days,  3:45,  2 users,  load average: 0.39, 0.53, 0.64
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
bluestor :0       -                Wed10   ?xdm?  38:40m  2.82s /usr/bin/gnome-
bluestor pts/0    :0.0             14:15    0.00s  0.28s  0.01s w
```

---

### Post by phitoo on 2006-08-04
> **stormblue said:**
> Thanks.  Here's my output.  Anything weird about it?

```
 14:33:12 up 2 days,  3:45,  2 users,  load average: 0.39, 0.53, 0.64
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
bluestor :0       -                Wed10   ?xdm?  38:40m  2.82s /usr/bin/gnome-
bluestor pts/0    :0.0             14:15    0.00s  0.28s  0.01s w
```

Hmmm! What am I looking for?

bluestor is logged in once at the console via the GNOME display manager and a second time from some remote computer/process. At least that's what it looks like to me.

---

### Post by stormblue on 2006-08-04
There shouldn't be any remote users.

---

