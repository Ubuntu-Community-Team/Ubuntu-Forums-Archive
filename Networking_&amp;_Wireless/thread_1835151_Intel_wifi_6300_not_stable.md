---
title: "Intel wifi 6300 not stable"
date: 2011-08-28
forum: Networking &amp; Wireless
---

### Post by acrush on 2011-08-28
Hello i got ubuntu 11.04 installed on my thinkpad T510,everything works great except the wireless. The wireless works fine when the system just boot up, however if I go download anything the network traffic will go down to 0 bit/s. I cannot even use the software center.

this is really painful...please help :mad:

---

### Post by praseodym on 2011-08-28
Hi,

what encryption mode do you use? There are sometimes problems with mixed WPA/WPA2-mode, better use WPA2-AES. Can you show the following terminal outputs:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
sudo iwlist scan
dmesg | grep iwl
route -n
cat /etc/resolv.conf
```

---

### Post by acrush on 2011-08-28
Awesome!, seems its the problem with encryption mode.
changed to WPA2-AES now it works fine

thanks for helping
> **praseodym said:**
> Hi,

what encryption mode do you use? There are sometimes problems with mixed WPA/WPA2-mode, better use WPA2-AES. Can you show the following terminal outputs:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
sudo iwlist scan
dmesg | grep iwl
route -n
cat /etc/resolv.conf
```

---

