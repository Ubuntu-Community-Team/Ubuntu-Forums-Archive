---
title: "Setting up my wireless usb adapter (linksys)??"
date: 2012-03-11
forum: Networking &amp; Wireless
---

### Post by Trixxy on 2012-03-11
Hello everyone , Im Tixxy im new to the whole Ubuntu experiance but a freind of mine who takes a software programing class with me says that it would be the best processor for me. Well I listened and now im running Ubuntu 11.10. Sadly I do not have internet and with finals coming up loosing a day of reasearch time isnt going to help. I need to know what to do to setup my linksys wireless usb adapter, I have the CD aswell. Please help as soon as possible, thanks.

PS. If there is anything you need to know tell me how to find it and I will tell you :) #clueless

---

### Post by praseodym on 2012-03-11
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands with the stick plugged in:

```
lsusb
lsmod
iwconfig
rfkill list
```

---

