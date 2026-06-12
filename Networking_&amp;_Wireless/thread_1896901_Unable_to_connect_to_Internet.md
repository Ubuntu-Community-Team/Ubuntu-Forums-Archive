---
title: "Unable to connect to Internet"
date: 2011-12-18
forum: Networking &amp; Wireless
---

### Post by wasim24 on 2011-12-18
Hello sir/mam i am very new to ubuntu i use ubuntu on my laptop with full installation but i am unable to access internet,i tried both 10.** x86 and x64 but not working,the another problem is i have a LAN connection which connects to internet automatically by giving user name and password,i only have IP address and MAC address other information like DNS, sub net mask,Gateway i don't know,and my ISP not giving me that info,the same N/W connects fine on windows7

---

### Post by krishnandu.sarkar on 2011-12-18
For this type of problem I'd suggest you to better configure your modem to PPPoE mode, that will save you from all the hassle of configuring and creating dialer in multiple OS'es. 

And also you'll get internet as soon as you turn on your modem with any device connected. No need to dial.

Anyway you can check [http://manpages.ubuntu.com/manpages/natty/man1/wvdial.1.html](http://manpages.ubuntu.com/manpages/natty/man1/wvdial.1.html) or [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by wasim24 on 2011-12-18
Sir,I downloaded "pppoeconf" package from "http://packages.ubuntu.com/" for natty
i installed it and typed the command "sudo pppoeconf" in terminal but i am getting eroor as "Sorry,no working ethernet card could be found.If you do have an interface card which was not autodetected so far,you probably wish to load the driver manually using the modconf utility.Run modconf now?" and 2 options are available i.e. Yes n no when i click on yes nothing happens.

I not know more about N/W can you explain in brief???

---

### Post by wasim24 on 2011-12-20
:guitar: i am now bored back to topic man

---

### Post by wasim24 on 2011-12-22
no 1 helping me bye i am switching to windows again ;)

---

### Post by praseodym on 2011-12-22
Hi,

please show the following terminal outputs (CTRL+ALT+T):

```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
rfkill list
sudo iwlist scan
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by shibuap on 2011-12-22
Sir,
i have a toshiba satallite c 640 . i installed ubundu 10.4 on it but lan not working how can i solve this issue ,from where i can download its lan driver

---

### Post by praseodym on 2011-12-22
Please show the terminal outputs of the first 4 commands. They show, which kernel is in use, shows the network devices, USB-devices and the drivers loaded. Otherwise its difficult to say which driver(s) you need.

---

