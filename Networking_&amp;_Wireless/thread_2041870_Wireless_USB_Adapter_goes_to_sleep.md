---
title: "Wireless USB Adapter goes to sleep"
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by Cybrknight on 2012-08-13
Hello everyone,

I am very new to ubuntu and Linux. I installed the 12.04 server on my desktop computer with a Belkin USB N Wireless adapter, and by my surprise it worked. I can connect to the Internet with no problem. I didn't even have to install a driver for it.

Here is the problem though. Unless I go to the console and login, the network card goes down or to sleep if I don't connect for a while. In other words, after a few hours of non-use, if I try to ping it or attach to it with ssh, I can't, until i go to the server and log-in.

What could be the problem?

Thanks,
CK

---

### Post by praseodym on 2012-08-13
Hi,

please show the outputs of:

```
lsusb
lsmod
iwconfig
```
Maybe the driver is unloaded during "suspend/hibernate"?

---

### Post by Cybrknight on 2012-08-16
> **praseodym said:**
> Hi,

please show the outputs of:

```
lsusb
lsmod
iwconfig
```
Maybe the driver is unloaded during "suspend/hibernate"?

Thank you so much for your help. I decided to connect the home server up to my router with a cable. I now don't get any problems.

Thanks again,
CK

---

