---
title: "broadcom and ubuntu, any changes from 2005?"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by axima on 2010-02-14
searching broadcom ubuntu in google results in a thread that is five years old. has there been any changes? i still cannot set up my 4 year old laptop's wireless to run and i have just about given up. why should i spend my valuable time getting something that is suppose to work when i could just run windows 7 and be done with it. now this is coming from a 4 year old laptop, has anything changed? i want to hear yes but i know that wireless support in linux is absolutely atrocious and sickening, even more than 4 years ago since wireless is now the norm and linux refuses to give proper attention to wireless drivers.

---

### Post by northd_tech on 2010-02-14
My Broadcom is actually pretty well supported under Linux (4321AG, except Linux calls it a 4328 ).

Can you run the following commands from a terminal and post the results here so that we can see what kind of hardware you are working with?

```
lspci

lsusb

lsmod

uname -a

sudo lshw -C network 

ifconfig

iwconfig
```

---

