---
title: "Ubuntu 10.04 wifi issues"
date: 2013-07-19
forum: Networking &amp; Wireless
---

### Post by caraj on 2013-07-19
I installed the linux non-free firmware I needed to, and now the only problem is that my laptop isn't detecting any networks. And if I choose "connect to a hidden network" the network i choose still never gets connected to.
I've also tried installing wifi radar, but I get the notice "dependencies unsatisfiable: menu", and I don't know what that even means.
How do I solve this issue?

---

### Post by praseodym on 2013-07-19
You know that 10.04 is outdated? Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
rfkill list
sudo iwlist scan
iwconfig
```
What kind of PC is that? Does LAN work?

---

### Post by caraj on 2013-07-19
It's a Dell Latitude D600. And I do know 10.04 is out of date, but it's all I have for now.[ATTACH=CONFIG]244907[/ATTACH][ATTACH=CONFIG]244908[/ATTACH][ATTACH=CONFIG]244909[/ATTACH]
Here's a readout of the terminal after I entered those things you said to.

---

### Post by praseodym on 2013-07-19
Check
```

dmesg | grep b43
```
The file **ucode4/5.fw** is missing in linux-firmware-nonfree. The following file contains the file(s):

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)

Unpack it to /lib/firmware

---

### Post by caraj on 2013-07-19
> **praseodym said:**
> Check
```

dmesg | grep b43
```
The file **ucode4/5.fw** is missing in linux-firmware-nonfree. The following file contains the file(s):

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz)

Unpack it to /lib/firmware

It's telling me I don't have the right permissions to do it. Do I need to log in as root? If so, how?

---

### Post by praseodym on 2013-07-19
Save it in "Downloads" and
```

sudo tar xvf ~/Downloads/2480236-Broadcom_Firmware.tar.gz -C /lib/firmware
```

---

