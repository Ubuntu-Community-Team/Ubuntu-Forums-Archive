---
title: "Ubuntu 10.04 LTS and 2 Networking Cards Problem"
date: 2011-08-25
forum: Networking &amp; Wireless
---

### Post by Th3Blaze on 2011-08-25
On my iPod , but i'll try to show you the outputs . I have an Atheros AR5001X and an nVidia Ethernet controller and there is no possible way 
To connect tO the internet. I have followed many guides but give up ... Any advice ? 
Thanks in advance

---

### Post by praseodym on 2011-08-25
Hi,

does

```
lspci -nnk | grep -iA2 net
```
show the drivers ath5k and forcedeth, respectively? Are these modules shown by
```

lsmod
```
? Is the Nvidia-Ethernet device a Gigabit device? For this driver two module parameters can be applied:

```
echo "options forcedeth msi=0 msix=0" | sudo tee /etc/modprobe.d/forcedeth.conf
```
and reboot.

---

