---
title: "Wired Internet connection not working"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by akhilesh890 on 2010-05-24
Hey all
I installed Ubuntu 10.04 into my compaq notebook.The problem is that I am not able to connect to my wired broadband internet.
Here are the details of my attempts so far:

1)"ifconfig -a" gave 2 devices eth0 and wlan0.
 
2)"pppoeconf" was unable to detect any ethernet cards.

3)Each time I plug in the LAN cable , the network icon would say "connecting" and ultimately result in "disconnected.Now in offline mode".My ethernet device is Realtek PCIe RT8101E/RTL102E (rev 02).

I also tried to install the realtek driver though I was not confident whether I did it correct .

Please help.

---

### Post by akhilesh890 on 2010-05-25
Hey all
I installed Ubuntu 10.04 into my compaq notebook.The problem is that I am not able to connect to my wired broadband internet.
Here are the details of my attempts so far:

1)"ifconfig -a" gave 2 devices eth0 and wlan0.

2)"pppoeconf" was unable to detect any ethernet cards.

3)Each time I plug in the LAN cable , the network icon would say "connecting" and ultimately result in "disconnected.Now in offline mode".My ethernet device is Realtek PCIe RT8101E/RTL102E (rev 02).

I also tried to install the realtek driver though I was not confident whether I did it correct .

Please help.

---

### Post by dineshs on 2010-05-25
Please ensure that the file /etc/network/interfaces
```
gksudo gedit /etc/network/interfaces
``` 
contain only this 
```
auto lo 
iface lo inet loopback
```   

and post the output of
```
ifconfig -a
```

---

### Post by Iowan on 2010-05-25
Merged post from closed thread - deleted duplicate.

From Code of Conduct:> Please do not cross post, or post the same thing in multiple locations.

---

