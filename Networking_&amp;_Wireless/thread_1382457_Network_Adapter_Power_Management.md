---
title: "Network Adapter Power Management"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by jurusu on 2010-01-16
How do i set the netwok adapter power to maximum?

In windows, this can be easily set under device manager --> hardware --> ..power management...

Thanks!!!

---

### Post by chili555 on 2010-01-16
I believe they are set to maximum by default. You can experiment. Here are my abbreviated tests:> chili@LAPTOP40:~$ iwconfig eth1
eth1      IEEE 802.11abg  ESSID:"GBR1"  
          --- snip ---
          Tx-Power=20 dBm
          --- snip ---
chili@LAPTOP40:~$ sudo iwconfig eth1 txpower 18
[sudo] password for chili: 
chili@LAPTOP40:~$ iwconfig eth1
eth1      IEEE 802.11abg  ESSID:"GBR1"  
          --- snip ---
          Tx-Power=18 dBm   Sensitivity=8/0  
          --- snip ---
chili@LAPTOP40:~$ sudo iwconfig eth1 txpower 21
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Invalid argument.If you find that the power is not at maximum, you can add a line to /etc/rc.local above 'exit 0':```
iwconfig eth1 txpower 20
```I am not at all certain that all cards allow the power to be changed.

---

### Post by jurusu on 2010-01-23
It is indeed set at maximum by default.
Thanks!

---

