---
title: "Wifi Won't Reconnect After Sleep/Suspend/Hibernate"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by Geothermal123 on 2012-10-29
I run 12.04 and I cannot get my wifi to reconnect after I resume from suspending or sleeping or hibernating whatever you call it. I tried putting SUSPEND_MODULE="iwlwifi" in the /etc/pm/config.d/config file, but that doesn't work. I really want this fixed. Help Please.

---

### Post by Geothermal123 on 2012-10-30
Bump

---

### Post by Geothermal123 on 2012-10-30
Hey. If you are having this problem and using SUSPEND_MODULES="iwlwifi" doesn't work for your computer
with INTEL wireless, put 

options iwlwifi bt_coex_active=0
in a file you make in
in /etc/modprobe.d/iwl.conf.

I found this posted somewhere else. Hopefully this works for you.

---

### Post by Geothermal123 on 2012-10-30
Actually, that did not fix the problem. I just went to the power settings and set it not to suspend when the lid is closed. Works for me.

---

### Post by raydar on 2013-06-27
Anybody ever figure this out?  I'm having this problem with Ubuntu Studio 13.04 (xfce) on an HP Pavillion dv7.

---

### Post by Toz on 2013-06-27
> **raydar said:**
> Anybody ever figure this out?  I'm having this problem with Ubuntu Studio 13.04 (xfce) on an HP Pavillion dv7.

Do you have the same module (iwlwifi)? I noticed a typo in post #3 and just corrected it. You might want to give it another try.

---

### Post by raydar on 2013-06-28
I do appear to have it running:
```
$ ps aux | grep iwlwifi
root       813  2.1  0.0      0     0 ?        S    07:57  16:54 [irq/50-iwlwifi]
root       829  0.0  0.0      0     0 ?        S<   07:57   0:00 [iwlwifi]
dejah     6518  0.0  0.0   9440   956 pts/0    S+   21:09   0:00 grep --color=auto iwlwifi

```
But I jumped the gun in wondering about the fix in post #3: The fix in post #1 worked for me.

But thanks anyway for so quickly replying to help!
Looks like I do have it.

---

