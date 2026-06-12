---
title: "Wireless works until restart to complete update"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by caricc on 2010-10-22
Here is my problem: I am using ubuntu 10.10 64 bit installed on a HP tx2 1274nr laptop. I can get my wireless to work on both the Broadcom B43 wireless driver and the Broadcom STA wireless driver. Though only one can be active at a time. 

My problem lies in I can activate either driver until I reboot the laptop. then it becomes inactive. 

Is there a fix for this problem. I would like to have my wireless active after restarting. 

Thanks in advance.

---

### Post by Ayuthia on 2010-10-23
> **caricc said:**
> Here is my problem: I am using ubuntu 10.10 64 bit installed on a HP tx2 1274nr laptop. I can get my wireless to work on both the Broadcom B43 wireless driver and the Broadcom STA wireless driver. Though only one can be active at a time. 

My problem lies in I can activate either driver until I reboot the laptop. then it becomes inactive. 

Is there a fix for this problem. I would like to have my wireless active after restarting. 

Thanks in advance.

It sounds like you need to blacklist one of the options because both drivers are loading so neither are working.  The easy one to do first would be to block the STA driver:
```

echo 'blacklist wl' |sudo tee -a /etc/modprobe.d/blacklist-wl.conf

```
This will create a file called blacklist-wl.conf that will contain the blacklist information.  What this does is prevent the wl (Broadcom STA) driver from loading when the system starts up.

---

### Post by caricc on 2010-10-23
Ok, that setup the blacklist. But now the Broadcom B43 drivers are not activated when the system is reloaded.

---

### Post by Ayuthia on 2010-10-25
> **caricc said:**
> Ok, that setup the blacklist. But now the Broadcom B43 drivers are not activated when the system is reloaded.

Ok.  Let's try loading the b43 module:
```

echo b43|sudo tee -a /etc/modules

```
This will add the b43 module to the startup list.  Hopefully that will do it.

---

### Post by caricc on 2010-10-26
That worked. Great!. Thanks for the help.

---

