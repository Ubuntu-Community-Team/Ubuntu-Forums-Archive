---
title: "slow internet connection after upgrade to 11.04"
date: 2012-02-27
forum: Networking &amp; Wireless
---

### Post by nyinyizaw on 2012-02-27
Please help me

    [SIZE=2]I was using 10.10 ubuntu . it is OK with connection. recently upgrade to 
11.04 and internet connection very slow. 
    while I was using (10.10 ) added this line for better connection . It worked. so while upgrade installing I choose to keep this file without replace. 
    I am using Ralink 802.11 n WLAN 

If you want more information ,please tell me, 
    SORRY for my English writing, thks

   [/SIZE]

---

### Post by madverb on 2012-02-27
Some of the ralink ones are terrible. I had the same issue with Ubuntu after an update. I think I downloaded the drivers from the ralink site and installed them using their package and it came back up.

---

### Post by nyinyizaw on 2012-02-27
Ok I got an answer . I shared here 


     it was wireless driver .   I went to     lsmod       and copy driver name and put in /etc/modprobe.d/blacklist.conf and   restart   NOW everything fine      :)   Thanks ubuntu forum

---

