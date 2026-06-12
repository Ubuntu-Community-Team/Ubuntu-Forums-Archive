---
title: "i am not able to connect internet with wifi on ubuntu10.10"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by harmohit on 2011-01-04
**I am using bsnl modem AN1020-21 ,it has both ethernet and wifi availiability , i am not able to connect internet with wifi but working with lan cable....am using ubuntu 10.10...plz help**

---

### Post by PatchesTheCaveman on 2011-01-04
Hi harmohit.  Happy New Year!

To figure out what's going on with your WiFi, we need to collect some diagnostic information.  To do that, go to Applications > Accessories > Terminal on your top panel.  In the black box that appears, type each of the following commands, then press Enter:
```
lspci -vnn
lshw -C network
ifconfig -a
uname -r
sudo iwconfig
```

The last command will ask you for your password.  Type it in and press Enter.  Note that it won't show stars or dots or anything but it will still work.

Once you've run all those, highlight all the output and then copy and paste it into a reply to this thread.  We'll take a look at it and see what we can do.

---

