---
title: "No wireless connection detected with Ubuntu 13.04 64 bits"
date: 2013-06-03
forum: Networking &amp; Wireless
---

### Post by ahmed11ber on 2013-06-03
[COLOR=#000000]Hello,
I have a laptop Hp pavilion g6 ek-2220 with windows 7  64 bits pre-installed, I'm trying to install in dual boot alongside with my windows 7, [/COLOR][COLOR=#000000]when I've tried Ubuntu 13.04 amd 64 bits it has not detected my wireless connection but when [/COLOR][COLOR=#000000]I have tried Ubuntu 13.04 32 bits version, it has detected my wireless connection, Should I install the 64 bits version even, it has not detected my wireless card ?  

I will appreciate  an assistance to solve this problem[/COLOR]

---

### Post by praseodym on 2013-06-03
Please show the terminal (CTRL+ALT+T) outputs of these commands with 64bit Ubuntu:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

