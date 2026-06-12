---
title: "enable/disable bluetooth via command line"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by vies on 2010-09-26
Hi,

I have a following problem. I need to enable/disable bluetooth via script. Currently I'm trying to simply start and stop bluetooth service by issuing command

```
sudo service bluetooth start
```
or
```
sudo service bluetooth stop
```

Stopping obviosly works ok, but when I'm starting the service, it starts, but bluetooth radio is turned off and I need to enable it trough bluetooth-manager (blueman).

Is there a way to turn radio on by command line? Or should I use some better way of turning bluetooth on and off at the first place

Vies

---

### Post by crysman on 2011-10-20
> **vies said:**
> Hi,
...
I have a following problem. I need to enable/disable bluetooth ...
Stopping obviosly works ok, but when I'm starting the service, it starts, but bluetooth radio is turned off and I need to enable it trough bluetooth-manager (blueman).
...


Stopping the service does not work for me. According to *powertop*, there is still energy drain by bluetooth ("Radio device: btusb"). To disable it I have to go to Blueman applet, right click and select "Turn Bluetooth Off". Please, **is there any way how to achieve this from console**? Thanks a lot!

PS: using Xubuntu 11.10 on ASUS U36SD
--

---

### Post by atultiwari on 2012-04-20
> **crysman said:**
> Stopping the service does not work for me. According to *powertop*, there is still energy drain by bluetooth ("Radio device: btusb"). To disable it I have to go to Blueman applet, right click and select "Turn Bluetooth Off". Please, **is there any way how to achieve this from console**? Thanks a lot!

PS: using Xubuntu 11.10 on ASUS U36SD
--


I am also facing same problem in Ubuntu 11.10... any help appreciated..

Thanks in Advance..

AT

---

