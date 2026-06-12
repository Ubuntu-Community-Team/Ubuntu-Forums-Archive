---
title: "mt-daapd autostarts but wont work"
date: 2012-06-11
forum: Networking &amp; Wireless
---

### Post by jan-banan on 2012-06-11
When i boot ubuntu 12.04 mt-daapd is autostarted but it doesnt show up in iTunes on my OS X 10.6.8 mac computer. If i restart mt-daapd using sudo killall mt-daapd && sudo mt-daapd -f it works just fine. I have tried the fix from this blog post: [http://www.vleeuwen.net/2009/05/setup-firefly-to-serve-itunes#comment-132](http://www.vleeuwen.net/2009/05/setup-firefly-to-serve-itunes#comment-132) in other words: sudo gedit /etc/init.d/mt-daapd and add the line DAEMON_OPTS=-m but it does not help. Any suggestions? 

The problem might be related to this problem since they booth appeared at the same time:
[http://ubuntuforums.org/showthread.php?p=12017016#post12017016](http://ubuntuforums.org/showthread.php?p=12017016#post12017016)

---

### Post by jan-banan on 2012-06-12
I managed to fix this on my own, i deleted mt-daapd from /etc/init.d/ and added it to /etc/rc.local, this also fixed the problem with netatalk. I dont know exactly why they had a conflict but either way it is resolved.

---

