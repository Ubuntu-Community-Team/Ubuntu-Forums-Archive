---
title: "No network connection 9.10 Karmic"
date: 2012-04-02
forum: Networking &amp; Wireless
---

### Post by MikeDanger on 2012-04-02
I have an SSH server running 9.10 Karmic that suddenly won't connect to the Internet or to my other servers. (including the NIS/NFS server that it mounts /home from). I have tried pinging other devices but everything comes back as "host unreachable". I don't think that there are any problems with the actual connection to the computer itself (ie from the wall to the NIC).

The most descriptive thing I have found so far came when I tried an /etc/init.d/networking restart: 
```
Restarting openntpd: invoke-rc.d: initscript openntpd, action  "force-reload" failed.
run-part: /etc/network/if-up.d/openntpd exited  with return code 1
```Does this ring any bells for anyone?

---

### Post by Iowan on 2012-04-02
I'll forgo the reminder that 9.10 is almost a year past EOL. 
**openntpd** doesn't ring any bells. Machine shows valid IP address and routing?

---

### Post by MikeDanger on 2012-04-02
IP address in ifconfig is the expected static IP. What do you mean by routing? DNS doesn't work, if that's what you're getting at.

---

### Post by Iowan on 2012-04-03
Yeah, I was probably getting to DNS after checking **route -n**... 
I presume you're pinging the other devices by IP address - so DNS doesn't come into play.

---

