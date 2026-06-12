---
title: "Help a Noob Install a Driver"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by weazoe on 2009-05-26
I just installed an Encore PCI Wireless card. It works out of the box, but drops it's network connection almost daily. I'm guessing it's the driver so I downloaded it from the manufacturers site.

The 'read me' is really incoherent, so I was hoping someone could tell me how to get it installed. The folder is on my desktop, and here are the contents:
/home/chris/Desktop/DPO_RT2860_Linux_STA_V1.4.0.0_20071119/common
/home/chris/Desktop/DPO_RT2860_Linux_STA_V1.4.0.0_20071119/include
/home/chris/Desktop/DPO_RT2860_Linux_STA_V1.4.0.0_20071119/os
/home/chris/Desktop/DPO_RT2860_Linux_STA_V1.4.0.0_20071119/sta
/home/chris/Desktop/DPO_RT2860_Linux_STA_V1.4.0.0_20071119/tools
/home/chris/Desktop/DPO_RT2860_Linux_STA_V1.4.0.0_20071119/iwpriv_usage.txt
/home/chris/Desktop/DPO_RT2860_Linux_STA_V1.4.0.0_20071119/Makefile
/home/chris/Desktop/DPO_RT2860_Linux_STA_V1.4.0.0_20071119/README_STA

I'm using Ver. 9.2 with an AMD processor and an Asus MoBo

Thanks for any help,
Weaz

---

### Post by LinuxGuy1234 on 2009-05-26
Open a Terminal via Applications->Accessories->Terminal.

Get needed stuff for building the driver. Type this and then press enter:
```
sudo apt-get install gcc binutils linux-headers libc6-dev make
```

Now do this (the last command may ask for your password):
```
cd /home/chris/Desktop/DPO_RT2860_Linux_STA_V1.4.0.0_20071119
make
sudo make install
```

---

