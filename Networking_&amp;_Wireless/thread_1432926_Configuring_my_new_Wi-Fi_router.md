---
title: "Configuring my new Wi-Fi router"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by sahilnanda on 2010-03-18
I am using Ubuntu 9.10.

I just got a Linksys WRH54G wireless router. I want to protect my wireless connection by putting a password to it but when I enter the Router's default IP address (192.168.1.1) into my browser to open the 'Utility Welcome screen', the browser does not respond.

According to the Router's manual this is because PC' TCP-IP is not set to automatically obtain the IP address.

Please help me resolve this issue.

Replies awaited.

Thank you!

---

### Post by chili555 on 2010-03-18
I assume you are connecting to the router with an ethernet cable. Please open a terminal and do:```
sudo ifconfig eth0 192.168.1.2 up
firefox 192.168.1.1
```

---

### Post by sahilnanda on 2010-03-18
Done!

My modem's (not my router's) configuration page opened up.

---

### Post by chili555 on 2010-03-18
Detach the modem from the router and be sure you are connected to the correct port on the router according to the user's manual.

---

### Post by sahilnanda on 2010-03-18
Yes, the connections were a bit messed up. I corrected them and did them as per the Router's manual. I am getting the wi-fi signal but now I can't connect to the internet on my desktop.

---

### Post by chili555 on 2010-03-18
> I can't connect to the internet on my desktop.Wired or wireless? Wireless is not going to work if the wired is connected and has an IP address.

Does your wireless have a driver and an interface? Please check:```
iwconfig
```

---

### Post by sahilnanda on 2010-03-18
Wired connection on the desktop.


Eruslt for 'iwconfig'
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

ppp0      no wireless extensions.

---

### Post by chili555 on 2010-03-18
Click the Network Manager icon and disconnect, count to five, sip some coffee and click connect. Any improvement?

It may have been stuck on 192.168.1.2 with no DNS nameservers; hopefully we have remedied that.

---

### Post by sahilnanda on 2010-03-19
There is no option for disconnecting anything.

By the way, I connect to the internet using 'sudo pppoeconf' and not by a DSL connection via the network manager.

---

### Post by chili555 on 2010-03-19
Please try:```
sudo ifconfig eth0 down 
```Then follow with your pppoe process.

---

