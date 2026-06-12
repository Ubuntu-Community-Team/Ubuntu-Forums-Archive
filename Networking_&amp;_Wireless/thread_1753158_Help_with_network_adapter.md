---
title: "Help with network adapter"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by RFXCasey on 2011-05-08
Hello, I need some help setting up a TRENDnet TE100 PCIWIN card on an install of Xubuntu 10.04. I installed the OS and then noticed it wasn't picking up the onboard NIC card so I installed this TRENDnet PCI card I had laying around. I typed in ifconfig -v but all it shows is a lo adapter. If I need to recompile the kernel with the proper module for the card I don't know what the module is and have never compiled a kernel before. Help please, this machine is going to be my testbed for learning Linux in text only format and I'm not getting off to a great start. The GUI is installed just for back up but it is of little use in solving my issue so far. Thanks.

---

### Post by chili555 on 2011-05-08
Please open a terminal and run and post:```
lspci -nn
```Thanks.

---

