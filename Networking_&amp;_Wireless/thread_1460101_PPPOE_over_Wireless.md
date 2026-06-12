---
title: "PPPOE over Wireless"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by theneoindian on 2010-04-22
Hi , 

      My adsl modem is in bridge mode . I can connect to internet via pppoe . pppoeconf recognise the pppoe in eth0 and setup a connection and i can use it .. Now , the Problem :

How can I setup a pppoe connection using pppoeconf so that it uses wireless ? I set the wireless mode to bridge in modem settings . But , after that , the access point stopped appearing in "aps in range" in network manager and i can't connect to it . pppoeconf also doesn't recognise wlan0 as a valid pppoe link . but dat is normal since i don't think it can check if wlan0 is pppoe without wlan0 being connected to the modem's wireless network . 

SO , HOW CAN I CONNECT TO INTERNET WITH MODEM IN BRIDGE MODE AND CONNECTING VIA THE WIRELESS INTERFACE OF THE MODEM ??

sidenote :confused: : hey , is pppoe over wireless even possible ? coz the datalink layer of wlan is not ethernet rite ?? correct me if i'm wrong ...

---

### Post by theneoindian on 2010-04-24
Hehe , as usual , i don't  get any replies ... Sooo sad :(

---

### Post by pdc on 2010-04-24
join this forum

[http://www.linuxquestions.org/questions/index.php](http://www.linuxquestions.org/questions/index.php)

---

### Post by theneoindian on 2010-04-25
> **pdc said:**
> join this forum

[http://www.linuxquestions.org/questions/index.php](http://www.linuxquestions.org/questions/index.php)

joined it ... thnx  :guitar:

---

### Post by chili555 on 2010-04-25
Of course it will work with wireless. The first step is to assure that your wireless is actually working. Does *iwconfig* show a wireless interface, wlan0 or eth1, perhaps? Next, click the Network Manager icon. Do you see your network? Right click the icon and select Edit Connections. Select DSL, add your details and you should be all set.

---

### Post by theneoindian on 2010-05-09
Hi , 
The problem is solved now . My main error was in misunderstanding the Wireless Bridge mode :) nyway after changing it to AP mode and running pppoeconf solves the problem . But i've to check if it is working after pppoeconf adding wlan0 to /etc/interfaces . 'll reply after checkin it . tnx for the replies

---

### Post by theneoindian on 2010-05-09
i've checked if it is working after pppoeconf adding wlan0 to /etc/interfaces . It DOESn't . Yeah , it is normal :) . nyhow , I had to manually remove the entry for wlan0 from /etc/interfaces . Now it's good to go .

---

