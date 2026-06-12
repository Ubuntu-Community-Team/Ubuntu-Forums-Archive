---
title: "Slow Internet Connection on Dell Inspiron N7110"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by cmmd2003 on 2011-09-22
Hey guys,

I've recently purchased a Dell Inspiron n7110. It is connected to the router in my house via a wireless connection. 

The problem is that using the internet is painfully slow. 

I would blame the router, except that there are three other laptops connected to it, and they're all fine. 

Any ideas as to what the problem may be?
It's really bugging me. 

Thanks.

---

### Post by varunendra on 2011-09-24
Hi cmmd2003, and welcome to the forums!

Please open a terminal, and enter these commands one-by-one and post their outputs (after browsing a couple of minutes via wifi connection):
```

uname -a
sudo lshw -C network
ifconfig
iwconfig
lsmod
cat /etc/resolv.conf
ping -c 4 google.com
```

Wrap each set of outputs in [noparse]```
..and..
```[/noparse] tags to preserve formatting and easier readability. To do so, just click the **# **symbol at the top of edit-box and copy-paste the output between the generated tags.

---

