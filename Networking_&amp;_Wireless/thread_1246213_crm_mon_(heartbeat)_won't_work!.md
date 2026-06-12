---
title: "crm_mon (heartbeat) won't work!"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by kevpatts on 2009-08-21
Hey all,

I am trying to setup a basic apache cluster using 2 Jaunty server edition virtualbox clients on and "internal network". I have set the boxes up so that they have static IP addresses and can ping each other. I then installed heartbeat (sudo apt-get install heartbeat) and followed [this]("http://linux-ha.org/Education/Newbie/InstallHeartbeatScreencast") basic guide.

The machines are called web1 and web2 and so I used "node web1 web2" in the ha.cf file. Each machine has a cluster, but each cluster only has 1 node configured, the machine it's running on. The other node isn't even mentioned as being offline.

Also, there is nothing heartbeat related appearing in /var/log/messages

All help appreciated.

Regards,
Kevin

---

