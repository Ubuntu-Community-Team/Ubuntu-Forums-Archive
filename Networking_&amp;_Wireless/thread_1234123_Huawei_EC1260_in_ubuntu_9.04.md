---
title: "Huawei EC1260 in ubuntu 9.04??"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by Vasan on 2009-08-07
I installed Ubuntu 9.04 in my Inspiron 1525. I am not able to coonect to net with my Huawei EC1260 in ubuntu 9.04. Its reliance broadband+ . I tried wvdial. But it didnt work. I am a beginner to ubuntu.

---

### Post by wangrui on 2010-07-09
There actually is a perfect solution for this problem. But I also didn't know it until today.

First, install usb-modeswitch
```
sudo apt-get install usb-modeswitch
```

After this, you can see the modem device
```
ls /dev/ttyUSB*
/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2
```

I use the following config file
```
cat /etc/wvdial.conf 

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyUSB2
ISDN = 0
Phone = #777
Password = internet
Username = internet
Stupid Mode=1
```

then
```
sudo wvdial
```

A lot of people didn't know usb-modeswitch, which is not installed by default. It is a perfect solution for all devices which contains installer CD in its chip.

---

