---
title: "Disable Wireless Card"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by booah on 2010-09-24
Hey,

Just installed Ubuntu 10.4 and unfortunately it installed the driver for the very poor, built in wireless card that came with the pc. On 9.10 I used a wireless usb dongle to connect to the network which worked great. The built in wireless card is getting preference however and it keeps dropping the connection and I cant even open a webpage. Is there some way i can just disable the wireless card and stick to the usb connection?

Thanks,

---

### Post by booah on 2010-09-25
I think blacklist would do the trick. Here is my network details
*-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: e0:91:53:27:5e:bd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 ip=192.168.1.101 latency=0 multicast=yes wireless=802.11bgn
       resources: irq:19 ioport:e800(size=256) memory:febfc000-febfffff

So i open the blacklist file :

sudo gedit /etc/modprobe.d/blacklist

given the wireless info what is the argument that follows blacklist?

Would it be possible to just remove the rtl819xSE either? 
thanks

---

### Post by chili555 on 2010-09-25
The file should be named /etc/modprobe.d/blacklist[COLOR="Red"].conf[/COLOR]. Please add your blacklist entry to the existing file named /etc/modprobe.d/blacklist.conf. I am skeptical that the driver is named rtl819xSE. Did you install it with ndiswrapper? Or what? You can find the real name of the driver with:```
lsmod | grep 819
```That will list any loaded modules with '819' in the name. Blacklist it by adding to the /etc/modprobe.d/blacklist.conf file:```
blacklist r819whateveryoufound
```Proofread carefully, save and close the text editor. Upon reboot, you should be set.

---

### Post by booah on 2010-09-25
> **chili555 said:**
> The file should be named /etc/modprobe.d/blacklist[COLOR=Red].conf[/COLOR]. Please add your blacklist entry to the existing file named /etc/modprobe.d/blacklist.conf. I am skeptical that the driver is named rtl819xSE. Did you install it with ndiswrapper? Or what? You can find the real name of the driver with:```
lsmod | grep 819
```That will list any loaded modules with '819' in the name. Blacklist it by adding to the /etc/modprobe.d/blacklist.conf file:```
blacklist r819whateveryoufound
```Proofread carefully, save and close the text editor. Upon reboot, you should be set.

Chili thanks a million. Great help!

you were right about the driver name too. When i installed ubuntu it automatically installed the wireless card but it got a low signal detection so I use a usb wireless dongle to connect to the network.

#wireless network card (disabled in favour of usb dongle)
blacklist r8192se_pci

---

### Post by chili555 on 2010-09-25
Glad it's working! Have fun.

---

