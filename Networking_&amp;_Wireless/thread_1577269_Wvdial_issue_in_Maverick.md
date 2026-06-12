---
title: "Wvdial issue in Maverick"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by shahdharmit on 2010-09-18
Hello,

I am from India. I've just installed Maverick beta. I use Reliance Netconnect to surf the Internet. In Fedora, I connect it with wvdial command. In Ubuntu I can't connect it. Following is my /etc/wvdial.conf file for Fedora ```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
Phone = #777
Modem = /dev/ttyUSB0
Username = phonenumber
Password = phonenumber
Baud = 9600

```And following is the /etc/wvdial.conf for Maverick.
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
ISDN = 0
Abort On No Dialtone = False
New PPPD = yes
Phone = #777
Modem = /dev/ttyUSB0
Username = phonenumber
Password = phonenumber

```The problem is that when I run ```
sudo wvdial
``` it says /dev/ttyUSB0 does not exist. The modem gets mounted on /dev/sdb. But replacing ttyUSB0 with sdb also doesn't work.

What shall I do?

Thanks.

---

### Post by grahammechanical on 2010-09-19
Did you replace modem = /dev/ttyUSB0 with modem = /dev/ttysdb or modem = sdb? Frustrating problems can cause us to miss the obvious.

Regards.

---

### Post by prat22 on 2010-12-15
[B]It seems you have a memory device inside the modem. Do you have a microSD card inserted in it by any chance?

If not, then install the gnome-ppp package and use it to configure your modem. Go to modem tab, and mount it manually at USB0. If this doesnt solve, there is a button beside it which says to detect the modem. Use it, it will find it on ttyUSB0, or ttyACM0, whatever.

And as far as I remember, *I *used to give "netconnect" as both my username and password. See the log carefully to understand where you are stuck.
[/B]

---

