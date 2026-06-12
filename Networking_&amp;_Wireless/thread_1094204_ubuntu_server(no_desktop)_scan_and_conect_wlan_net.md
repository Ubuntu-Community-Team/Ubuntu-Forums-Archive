---
title: "ubuntu server(no desktop) scan and conect wlan network"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by dugixy1 on 2009-03-12
hello 

my 1 post and problem

i am new on ubuntu, i need only how to conenct my ruter from ubuntu server,i need command to scan my ruter and conect my network?

with command sudo iwlist scan i see my and neighbours network but i dont howe to pick up my network and conct my ruter,i try 15 days and people dont now, because i come here.

thanks

please help

---

### Post by MaxIBoy on 2009-03-12
To scan for networks:
```
sudo iwlist scan
```

To join the network for which you have the best signal:
```
sudo iwconfig wlan0 essid any
```

To join a network called "dugixy1_network:"
```
sudo iwconfig wlan0 essid dugixy1_network
```

---

### Post by dugixy1 on 2009-03-12
thanks very much,that works super but i still have a problem

 i have WEP Encryption and whan is encription up i can not conect my ruter.

i need more command

now work fine witout WEP, but i need with wep

my network name is - SpeedTouchEE761B
my interface is -  802.11b/g

and use WEP encryption.

thanks again:D

---

### Post by dugixy1 on 2009-03-13
update,please help

---

### Post by MaxIBoy on 2009-03-13
[http://www.ibiblio.org/john/linux-wep.html](http://www.ibiblio.org/john/linux-wep.html)

It was on the first page of Google results, not that hard to find.

---

