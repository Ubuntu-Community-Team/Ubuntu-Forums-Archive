---
title: "wireless doesnt autoconnect for all users - please help"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by tehpwnerer1918 on 2010-11-17
I work at a school and we are experimenting with Linux. We are using 10.10 and are connected to AD using Likewise. My problem is that students cannot log in unless the laptops are connected with a wire, as for some reason either the wireless is not active at the login screen or is not connected. Is there a way to keep it on so students can log in as they need network access to log in? Thanks.

---

### Post by tehpwnerer1918 on 2010-12-01
I really need help with this. Anyone have a clue?

---

### Post by Davste on 2010-12-01
Hi,

When you say the WiFi is not active, you mean the wireless symbol at the top right has a red exclamation mark?

Try posting the results of

```
iwconfig
```


and 

```
ifconfig
```

so we can look deeper into this.

---

### Post by Hippytaff on 2010-12-01
also 
```

lshw -C network

```
:-)

---

