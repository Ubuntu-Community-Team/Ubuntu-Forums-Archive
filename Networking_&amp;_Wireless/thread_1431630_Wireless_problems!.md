---
title: "Wireless problems!"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by GeoH2102 on 2010-03-16
Hi everyone, first post here, I'm a new Ubuntu user!

I've just installed Ubuntu 9.10, straight from the homepage. All went fine, everything appears to be running smoothly.. but I can't get the wireless working!

All it does is ask for the WPA/WPA2-Personal key repeatedly. I know I've got the code right, as I've typed it whilst "Show Characters" is on multiple times. Every time I enter it, the networking icon looks as though it's working, and then after a moment it'll ask me again.

Any help would be much appreciated!

---

### Post by wojox on 2010-03-16
Open you terminal and what does this output when run:

[CODE]lspci | grep -i net/CODE]

---

### Post by GeoH2102 on 2010-03-16
The commands gave me the following:

```
geo@geo-laptop:~$ lspci | grep -i net
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

```

EDIT: Don't know if this is relevant, but I'm dual-booting with Windows 7.

---

### Post by bkratz on 2010-03-17
> **GeoH2102 said:**
> The commands gave me the following:

```
geo@geo-laptop:~$ lspci | grep -i net
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

```

EDIT: Don't know if this is relevant, but I'm dual-booting with Windows 7.

Apparently you are not alone. You might want to get involved with this current thread

[http://ubuntuforums.org/showthread.php?t=1421783&highlight=3945ABG](http://ubuntuforums.org/showthread.php?t=1421783&highlight=3945ABG)

See post 15 specifically, it appears that a recent update hurt several users, perhaps one of them will have additional information..

---

### Post by GeoH2102 on 2010-03-19
Just tried to install the beta1 client for Lucid today, still no joy :(

---

