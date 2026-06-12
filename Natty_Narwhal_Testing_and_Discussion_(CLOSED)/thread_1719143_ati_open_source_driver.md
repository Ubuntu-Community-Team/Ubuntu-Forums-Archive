---
title: "ati open source driver"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by xgt001 on 2011-04-01
hey everyone
i have ati m6370 radeon and its rocking in 11.04 without any prop driver :D :D unlike in previous releases :D
but i have only one issue.... my fan wouldnt keep quite without the ati prop driver.... my laptop is quite noisy :(
is there any way to fix it without installing ati prop driver???

---

### Post by dumbo on 2011-04-01
> **xgt001 said:**
> hey everyone
i have ati m6370 radeon and its rocking in 11.04 without any prop driver :D :D unlike in previous releases :D
but i have only one issue.... my fan wouldnt keep quite without the ati prop driver.... my laptop is quite noisy :(
is there any way to fix it without installing ati prop driver???

This might work (if it works, it would repeating after every reboot - I think it can done automatically via sysctl somehow).

sudo echo "low" > /sys/class/drm/card0/device/power_profile

---

### Post by xgt001 on 2011-04-01
> **dumbo said:**
> This might work (if it works, it would repeating after every reboot - I think it can done automatically via sysctl somehow).

sudo echo "low" > /sys/class/drm/card0/device/power_profile
hey thanks a ton that worked :) :D
but if u tell how to run that script automatically on every boot i would really be greatful :D

---

### Post by lucazade on 2011-04-01
> **xgt001 said:**
> hey thanks a ton that worked :) :D
but if u tell how to run that script automatically on every boot i would really be greatful :D

you can try to put it in
/etc/rc.local

before "exit 0"

or a sysctl option would be better

---

### Post by xgt001 on 2011-04-03
> **lucazade said:**
> you can try to put it in
/etc/rc.local

before "exit 0"

or a sysctl option would be better

pls forgive my lack of knowledge and foolishness

can u explain wat sysctl option refers to in a bit more detail...??

---

### Post by lucazade on 2011-04-03
> **xgt001 said:**
> pls forgive my lack of knowledge and foolishness

can u explain wat sysctl option refers to in a bit more detail...??

/etc/sysctl.conf - Configuration file for setting system variables
here you can put kernel parameters and other system-wide settings

I don't know which is the correct option (and if exists) to fix your issue instead of using this command:
echo "low" > /sys/class/drm/card0/device/power_profile

you should find some guide of sysctl available options.

---

