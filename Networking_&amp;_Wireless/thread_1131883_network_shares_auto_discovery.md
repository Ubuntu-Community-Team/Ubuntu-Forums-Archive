---
title: "network shares auto discovery"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by razor7 on 2009-04-21
Hello...when I try to access network in nautilus, i got an error message saying that the network is unavailable, but it becomnes available if I manually add the network machines IP addresses to /etc/hosts

Is there any way to get all machines in the network automatically detected at startup? so I can acces their shared resources.

Thanks a lot!

---

### Post by razor7 on 2009-04-22
Hello... I will auto answer this. Im using openDNS services, so it affects the way names are resolved in my network.

Just changed this line in all samba clients smb.conf file, restarted the box  and everything worked again.

```
 name resolve order = lmhosts host wins bcast
```

To this
```
 name resolve order = bcast lmhosts host wins
```

---

