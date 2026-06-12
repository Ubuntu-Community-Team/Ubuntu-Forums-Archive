---
title: "ndiswrapper dependancy error on ubuntu 12.04 precise"
date: 2013-05-14
forum: Networking &amp; Wireless
---

### Post by TheTobi213 on 2013-05-14
I have a fresh, unupdated installation of ubuntu 12.04 precise. I did a bit of digging to try and get ubuntu to use my Belkin N600 DB so it can connect to the internet so it can update. I came across the idea of using ndiswrapper. I got an installation of it and tried to install it when the error 'dependency is not satisfiable: dkms (>=2.1.0.0), and now i'm stuck. is there any way to solve this issue without having to go to a wired internet connection to get my computer to use the belkin?

---

### Post by praseodym on 2013-05-14
Please show the outputs of
```

lsusb
lsmod
iwconfig
rfkill list
```

---

