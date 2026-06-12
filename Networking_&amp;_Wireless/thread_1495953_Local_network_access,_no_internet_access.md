---
title: "Local network access, no internet access"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by carsonrose on 2010-05-28
I dont know whats going on, but I cant access the internet all of a sudden. I can, however, access the local network. I can view anything inside the network, but cant go to [www.google.com](www.google.com), it wont connect. 

When I mouse over the connection icon in the sys tray, it says "unmanaged". Its has been going up and down for a couple days now, (my connection to the internet), however everyone else on the network is fine. 

:confused::confused:   Any ideas?   :confused::confused:

-Doug

---

### Post by dineshs on 2010-05-29
what do you get for
```
ifconfig -a
```
```
ping 4.2.2.1
```

---

### Post by Iowan on 2010-05-29
Although it's more likely DNS than routing, you can verify that **route -n** shows the proper gateway.

---

### Post by Iowan on 2010-06-04
Extra posts moved to separate thread [here]("http://ubuntuforums.org/showthread.php?t=1501495").  Linked for common information.

---

### Post by carsonrose on 2010-07-05
It was a gateway issue...... Thanks!

:p

---

### Post by Iowan on 2010-07-05
Glad you got it fixed. 
[Here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") is how to mark the thread [SOLVED]. :)

---

### Post by carsonrose on 2010-07-14
> **Iowan said:**
> Glad you got it fixed. 
[Here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") is how to mark the thread [SOLVED]. :)

Thanks !

---

