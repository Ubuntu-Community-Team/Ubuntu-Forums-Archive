---
title: "BSNL WLL Phone Internet connectivity Problem"
date: 2009-08-17
forum: Networking &amp; Wireless
---

### Post by netcrack on 2009-08-17
I have BSNL WLL Phone(India)

I am having problem in connecting internet in Ubuntu 9.04.

part of lsusb result

```
Bus 003 Device 003: ID 0451:3410 Texas Instruments, Inc. TUSB3410 Microcontroller
```

dmesg result at the end

```
TI USB 3410 1 port adapter converter now attached to ttyUSB0
```

wvdial.conf file
```

[Dialer bsnl]
Modem = /dev/ttyUSB0
Baud = 230400
Phone = #777
Init1 = ATZ
Stupid Mode = 1
Dial Command = ATDT
Username = ****
Password = ******
PPPD Options = lock noauth refuse-eap refuse-chap refuse-mschap nobsdcomp nodeflate 
```

While dialing using wvdial im getting this error message

```

--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: Input/output error
--> Cannot open /dev/ttyUSB0: Input/output error
--> Cannot open /dev/ttyUSB0: Input/output error

```

Anyone has solution to this problem.

Please help me.

---

### Post by netcrack on 2009-08-20
Please some one help me

I want to access internet in my ubuntu system.

---

### Post by zot171 on 2009-08-20
Hey, I dont really know if this is your problem, but I had to set my Palm Centro to modem mode as device /dev/ttyACM0 to connect to the internet with it. it could be a hardware difference between our phones, but that worked for me

---

### Post by GeorgeVita on 2009-08-20
Hi **netcrack**,
searching this forum for 'TUSB3410 OR BSNL' ([http://ubuntuforums.org/search.php?searchid=63207814](http://ubuntuforums.org/search.php?searchid=63207814)) has a lot of hits.

As I remember user 'virginbala' managed to connect a similar phone/modem at:
[http://ubuntuforums.org/showthread.php?p=7690623#post7690623](http://ubuntuforums.org/showthread.php?p=7690623#post7690623)
Review this thread and/or post him a question.

Another working post (I am not sure that is the same phone/modem):
[http://ubuntuforums.org/showthread.php?p=7816175#post7816175](http://ubuntuforums.org/showthread.php?p=7816175#post7816175)
Regards,
George

---

### Post by netcrack on 2009-08-31
I installed fedora 11 and i can connect to internet using the same connection without any problem.
Any body tell why its not working in Ubuntu 9.04.
:(

---

### Post by kharat on 2009-08-31
> **netcrack said:**
> I installed fedora 11 and i can connect to internet using the same connection without any problem.
Any body tell why its not working in Ubuntu 9.04.
:(

hi,
I had been able to connect using WLL but MTNL, and in suse. Below link might be of some help.

[http://forums.opensuse.org/archives/sf-archives/archives-network-internet/archives-wireless-networking/339254-cdma-1x-2000-fwt-mtnl-mumbai-unable-browse.html](http://forums.opensuse.org/archives/sf-archives/archives-network-internet/archives-wireless-networking/339254-cdma-1x-2000-fwt-mtnl-mumbai-unable-browse.html)

vikas

---

### Post by netcrack on 2009-11-04
I installed Ubuntu 9.10, now it connects to Internet without any problem :D

---

