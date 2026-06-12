---
title: "Wireless Network"
date: 2012-01-08
forum: Networking &amp; Wireless
---

### Post by faixan on 2012-01-08
Hi,

i want to create a wireless network(protected) using my laptop's wireless so that other devices(other laptops and cellphones) could connect to internet through my laptop, while i connect directly through ethernet cable.

i've Dell Inspiron 1545 with a
```

:~ $lspci -vnn | grep 14e4
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

how can i do this?

---

### Post by faixan on 2012-01-09
someone? any one? :s


i'm using ubuntu maverick. i don't want any DHCP or DNS settings to be enabled, i just want a password protected network that would enable other devices to directly connect to internet without having to setup proxy settings or any thing like that.

---

### Post by josephmills on 2012-01-09
> **faixan said:**
> Hi,


:~ $lspci -vnn | grep 14e4
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g[COLOR="Red"] LP-PHY[/COLOR] [14e4[COLOR="Green"]:4315][/COLOR] (rev 01)






Please take a moment to look over this [How to fix your wifi post #44 ](http://ubuntuforums.org/showthread.php?t=1748245&page=5) hope that this helps 
Joseph

---

### Post by faixan on 2012-01-09
> **josephmills said:**
> Please take a moment to look over this [How to fix your wifi post #44 ](http://ubuntuforums.org/showthread.php?t=1748245&page=5) hope that this helps 
Joseph

hi, thanks for referring me, but from what i see and know, my wireless is working pretty fine, it's creating networks, even detecting networks, don't really have a wireless network to which i'd know the password to so that i could check the actual connection, but what i want to do here is to create own network and share the internet on wireless from the internet that i'm using on my ethernet cable.

---

