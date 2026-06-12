---
title: "Intel 3945 not working in 10.10"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by PerfectEllipses on 2010-12-02
A couple of weeks ago, I installed kubuntu 10.10 on my laptop and my wireless card has not worked ever since. It was fine under 10.04. 

lspci:

```
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```rfkill list:

```
0: acer-wireless: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
1: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
2: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```Any help at all would be greatly appreciated! I really don't want to be forced to give up 10.10. 

Thanks!

---

### Post by judedawson on 2011-05-01
Hi PerfectEllipses,

I have a somewhat similar issue (Ref. [http://ubuntuforums.org/showthread.php?t=1745588](http://ubuntuforums.org/showthread.php?t=1745588)).

Did you manage to solve the problem you reported?

Thanks.

From,
Jude

---

### Post by judedawson on 2011-05-02
Hi there,

I have a somewhat similar problem (Ref. [http://ubuntuforums.org/showthread.php?t=1745588](http://ubuntuforums.org/showthread.php?t=1745588))

Did you manage to solve the problem you reported?

Thanks.

---

### Post by PerfectEllipses on 2011-05-02
Unfortunately, no. I ultimately ended up dual booting with 10.04 and primarily using 10.04. I still haven't found anyone with better solutions.

---

### Post by judedawson on 2011-05-02
Oh dear... 

For someone who's been on the GNOME desktop environment for almost 2 years, I must say that Kubuntu looks and feels really nice and relatively easy to use. It's a pity that the wireless network connection is acting up.

Here's hoping someone will come to our rescue :)

From,
Jude

---

### Post by judedawson on 2011-05-05
Hi, have you tried posting your query on [http://kubuntuforums.net](http://kubuntuforums.net) ? I just discovered today there was one (duh...). 

I've posted my query in their forums & have my fingers crossed. 

Give it a shot.

---

### Post by judedawson on 2011-05-16
Hi PerfectEllipses, 

I've managed to solve my problem with the wireless connection (Ref. [http://ubuntuforums.org/showthread.php?t=1745588&page=2](http://ubuntuforums.org/showthread.php?t=1745588&page=2)). Perhaps it may give a clue to fix yours.

Cheers :D

From,
Jude

---

