---
title: "setting sierra 305 broadband modem on ubuntu 12.04"
date: 2012-07-21
forum: Networking &amp; Wireless
---

### Post by thebluesvega on 2012-07-21
hello master..
i use ubuntu 12.04 and have a problem with my connection, after install sierra 305 i can detect my modem but i cant connect to internet.
i have delete **/etc/resolv.conf **but it not work.

help me please..
thx

---

### Post by praseodym on 2012-07-21
Hi,

the file /etc/resolv.conf is necessary.

```
sudo touch /etc/resolv.conf
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo /etc/init.d/networking restart
```
You better copy/paste these 3 lines.

Check:

```
lsusb
lsmod
ifconfig -a
cat /etc/resolv.conf
route -n
rfkill list
```

---

### Post by thebluesvega on 2012-07-23
> **praseodym said:**
> Hi,

the file /etc/resolv.conf is necessary.

```
sudo touch /etc/resolv.conf
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo /etc/init.d/networking restart
```You better copy/paste these 3 lines.

Check:

```
lsusb
lsmod
ifconfig -a
cat /etc/resolv.conf
route -n


rfkill list
```



Hi [praseodym]("http://ubuntuforums.org/member.php?u=1411497") thx for your help, i have try your method but it not work..

---

