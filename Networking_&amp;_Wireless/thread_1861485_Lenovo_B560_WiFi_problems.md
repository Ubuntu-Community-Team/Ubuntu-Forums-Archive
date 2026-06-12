---
title: "Lenovo B560 WiFi problems"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by spennipc on 2011-10-15
Hi All,
I have the problem that my WiFi is not working with 11.10. I can not enable wireless. After lots of googeling I found this command:
*sudo rmmod -f acer-wmi*
Running this in a terminal immediately enabled wireless.
Problem is now how can I make it permanently so that it is running the command at start up? Or do I have to remove the acer-wmi from a config file? 
Oh, the wireless chip is a broadcom BCM4313.
Thanks for any help.

---

### Post by wildmanne39 on 2011-10-15
Hi, this is how to make it permanent.
```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```
would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by spennipc on 2011-10-16
> **wildmanne39 said:**
> Hi, this is how to make it permanent.
```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```
would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

Thank you very much. That solved the problem

---

### Post by wildmanne39 on 2011-10-16
Hi, your welcome!
Enjoy

---

