---
title: "wifi problems again with lubuntu install"
date: 2013-05-22
forum: Networking &amp; Wireless
---

### Post by andyn11 on 2013-05-22
hi i had posted before about wifi problems on ubuntu and had it solved but now ive rebooted with Lubuntu  and have found the old thread that solved my problem but nothing seems to be working ...

i am using a USB wifi antena coz the internal wifi card is hard blocked and doesnt wanna play and now i have to figure out how to install my antenna again as it does not work from just plugging it in :( 

any help would be great


link to last (ubuntu) thread that solved my problem : [http://ubuntuforums.org/showthread.php?t=2125335&p=12556251#post12556251](http://ubuntuforums.org/showthread.php?t=2125335&p=12556251#post12556251)

---

### Post by praseodym on 2013-05-22
Did you compile the driver again for this kernel in use?

---

### Post by andyn11 on 2013-05-22
what do you mean by this?

---

### Post by praseodym on 2013-05-22
After a kernel upgrade you need to compile the driver again.

---

### Post by andyn11 on 2013-05-23
i have no idea wut that is so no i didnt

---

### Post by praseodym on 2013-05-24
Kernel upgrades come in automatically. Check
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
```

---

### Post by jediboaz on 2013-05-24
i also learned something here, thanks [**[COLOR=#000000]praseodym[/COLOR]**]("http://ubuntuforums.org/member.php?u=1411497")

---

