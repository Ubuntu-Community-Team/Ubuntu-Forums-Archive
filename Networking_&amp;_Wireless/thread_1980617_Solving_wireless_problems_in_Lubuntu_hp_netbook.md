---
title: "Solving wireless problems in Lubuntu hp netbook"
date: 2012-05-15
forum: Networking &amp; Wireless
---

### Post by bawwi on 2012-05-15
Been using Ubuntu for a while now, and now I've made the full switch to Lubuntu and couldn't be happier. My problem is with my hpmini 100e net book, that had the typical issue of hardware blocked wireless connection. Introducing the following codes in the terminal solves the problem:

"sudo rmmod -f hp-wmi
sudo rfkill unblock all" 
rfkill list all"

My question is if there is a way to load these commands to a script so I don't have to type them everytime. I knew it was possible in Ubuntu. 

Thank you for your kind advice

---

### Post by chili555 on 2012-05-15
How about this:```
sudo su
echo "blacklist hp-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and I think you'll be all set; no more commands to issue.

---

### Post by bawwi on 2012-05-15
> **chili555 said:**
> How about this:```
sudo su
echo "blacklist hp-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and I think you'll be all set; no more commands to issue.

Thank you, it worked. Solved

---

