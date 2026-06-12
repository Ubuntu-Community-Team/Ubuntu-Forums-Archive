---
title: "How to configure ISDN"
date: 2006-02-15
forum: Networking &amp; Wireless
---

### Post by mm197 on 2006-02-15
Hello

I'm using ubuntu 5.10 Live CD and don't know how to configure ISDN connection.
The hardware manager recognize it - But I can't find it in the network tools or networking menu.

Thanks
Moti

---

### Post by SQuIDers on 2006-05-07
I have configured the ppp0 device to be my USB Intracom ISDN modem (set the modem device to be /dev/ttyACM0 in the administration->networking menu). I get connected to the isp (even the red light flashes on the USB modem, like it does when connecting from windows), but i cant ping anything else but myself and the isp (pages in browsers wont open, etc).

Also, i must exclamate that even in slackware 10.2, with both 2.4 and 2.6 i`ve tried (and succeded?) to configure kpp to use my ISDN modem (even passed the extra parameters needed by the ISDN modem - single channel ATB40), but i had the same result like written above... 

I have: Intracom Netmod ISDN terminal (modem) via USB.
I`ve tried: Slackware 10.2 with kernel 2.6 and later with 2.4 kernel with kppp and with Init2 string set to ATB40, and tinkering with resolv.conf.. same result as when connecting to my ISP from Ubuntu 5.10, except in ubuntu i don`t know where to pass the ATB40 command...

Any takers? (i`m currently on ubuntu, and planning to stick with it)

---

### Post by SQuIDers on 2006-05-07
Ive tried with wvdial with following wvdial.conf, and still same results


```
[Dialer Defaults]
Modem = /dev/ttyACM0
Baud  = 115200
Init1 = ATZ
Init2 = ATB40
Phone = 042210555
Username = net
Password = net
```

---

### Post by SQuIDers on 2006-05-07
Made it work
look @ [http://www.ubuntuforums.org/showthread.php?p=993330#post993330](http://www.ubuntuforums.org/showthread.php?p=993330#post993330)

or if using kppp do the following:

go to modems tab
click on a modem and then edit
click on modem tab
click on modem commands
on the "Extra Initialisation commands" type "ATB0KAS0" (i only made it work in dual channel mode :( , but its better then nothing... )


if you dont have a dual channel account at your provider`s, ask for one :P

i`ll play with this some more

---

### Post by SQuIDers on 2006-05-09
I`ve changed my provider, and it works on singlechannel like a charm :)

So, if you get connected via ATB40, and have no traffic, it`s beacuse of the provider.


Cheers

---

### Post by IoRDaN on 2006-05-16
so, im usin' a TELES IS0/PCI
like i am so new user of linux, i dunno to install that modem.
and, of course, i can't access internet with ISDN connection.
it's not so good to use 56kbps.

im so needy!

plz help me to install it.

---

