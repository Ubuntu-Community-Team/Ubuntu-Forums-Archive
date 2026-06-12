---
title: "upgrade from 7.04 to 7.10 break mysql + mythtv (solved)"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by gigli on 2007-10-20
When i upgraded from feisty to gutsy mythtv couldn't connect to mysq, it wouldn't start at boot. I could manually start mysql and mythtv, but whenever i restarted the computer the problem still was there. I couldn't understand this since it worked perfectly for a long time with feisty. The mysql-server bind-address was 192.168.0.2 because of an another mythtv-frontend, the computer itself got the same static ipaddress from the dhcp-server. But if i changed the bind-address in my.cnf to 127.0.0.1 it worked perfect, but i couldn't connect from my another machine. So i have to change from roaming mode to a static address in network-manager, and that solved all the problems. Even after a  restart. Hope this will help someone.

---

### Post by gsanse on 2007-10-25
I had exactly the same problem but have solved it differently. Instead of turning manual ip configuration, I turned off roaming mode and used dchp server for ip assignment. I am not sure what roaming mode is, but it is causing problems with mysql server start.

gsanse

---

