---
title: "Wicd - Changed access point and ip range and can't ping anything"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by neohobbit on 2009-03-01
I have searched and haven't found anything that seems to be similar to my issue or seem to have fixed it. My apologies if I have missed one that already answers my problems.

My Lenovo 3000 C200 Laptop was connected to my Wireless with WPA access point using WICD at home, that was in the 192.168.0.0 range and working perfectly.

I took my laptop into the office and used WICD to change to work's Access Point which is using WEP (I know it should be WPA but its a long story) and is in the 10.1.1.0 range with a static ip (as there is no DHCP server). WICD tells me it is connected. 

I can not ping anything in the 10.1.1.0 range. Not even the router. I can only ping myself.

I am running Ubuntu 8.10 with XDM and Openbox

Wireless Card: Broadcom BCM4311  (with the b43 restricted drivers)
ifconfig shows that eth1 (my wireless card) has the static ip, and gateway and dns all seem to be pointing to the right place.
```

inet addr:10.1.1.203 Bcast:10.1.1.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:263
TX packets:0 errors:3 dropped:0 overruns:0 carrier:0
```


Where i am sitting right now I don't have access to a wired socket to test wired lan to make sure it is still ok. I have resorted to use my desktop to send this message :P

---

### Post by qbox on 2009-03-01
Broadcom cards always have some problem. Maybe I have some problems like yours. When I try to connect to WEP locked network sometimes I dodnt get correct IP or i get connected but cant open nothing. There is some bugs in the drivers. I use windows drivers. Have same bugs with ndiswrapper and with restricted drivers. Sometimes I get connected and have good internet connection and sometimes I cant connect. I waiting for a good linux drivers.
But maybe me and you dont have the same problem. 
Try this
1.
Check the default gateway (type in console 'route') if its not set the right GW set it with
sudo route add default gw <DEFAULT GW ADDRESS>
2. if ok (1.)
try to ping the router. if ping success try to ping another computer in the network. 
3.If ok (2.)
check the DNS.
Good luck.

---

### Post by neohobbit on 2009-03-01
Thanks for your reply.

route -n results in the following:
> 
Destination     Gateway   Genmask       Flags Metric Ref  Use Iface
10.1.1.0        0.0.0.0   255.255.255.0 U     0      0    0   eth1
0.0.0.0         10.1.1.1  0.0.0.0       UG    0      0    0   eth1


ping 10.1.1.1

results in Destination Host Unreachable.

I'm curious about whether it will go back to my home network fine when I finish work tonight. Might stay after work tonight and just as an experiment change the wireless to WPA to see if it has something to do with WEP encryption. As i stated before, I use WPA at home and it was working perfectly. Just seems to be change of Networks that has caused this.

---

### Post by imdano on 2009-03-03
Wicd will think you're connected as long as you have an IP address and a link quality greater than 0.  I've seen several cases where people using static IP's have appeared to be connected because they assigned themselves an IP and their driver is reporting a valid link quality, but in reality something like authentication (especially WEP) has failed so they're not really connected.  What does the output of iwconfig look like?

---

