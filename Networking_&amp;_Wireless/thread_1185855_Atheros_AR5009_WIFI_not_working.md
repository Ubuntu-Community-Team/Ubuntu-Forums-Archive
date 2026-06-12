---
title: "Atheros AR5009 WIFI not working"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by stressfreesoul on 2009-06-12
Im having a few issues getting my HP G60-100EM working in Ubuntu and wondered if you could help. Its the damn Atheros AR5009 WIFI adapter, I cant seem to get it working in Ubuntu 9.04.
Ive tried both the standard driver and the Madwifi driver (proprietary) with no results. Id really like to get it working, it saves having a dongle sticking out the side.

---

### Post by x22 on 2009-06-12
looks like a solution here:

[http://ubuntuforums.org/showthread.php?t=929012](http://ubuntuforums.org/showthread.php?t=929012)

"modprobe ath9k"

---

### Post by ronz0o on 2009-06-12
Plug the Ethernet in, sudo apt-get update, sudo apt-get dist-upgrade, and reboot. Go to hardware drivers, and see if you have restricted drivers waiting for you. You should be good to go!  =)

---

