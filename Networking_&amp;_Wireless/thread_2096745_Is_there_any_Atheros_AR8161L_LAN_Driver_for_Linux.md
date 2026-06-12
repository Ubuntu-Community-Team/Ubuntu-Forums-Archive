---
title: "Is there any Atheros AR8161L LAN Driver for Linux?"
date: 2012-12-20
forum: Networking &amp; Wireless
---

### Post by c0mrad on 2012-12-20
Hello, I have problem on Linux.
On "HP Pavilion HPE h8-1364ez"  my  Ubuntu cant see Atheros AR8161L LAN device, I can only use Wireless  internet but at home I have only LAN connection.
So is there any Driver  software to install? I found some **alx** driver but there are problems  while installing... Any ideas?

Please Help!

---

### Post by ahallubuntu on 2012-12-20
Did you try installing build-essentials to get rid of that error when you try to make the alx driver?

```
sudo apt-get update && sudo apt-get install build-essential linux-headers-`uname -r`
```

---

### Post by forkandles on 2012-12-22
Using your working wireless internet, follow one of the two options in this link:
[http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller)

---

