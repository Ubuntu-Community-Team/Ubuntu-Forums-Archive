---
title: "Wireless Card Intel 82562V-2 Not Working"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by msharif911 on 2010-02-02
Hi. I have a Dell Vostro 200 with the above wireless card in it and I cant get it to work.

I have been on Intel's website and downloaded e1000-8.0.18 and installed as the instructions. But it is still greyed out on the Network Manager. 

I have just installed Ubuntu Desktop the latest current version. So apologies for being a newbie.

---

### Post by chili555 on 2010-02-02
Let's see if the kernel has any insights. Please reboot and run, from a terminal:```
dmesg | grep e1000
```Please post the result.

Are you sure that e1000 is the correct driver? I suspect it's e1000[COLOR="Red"]e[/COLOR]. May we please see:```
lspci -nn | grep Ethernet
```Thanks.

---

