---
title: "Wire less not getting detected in the scroll down menu"
date: 2011-12-08
forum: Networking &amp; Wireless
---

### Post by teja2609 on 2011-12-08
Hie Friends, 


I am new to Linux OS and i recently installed Unbutu 10.10 in my laptop.  When i am using laptop found that wire less is getting detected. even  in the scroll down of network connection icon. Laptop is Dell INSPIRON  15R N5010 MODEL. please do help in getting out of this problem. Thanks  in advance.

---

### Post by teja2609 on 2011-12-10
Friends please help me out.

---

### Post by karol4722 on 2011-12-10
so your laptop detected network or not?
If not change 
```
managed=false
```
for
```
managed=true
```
in
```
/etc/NetworkManager/NetworkManager.conf
```
then
```
/etc/init.d/networking restart
```

---

