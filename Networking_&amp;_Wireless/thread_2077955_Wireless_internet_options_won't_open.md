---
title: "Wireless internet options won't open"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by Murray825 on 2012-10-29
I tried to open the wireless internet options so i could put in the wpa key because it didn't prompt me for it but the options wouldn't open

---

### Post by Murray825 on 2012-11-03
Bump

---

### Post by Hadaka on 2012-11-03
Hi, what device?..your router or the computer
and what version of ubuntu? Please provide more details.

---

### Post by Murray825 on 2012-11-03
Ubuntu Version: 12.10 
Router: Arris WTM552G (However I was trying to connect to a Belkin router at a friends house when network options quit working)
Computer Model: Dell Inspiron 14r (N4110)

The internet status indicator on the top bar isn't showing either

---

### Post by Hadaka on 2012-11-03
Hi, is there a triangular type symbol in the upper right corner
next to the envelope? And what exactly commands  did you input?

---

### Post by Murray825 on 2012-11-03
No there is not and I didn't enter any commands. I went to the internet indicator to try to connect to the router and then it dissapeared, wouldn't prompt me for the password, and then options wouldn't work. It's been almost a week

---

### Post by Hadaka on 2012-11-03
Hi, try this..

```
/etc/init.d/networking restart 
```

---

### Post by Murray825 on 2012-11-03
> **Hadaka said:**
> Hi, try this..

```
/etc/init.d/networking restart 
```

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service networking restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop networking ; start networking. The restart(8) utility is also available.
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.148" (uid=1000 pid=4854 comm="stop networking ") interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
christiaj@christiaj-Dell-System-Inspiron-N4110:~$

---

### Post by Murray825 on 2012-11-03
> **Murray825 said:**
> Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service networking restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop networking ; start networking. The restart(8) utility is also available.
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.148" (uid=1000 pid=4854 comm="stop networking ") interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
christiaj@christiaj-Dell-System-Inspiron-N4110:~$

Idk why but it replaced things with 8) s

---

### Post by Murray825 on 2012-11-09
Bump

---

### Post by Murray825 on 2012-11-18
Bump

---

