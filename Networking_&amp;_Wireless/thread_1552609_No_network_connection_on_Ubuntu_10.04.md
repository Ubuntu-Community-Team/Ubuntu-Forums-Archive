---
title: "No network connection on Ubuntu 10.04"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by Petter72 on 2010-08-13
Can anyone please tell me how to troubleshoot a nonworking network connection:
All of a sudden Ubuntu cannot no longer connect to the network, this is for both the ethernet and the wired connection. If I do ifconfig from a terminal, eth0 (the ethernet) shows no entry for field inet addr.
For the wireless connection, Ubuntu used to connect automatically to network, and for the wired network, there is just no connection. 
The only thing I can ping is the loopback device (127.0.0.1)

Thanks in advance.

---

### Post by Iowan on 2010-08-13
A few things to check/try:
Right-click Network Manager - verify "Networking Enabled" is checked.
[http://ubuntuforums.org/showthread.php?t=1537792]("http://ubuntuforums.org/showthread.php?t=1537792")
[http://ubuntuforums.org/showthread.php?t=1505217]("http://ubuntuforums.org/showthread.php?t=1505217")
(I didn't check these closely - hope they're not redundant...)

---

### Post by Petter72 on 2010-08-14
The problem was that I had disabled the network connections and lost the network manager icon  to enable it.
The odd thing was that I was able to get the network manager back by adding a notifiaction area to the task bar.

thanks

---

### Post by Iowan on 2010-08-14
> **Petter72 said:**
> 
The odd thing was that I was able to get the network manager back by adding a notifiaction area to the task bar. Yeah, that was in a link I apparently forgot to include. :(

You can use the Thread Tools to mark this thread [SOLVED]. :)

---

