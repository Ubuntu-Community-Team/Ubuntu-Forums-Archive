---
title: "Wireless driver install root password"
date: 2012-01-24
forum: Networking &amp; Wireless
---

### Post by jerdrb on 2012-01-24
Hey guys, im stumped, im attempting to get this wireless driver for ubuntu 10.04 to work. Im installing with an sh file given in the driver folder yet it keeps asking for a root password in terminal. I am confused though due to this being a completely fresh install and nothing else has been done to it besides attempting to install. Its not the gui sudo password which is the username but it asks for the pw for root in terminal. I have tried everything from entering nothing, the user password, made sure the account was in root permissions, typing in root as the password. Nothing works. can anyone help?? This has happened with the same card drivers on different flavors of limux such as fedora, and another version of ubuntu 11.0. Can anyone help? Ive provided a link to the driver here [http://file.encore-usa.com/misc/product/ENUWI-1XN4X/RTL8192CU_linux_v3.1.2590.20110922.zip](http://file.encore-usa.com/misc/product/ENUWI-1XN4X/RTL8192CU_linux_v3.1.2590.20110922.zip)

Thanks.

---

### Post by MrStill on 2012-01-25
Have you tried running the install as root, not using sudo?

---

### Post by jerdrb on 2012-01-25
very new to linux, could you explain how to do this with a pre written sh install file?

---

### Post by lisati on 2012-01-25
As outlined here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

```
sudo -i
```

---

### Post by jerdrb on 2012-01-25
Fixed! i had to replace every su command with sudo su, then it asked my user account pw, and installed the driver correctly! thanks for help guys

---

