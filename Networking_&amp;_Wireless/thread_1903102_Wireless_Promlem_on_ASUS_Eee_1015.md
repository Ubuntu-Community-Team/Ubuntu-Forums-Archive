---
title: "Wireless Promlem on ASUS Eee 1015"
date: 2012-01-01
forum: Networking &amp; Wireless
---

### Post by karantina_21 on 2012-01-01
Hello,

I have just installed ubuntu10.04 netbook edition on my netbook. However, I cannot connect internet with wireless or LAN. I quess my wireless device does not work properly.
when I write iwconfig on terminal I got output like " no wireles extensions".
when I write sudo iwlist wlan0 scan I got output like "interfane does not support scanning"
lastly my driver is "broadcom corporation device 4727"

waiting for your help

---

### Post by praseodym on 2012-01-01
Hello,

for the Broadcom 4727 you need to install the packages **dkms**, **patch**, **fakeroot**, and **bcmwl-kernel-source**. They are packed on the installation-CD in the folders in **~/pool/**, in one of the alphabetical folders. Just install them by double clicking one after another, and activate the "Broadcom-STA"-driver in "additional drivers".

For LAN: Please open a terminal (CTRL+ALT+T) and show the outputs of the commands:
```
lspci -nnk | grep Ethernet
cat /etc/network/interfaces
ifconfig -a
lsmod
```

---

### Post by karantina_21 on 2012-01-02
Hi
I succesively installed patch and fakeroot. However, when I want to install dkms I got an error like "Dependency is not suitable:gcc"
after this error I tried to install everything in g folder. But &#305; always got en error. Moreover when I try to install bcmwl-kernel-source I got an error like "Dependency is not suitable:dkms". this funny. since &#305; have to install first dkms to be able to install kernel. Also I have to install first gcc to be able to install dkms. this is a loopthat I could not solve.

---

### Post by praseodym on 2012-01-02
Take the 2 packages dkms and bcmwl-kernel-source, copy them to "Downloads" and install them with:

```
sudo dpkg -i ~/Downloads/*.deb
```
Show the error messages. You can search and download the missing packages from [http://packages.ubuntu.com](http://packages.ubuntu.com) for your Ubuntu version and 32 or 64 bit, and try the command again until it worked.

---

