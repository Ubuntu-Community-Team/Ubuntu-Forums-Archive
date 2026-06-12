---
title: "Network manager Prob"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by rotate2010 on 2010-08-21
hii frnds,i have just installed ubuntu 9.04...then create dsl connection for Bsnl broadband connection through network manager and it was working properly...but then i upgrade my system 9.04 to 9.10...it upgraded successfully..but then my internet didnt work properly..means my eth0 was enabled and connected..but when i clicked on Bsnl connection..it didnt connect..till now my netwrok manager was working properly..then i make connection through command "sudo pppoeconf"..it was started..but now i want to connect through network manager...now my whole network manager is disabled..means i cant create any new connection...if i click add on dsl then i fills all info but when i click on "Apply"..dat window poped off and no connection was created..so pls help me..this happened with me second time..and i noticed that if u once make connection through pppoeconf then ur whole network manager is disabled..whts reason behind it???how can i get it back??thnx in advance

---

### Post by dineshs on 2010-08-21
Have a look here
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)
But I think Network manager in 9.10 has bug
[http://ubuntuguide.net/fix-dsl-pppoe-connection-problem-with-network-manager-in-ubuntu-9-10](http://ubuntuguide.net/fix-dsl-pppoe-connection-problem-with-network-manager-in-ubuntu-9-10)
What I suggest is
It is better to configure your modem in PPPoE mode.For this follow instructions given in the first link upto reboot.Then follow this link 
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html) 
and configure your modem(select your modem under the menu CPE configuration)
The connection will be always ON

---

