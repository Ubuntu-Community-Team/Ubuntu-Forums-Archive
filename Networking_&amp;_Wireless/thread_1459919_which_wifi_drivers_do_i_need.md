---
title: "which wifi drivers do i need?"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by zander1013 on 2010-04-22
hi,

i just installed ubuntu studio but i don't think it includes wifi drivers by default.

the laptop i am using has worked well using vanilla ubuntu 9.10 including wifi.

i just need to know what driver packages to install.

please advise.

---

### Post by unmole on 2010-04-22
As I said [here]("http://ubuntuforums.org/showthread.php?t=1459909")
,the driver which you need to use will depend on the kind of hardware you have. If you tell us what hardware you have, we might be able to help you.
To find out which WiFi card you have, open a terminal (Applications>Accesories>Terminal) and type ```
lspci
``` and hit enter. Post the output here.

---

### Post by zander1013 on 2010-04-22
ty for the assist umole.

installing gnome network manager and rebooting a few times turned the trick.

---

