---
title: "Internet via USB Stick on Ubuntu 9.10"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by soj on 2010-01-25
Hi,

I just installed Ubuntu 9.10 on my compaq presario V3000 series laptop through Windows XP. I am trying to connect to the internet via a USB Stick (Huawei EC168C. The modem is getting detected however, once I try to connect from the notification area, it does nothing.

Can anyone help me?

Thanks
Soj

---

### Post by pdc on 2010-01-25
this is the never-ending story that linux sees these devices as CD-ROM devices, and they need to be flipped;

eg see here for an explanation

[http://tux-n00b.blogspot.com/2009/05/huawei-ec168c-on-ubuntu-804-hardy-heron.html](http://tux-n00b.blogspot.com/2009/05/huawei-ec168c-on-ubuntu-804-hardy-heron.html)


BUT FIRST, open a terminal and type in

> lsusb           copy and paste the results back here


if by a miracle it says

> 12d1:140b Huawei

see here for configure

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

go halfway down the page: "Create a mobile .." tells you how to configure

let us know it goes for you

---

### Post by soj on 2010-01-26
Hi,

Thank you for your quick response. Please find what I got in Ubuntu 9.10 on typing "lsusb" in the terminal window.

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 12d1:1412 Huawei Technologies Co., Ltd.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Hope this helps you to help me resolve the issue.

Thank you

Regards,
Soj

---

### Post by soj on 2010-01-27
Hi Ubuntu Lovers,

Any help in this matter is most appreciated.

Thanks

Soj

---

### Post by darkod on 2010-01-27
> **soj said:**
> Hi Ubuntu Lovers,

Any help in this matter is most appreciated.

Thanks

Soj

Did you try the procedure from the second link in post #2?

---

### Post by soj on 2010-01-27
Hi

Yes I did. it still doesnt allow me to connect.

Thanks
Soj

---

### Post by pdc on 2010-01-27
a device was an identical number is used on a Reliance piece of equipment;

here is a link

[http://reliancewireless.wordpress.com/](http://reliancewireless.wordpress.com/)

try it;

the essence is a programme called wvdial is installed;

it bypasses network manager

if you google search on 

> ubuntu huawei 12d1:141

the posts I read have all used wvdial

tell us what country and network you wish to connect to

---

### Post by jeymbj on 2010-02-06
us 002 Device 004: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 062a:0252 Creative Labs 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by jeymbj on 2010-02-06
hi

i am in germany and the provider is O2 Germany
i need help to make it work i have use linux for more than 5 years but i am not good working with the terminal can someone advise me about 
and help me to install my usb stick for internet

thank you in advance

---

