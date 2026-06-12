---
title: "Mandriva 2008.1 messes up my Vista clock"
date: 2008-05-03
forum: Mandriva/Mageia
---

### Post by Amorphous_Snake on 2008-05-03
I have a dual boot of Vista and Mandriva 2008.1. During installation, I chose that my system clock uses the local time and not UTC, but everytime I log into Mandriva, the clock is not right.

How can I fix this without using NTP servers?

---

### Post by Oldsoldier2003 on 2008-05-04
> **Amorphous_Snake said:**
> I have a dual boot of Vista and Mandriva 2008.1. During installation, I chose that my system clock uses the local time and not UTC, but everytime I log into Mandriva, the clock is not right.

How can I fix this without using NTP servers?

 What worked for Me was to install Mandriva using system clock uses UTC option then change the timezone to local. That was one of the reasons my initial experience with Mandriva 2008.1 wasn't as satisfactory as I had hoped leading me to eventually remove it from my multi boot system in favor of fedora.

---

### Post by Amorphous_Snake on 2008-05-04
But how can I fix an already present installation?

---

### Post by AdamWill on 2008-05-05
maybe if you toggle it to UTC and then back again, it'll help? you can do this via drakclock.

---

### Post by pelle.k on 2008-05-16
I got it solved by letting the settings be, (using localtime) and setting the time with;
```
date -s HH:MM
```
as root or with sudo naturally :)

---

