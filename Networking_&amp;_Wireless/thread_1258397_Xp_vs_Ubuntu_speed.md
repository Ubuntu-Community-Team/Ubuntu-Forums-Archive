---
title: "Xp vs Ubuntu speed"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by invincibletoviruses on 2009-09-05
i used xp and ubuntu on the same system and ive noticed my internet is much faster with xp than ubuntu. I use a wireless connection. 

[edit]
I will go update to 9.04 and see if it is improved

---

### Post by shredder12 on 2009-09-05
Well you can check this link.. somethime IPv6 gets enabled and slows down your internet..
[www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

### Post by invincibletoviruses on 2009-09-05
when i enter ```
sudo vi /etc/modprobe.d/aliases
``` into the terminal this is what it shows
```
~
~
~
~
~
~
~
~
~
~
~
~
~
"/etc/modprobe.d/aliases" [New File]
```
> Find the line: alias net-pf-10 ipv6
change to
alias net-pf-10 off
there is no line saying that

---

### Post by utnubuuser on 2009-09-05
Next thread:[http://ubuntuforums.org/showthread.php?t=1251983]("http://ubuntuforums.org/showthread.php?t=1251983")

---

### Post by shredder12 on 2009-09-05
Well,, it could be that you don't have an ipv6 issue..
but this guide is worth looking.. [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

according to it... in order to check if you have an IPv6 issue.. run this command..
```
lsmod | grep inet6
```

if you get an output like this..
```
 ipv6         123456  22  ip6_tables
```
then it is enabled..
if there is no output then it is already disabled.. i.e. IPv6 is not the troublemaker...

---

