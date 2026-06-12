---
title: "Error : can not access internet with ADSL modem"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by Epenjehem on 2010-10-26
I using Ubuntu 10.04 desktop edition
In the morning, i still can access internet with ASDL modem connection. I used command in terminal like this as usual :

[INDENT]sudo pon dsl-provider[/INDENT]

And then i use my laptop to make some PHP project....
Suddenly, i can not access internet any more.

Than i restart my computer, type in sudo pon dsl-provider and it show :

Plugin rp-pppoe.so loaded
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5

Still can not access internet. Then i try to change to another computer, the connection is ok and i can browse like usual.

What happen here? 

Even my modem is off, and i try to connect again with the same method like above, it show the same result.

Any one can help??

---

### Post by dineshs on 2010-10-26
Try if this can help
First backup  /etc/network/interfaces using
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
Now run
```
 gksudo gedit /etc/network/interfaces
```
Let the file contain only these lines ```
auto lo
iface lo inet loopback
```
(delete other lines)
Now try ```
pon dsl-provider
``` to connect.If you still have problems post the contents of```
sudo gedit /etc/resolv.conf
```

---

