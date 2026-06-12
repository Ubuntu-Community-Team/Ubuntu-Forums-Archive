---
title: "Wireless is not enable in my HP Pavilion TS Sleekbook 15"
date: 2013-07-16
forum: Networking &amp; Wireless
---

### Post by mohanix on 2013-07-16
My laptop led is still showiing red that means wireless is not enabled. Im using ubuntu 12.10
I have tried in terminal rfkill list all and shows as following
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by praseodym on 2013-07-16
Please show these outputs, too:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
ifconfig -a
cat /etc/resolv.conf
route -n
iwlist chan
sudo iwlist scan
```

---

