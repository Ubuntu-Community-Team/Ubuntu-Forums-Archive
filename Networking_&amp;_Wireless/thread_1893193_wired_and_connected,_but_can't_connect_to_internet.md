---
title: "wired and connected, but can't connect to internet"
date: 2011-12-09
forum: Networking &amp; Wireless
---

### Post by sdelinde on 2011-12-09
Toshiba satellite a215, lucid Lynx 64-bit os. I ran cd to install Lucid Lynx, and have manually set up my wired network. I can see other computers on network but can not
get the internet on fireFox to find server. My ip address and dns are correct, they worked
well with Ubuntu 7.10. What am I missing in order to get connected.

Thanks for any of your help! I have played with Ubuntu for a while but an still a green horn
newby.

---

### Post by praseodym on 2011-12-09
Hi,

please show

```
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```

---

### Post by sdelinde on 2011-12-09
[attach]208821[/attach][attach]208822[/attach][attach]208823[/attach][attach]208824[/attach][attach]208825[/attach]

---

### Post by sdelinde on 2011-12-09
[attach]208826[/attach]

---

### Post by praseodym on 2011-12-09
Do you have a wired connection available? Even if not, can you try:

```
sudo apt-get install linux-backports-modules-wireless-$(uname -r)
```
If it doesnt work: Check box all user rights in "USERS&GROUPS", login again, remove your wired profiles in "wired" and "dsl" (if any) and reboot.

---

### Post by sdelinde on 2011-12-12
[praseodym]("http://ubuntuforums.org/member.php?u=1411497") , I do have wireless but am to far from signal. My problem is the wired network. It shows that I am connected, I can see others printers and desktops on my network, so I am connected, I just
can not get on the internet!

Thanks for your help, I had to go out of town for the week-end and could not access the web.

---

