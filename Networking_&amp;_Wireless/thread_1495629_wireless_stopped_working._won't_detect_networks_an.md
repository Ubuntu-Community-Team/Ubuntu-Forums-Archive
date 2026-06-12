---
title: "wireless stopped working. won't detect networks anymore"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by akh2103 on 2010-05-28
Hi--

my wireless was working well in ubuntu. now it won't detect networks anymore. 

the output of iwconfig is 
no wireless extensions

Any suggestions on what to do? I can't find any previous posts that have answered this

Thanks!

Abe

---

### Post by akh2103 on 2010-05-28
i just ran sudo ifconfig wland0 up. 

output: error while getting interface flags: no such device

any idea what is going on?

---

### Post by akh2103 on 2010-05-28
My hardware is an Acer Aspire one with Broadcom BCM4312 802.11b/g
I am using ubuntu 9.1

everything was up and running and suddenly stopped

---

### Post by marcottebj on 2010-05-28
I assume you rebooted

---

### Post by Darkness Des on 2010-05-28
This probably has nothing to do with anything, but it's supposed to be
```
sudo ifconfig wlan0 up
```
There's no D in WLAN.

---

### Post by akh2103 on 2010-05-28
yep. I rebooted and dropped the D in LAN. Any ideas what might be up? I think it is not detecting the wireless card for some reason but it is strange because it was all working fine before.

Abe

---

### Post by akh2103 on 2010-05-28
is there any reason not to update to version 10.04 and cross my fingers?

---

### Post by akh2103 on 2010-06-03
upgrading to ubuntu 10.04 did solve it, in case others run across this same issue.

anybody know why this happened?

---

