---
title: "ifup wlan0 doesn't work anymore"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by borobudur on 2009-04-02
I had it working the first time but now it doesn't anymore!?

It's a script in** /etc/network/if-up.d/**

```
ifup wlan0 dosomething
```Edited: I read somewhere that for **ifup** the network interfaces have to be in the file **/etc/network/interfaces**. But if I put them like this
```
auto wlan0
iface wlan0 inet dhcp
```my system acts very weird. Doesn't come up anymore at startup!?

---

### Post by borobudur on 2009-04-07
*** bump ***

---

### Post by kevdog on 2009-04-07
Can you tell us what you are trying to do or trying to accomplish?

---

### Post by borobudur on 2009-04-07
It's a short java program calling my ldap server. The program checks if today is anybodies birthday. 

I would like to run my program each time when the network is available (this is usually the case at start up). 

So, I have a script in **/etc/network/if-up.d/ **calling my program:

```
ifup wlan0 /path/to/my/script/check-birthday.sh
```Actually it looks like this:```
#! /bin/sh
date +"%Y-%m-%d_%H:%M:%S $(ifup wlan0 birthday)" >> /var/log/birthday.log
```I just see the date in my log file. It seems it ignors the ifup.

---

### Post by kevdog on 2009-04-07
ifup wlan0 /path/to/my/script/check-birthday.sh

That statement doesnt make any sense to me.

You are saying bring the wlan0 interface up (ifup = interface up) and then run this script.

Is this what you want to do?
ifup is not a conditional statement -- its an executable program

---

### Post by borobudur on 2009-04-07
Oh! It's not a conditional statement! Ups...

Actually I wanted to do this in /etc/network/interfaces
```
iface wlan0 inet dhcp
        up birthday
```
But my system doesn't support this...

---

