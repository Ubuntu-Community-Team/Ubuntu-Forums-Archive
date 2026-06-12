---
title: "Ubuntu 10.10 alpha still showing Ubuntu 10.04 LTS"
date: 2010-06-17
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Winalways on 2010-06-17
I upgraded from Ubuntu 10.04 LTS to 10.10 alpha 1 as per the instructions given in [http://www.ubuntu.com/testing/maverick/alpha1](http://www.ubuntu.com/testing/maverick/alpha1) yesterday. I carried out all the processes thereafter, it downloaded some 381 MB, installed packages for one hour or so and even demanded a restart. Later when I checked "About Ubuntu", its still showing 'you are using Ubuntu 10.04 LTS!'

When I try to use the "update-manager -d" today, but it says the package information was updated a day ago!

Please help!

---

### Post by howefield on 2010-06-17
What's the output of the terminal command.

```
cat /etc/lsb-release
```

---

### Post by overdrank on 2010-06-17
Moved to Maverick Meerkat Testing and Discussion :)

---

### Post by Winalways on 2010-06-17
[QUOTE=howefield;9476338]What's the output of the terminal command.

[FONT=monospace]DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu maverick (development branch)"
[/FONT]

---

### Post by Starks on 2010-06-17
> **Winalways said:**
> I upgraded from Ubuntu 10.04 LTS to 10.10 alpha 1 as per the instructions given in [http://www.ubuntu.com/testing/maverick/alpha1](http://www.ubuntu.com/testing/maverick/alpha1) yesterday. I carried out all the processes thereafter, it downloaded some 381 MB, installed packages for one hour or so and even demanded a restart. Later when I checked **"About Ubuntu"**, its still showing 'you are using Ubuntu 10.04 LTS!'

When I try to use the "update-manager -d" today, but it says the package information was updated a day ago!

Please help!
About Ubuntu is worthless. Use Administration>System Monitor>System.

---

