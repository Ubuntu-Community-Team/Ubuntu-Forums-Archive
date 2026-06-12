---
title: "disable power management with bcma?"
date: 2012-03-19
forum: Networking &amp; Wireless
---

### Post by miatawnt2b on 2012-03-19
I think I am having an issue with power management and the bcma driver on my broadcom BCM943225 chipset.

Can someone point me to the direction of disabling power management on the wifi?

Thanks,
-J

---

### Post by miatawnt2b on 2012-03-20
bump

---

### Post by wildmanne39 on 2012-03-20
Hi, this is how to disable power management.
```
gksudo gedit /etc/pm/power.d/wireless
```
(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following:
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
```
above exit0, then save gedit, close and reboot.
Thanks

---

### Post by miatawnt2b on 2012-03-21
thanks, I ended up blacklisting all of the broadcom drivers and compiling wl from the broadcom site.
-J

---

### Post by wildmanne39 on 2012-03-21
Hi, you know that still has nothing to do with power management right?
Thanks

---

### Post by miatawnt2b on 2012-03-21
Yes, though I wasn't clear, the wl driver doesn't have the same low power/bandwidth issues that the bcma driver seems to.

-j

---

### Post by wildmanne39 on 2012-03-21
I am glad you have your issue fixed please use thread tools at the top of the page to mark the thread solved.
Thanks

---

