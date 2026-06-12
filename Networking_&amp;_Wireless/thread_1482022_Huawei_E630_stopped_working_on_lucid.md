---
title: "Huawei E630 stopped working on lucid"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by kockas on 2010-05-13
Hi,
 
I installed my 3G card Huawein E630 sucesfully on carmic 9.10. However, after upgrade to lucid 10.04, I cannot connect anymore.
After insertion card contains drive containing windows drivers and modem.
In karmic both were detected properly, however in lucid only drive is visible and modem is not detected.
Connection is setup properly, but network manager does not offer me the connection.
Any idea, how can I get it working again?
 
Thanks.

---

### Post by alexfish on 2010-05-13
hi

try to eject or safely remove the device that appears on the desk top

to see if the modem has configured and the ports , from the terminal

Code:

dmesg | grep -e "modem" -e "tty" 

then try NM

---

### Post by MeanEYE on 2010-05-15
Hi, I ran into similar issue while I was fixing friends laptop. Solution is quite simple... 

Just install **usb-modeswitch**. Not sure why Ubuntu Team decided to remove this package from Lucid. Without this package Huaweii modems are detected only as USB storage devices.

To install this package from terminal use the following command:
```
sudo aptitude install usb-modeswitch
```

Have fun!

---

### Post by jimmers on 2010-05-16
usb-modeswitch is available in Lucid through synaptic

---

