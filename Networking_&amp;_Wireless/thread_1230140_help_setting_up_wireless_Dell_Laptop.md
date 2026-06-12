---
title: "help setting up wireless Dell Laptop"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by e mac on 2009-08-03
I have a Dell laptop wired to my wireless linksys router working fine, but when I try to go wireless I cannot view network connections, I only see " Intel pro/wireless 2915 ABG network connection" . I also have another laptop Toshiba, using the same wireless linksys router wired and wireless and working fine. On that laptop when I clicked on View Network connection I saw at least 15 connection including my linksys. My question is why can't I see these on my Dell Laptop?.

---

### Post by Crafty Kisses on 2009-08-03
Go into a Terminal **(Applications->Accessories->Terminal)** and type the following commands:
```
lsusb
lspci
```
What are the results of those commands?

---

