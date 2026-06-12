---
title: "New mb - no network inferface detected"
date: 2013-08-06
forum: Networking &amp; Wireless
---

### Post by rune_pedersen2 on 2013-08-06
So I just bought a new computer, with an Asus F2A95-V motherboard. Installed Ubuntu Server on the machine, and it could'nt detect any network interface hardware. I have no idea how to get the drivers, and install from the terminal (as I have no desktop).

Help appreciated!!

---

### Post by rune_pedersen2 on 2013-08-06
lspci shows that a driver is loaded for the network hardware.

Ethernet controller: Atheros COmmunications Inc. AR8161 Gigabit Ethernet (rev 10)

Under the network detection while installing Ubuntu, it detected nothing :/

---

### Post by rune_pedersen2 on 2013-08-06
Tried downloading and installing the linux-backports-modules-cw-3.4-precise-generic , and then using the modprobe alx command. It shows that the alx module is not found (might be for wireless connections).
Any suggestions for an solution? I'm struggling to get this to work.
It's an ASUS F2A85-V motherboard.

---

### Post by chili555 on 2013-08-06
We need more information:```
lspci -nn | grep 0200
lsb_release -a
```You are on the right track, I suspect.

---

### Post by rune_pedersen2 on 2013-08-07
lspci -nn | grep 0200
result: 03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)

lsb_release -a
result: 
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 12.04.2 LTS
Release: 12.04
Codename: precise

thanks

---

### Post by chili555 on 2013-08-07
Your device *is* covered in linux-backports-modules-cw-3.4-precise-generic. Let's try to see what went wrong:```
sudo apt-get install --reinstall linux-backports-modules-cw-3.4-precise-generic
sudo apt-get install --reinstall linux-backports-modules-cw-3.4-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.```
sudo modprobe alx
```Please note and post any errors or warnings.

---

