---
title: "network configuration in ubuntu 12.04"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by jee1991 on 2012-06-13
I am using adsl modem to connect to internet.
 Thinks were working fine with my ubuntu 12.04 but for a week while booting i get this
            " waiting for network configuration" 
followed by 
            " waiting for 60 more seconds for network configuration" 
then i dont get the network icon in the desktop title bar and I am not connected to internet 

... Please help me to fix this....

---

### Post by jee1991 on 2012-06-13
[QUOTE=jee1991;12023421]I am using adsl modem to connect to internet.
 Thinks were working fine with my ubuntu 12.04 but for a week while booting i get this
            " waiting for network configuration" 
followed by 
            " waiting for 60 more seconds for network configuration" 
then i dont get the network icon in the desktop title bar and I am not connected to internet 
      I have tried changing my ethernet cable and LAN card..

... Please help me to fix this....

---

### Post by jee1991 on 2012-06-13
thanks ..
 this page helped me
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

---

### Post by tistu on 2012-06-15
Hello!
My system boot-up gets delayed 2-3 minutes and a message saying Waiting  for network configuration appeares on plymouth. Now, I had this problem  before, when I used pppoeconf to configure a pppoe connection, and then  when I didn't use it anymore, I unplugged the cable, because, then I  wanted to use my wireless connection. I left /etc/network/interfaces  empty and I changed /etc/NetworkManager/NetworkManager.conf  (managed=true). The bug was then gone.
I configured the pppoe connection again and now I don't want to use it  anymore and I did everything I told you, but now, the bug doesn't  dissappear anymore. /etc/network/interfaces is empty,   /etc/NetworkManager/NetworkManager.conf is managed.
What sould I do, cause my networkmanager doesnt start on boot anymore, and I have to start it with boot-up manager everytime.

---

### Post by krishnamohan on 2012-06-30
The first fix in this site did it for me..

[http://www.codewhirl.com/2011/10/ubuntu-11-10-waiting-up-to-60-more-seconds-for-network-configuration/](http://www.codewhirl.com/2011/10/ubuntu-11-10-waiting-up-to-60-more-seconds-for-network-configuration/)


Note that I have Network Manager added to startup applications...and I use it to create wired connections...

---

