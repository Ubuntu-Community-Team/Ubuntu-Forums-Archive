---
title: "internet connection help"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by killzoneman0 on 2006-06-15
i have a cable modem and am trying to get onto the internet with ubuntu.  After plugging the ethernet cable into both the modem and laptop, i am not sure what to do next. any help?

---

### Post by Noobie_Unbuntu on 2006-06-16
Try this if you don`t know what driver your card needs try searching on google for a compatible linux driver
Open a terminal, and Type:

Sudo gedit /etc/modules
type "insert your driver heer" without the qutes and save 

Go back to the terminal, and type: 

Sudo gedit/etc/modprobe.d/blacklist
add "blacklist tulip" without the qutes and save, then restart the system!



I hope it works for you as easy as it did for me!!

if that dosen`t work email me at [email]jake_edward@hotmail.com[/email] and I`ll try and help you 
Jamie

---

