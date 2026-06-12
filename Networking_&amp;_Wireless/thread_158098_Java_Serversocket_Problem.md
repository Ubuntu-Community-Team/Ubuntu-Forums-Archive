---
title: "Java Serversocket Problem"
date: 2006-04-10
forum: Networking &amp; Wireless
---

### Post by outofwindowwatcher on 2006-04-10
Hi,
I'm writing a small server in java. It does nothing more than sending a message to a client (telnet). The code is ok. It listens to a given port (>1024) and I can connect to it at localhost, but not from outside, which does work on any windows machine.
I don't know much about iptables and stuff and don't want to mess around with the settings done by the ubuntu installation. 
Is there an easy way to fix my problem? 

Thanks for any help!

---

### Post by spd106 on 2006-04-11
Maybe try using netstat to view listening sockets. There may be a conflict, though it's unlikely.

---

### Post by outofwindowwatcher on 2006-04-11
Thank you, but I already tried that. Didn't help. Java would give me an esception, if another process listened to the port. I tried it at several different ports - all the same.

---

### Post by outofwindowwatcher on 2006-04-11
Ok, solved it
The thing was, that I had firestarter installed months ago, but since then never used it. But firestarter seemed to have left a script, which did settings to iptables at boot time. After uninstalling and rebooting, everything, I desired, works.
Another missunderstanding of security concepts. Hope I will soon be cured from the brainwashing, that microsoft did to me ;)

---

