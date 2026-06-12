---
title: "Wireless does not work after &quot;11.10&quot; install on Dell inspiron 640 m"
date: 2011-10-21
forum: Networking &amp; Wireless
---

### Post by mixo_010 on 2011-10-21
Wireless did not work after install 11.10 and  it did not work. Wireless card is broadcom STA . Installed proprietary STA  driver,still does  not work. I have not seen any other fixes specific to 11.10.

---

### Post by varunendra on 2011-10-21
Hi, and welcome to the forums :)

Please open a terminal and post outputs of these commands:
```
sudo lshw -C network
lsmod
cat /etc/modprobe.d/blacklist.conf
```

Please wrap each set of outputs in separate [noparse]```
..and..
```[/noparse] tags. Just click on the **#** symbol at the top of edit box to auto-generate those tags and paste the output in-between the generated tags.

---

