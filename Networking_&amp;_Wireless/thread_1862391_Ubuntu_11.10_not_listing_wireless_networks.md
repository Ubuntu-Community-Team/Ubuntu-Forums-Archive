---
title: "Ubuntu 11.10 not listing wireless networks"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by Forever Delayed on 2011-10-16
Please help, just updated to Oneiric Ocelot the other day and it's not picking up any wireless networks. Went to install additional drivers but the Broadcom STA wireless driver is already installed and in use. If you need any more information just give me the commands to run and I'll post the results here.

---

### Post by wildmanne39 on 2011-10-16
Hi, please try this, you may have to restart your computer.
```
sudo su
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
exit
```
Thank you

---

### Post by Forever Delayed on 2011-10-17
> **wildmanne39 said:**
> Hi, please try this, you may have to restart your computer.
```
sudo su
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
exit
```
Thank you

Yes that worked perfectly. Would you mind explaining what that did? Just for my own knowledge, thanks.

---

### Post by wildmanne39 on 2011-10-17
Hi, that makes sure the bcma driver does not load and allows the one you need to load, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

