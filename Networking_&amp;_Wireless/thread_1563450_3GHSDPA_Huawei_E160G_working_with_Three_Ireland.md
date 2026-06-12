---
title: "3G/HSDPA Huawei E160G working with Three Ireland"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by Schaeufele on 2010-08-29
_System:_

Toshiba Satellite 3000-514 (upgraded to 1 GB RAM)
Xubuntu 9.10 Karmic Koala, Kernel 2.6.31.22.35

_3G/HSDPA USB Modem:_

Huawei E160G, provided by Three Ireland, firmware version 11.608.06.00.156

General hint: 

This modem has a socket for an external antenna. The mast I am getting my mobile broadband from is almost six miles away with no direct line of sight (trees in between). I am using this external antenna: [http://solwise.co.uk/3g-antenna-lpda-0044.htm](http://solwise.co.uk/3g-antenna-lpda-0044.htm). Solwise also sell a pigtail to connect antenna and modem. This setup works really well and is stable with excellent signal strength and good download speeds. A massive improvement over the constantly faulty and glacially paced Eircom dialup line.

[U]Steps to get modem to work with my system:
[/U]
0) Tried modem without any changes to Xubuntu/modem, just plugged in modem. Network Manager found connection but I could not connect. I then went through the below steps.

1) Install USB-Modeswitch

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

Not sure if this was entirely necessary. Perhaps you want to try without first.

2) Upgrade modem firmware

Unfortunately this only works under Windows, but perhaps the local Three-shop can help. I did it on my laptop where I still have Windows XP in parallel.

You will find the upgrader and instructions here:

[http://www.three.ie/nbs/support.htm](http://www.three.ie/nbs/support.htm)

Go to very bottom of above page to find 

[http://ask3.three.co.uk/mbbdocs/drivers/E160-Updater.zip](http://ask3.three.co.uk/mbbdocs/drivers/E160-Updater.zip)

This updates the modem firmware to version 11.608.13.00.156.B409.

3) Boot Xubuntu

4) Plug in modem

Network Manager should find Three Ireland under Mobile Broadband. Edit the connection to make sure you have Number *99# and APN  3ireland.ie.
Finally: connect using Network Manager and surf away!

---

### Post by Schaeufele on 2010-08-30
_Addition to my previous post_

With Ubuntu 9.10 you will need USB-Modeswitch, otherwise the USB modem will need to be removed and plugged back in before a connection can be made.

USB-Modeswitch can either be installed using the method described above, or much simpler through Synaptic. Just start Synaptic, search for USB-Modeswitch and install.

---

