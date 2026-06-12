---
title: "problem with realtek driver r8101 and RTL8105E PCie  FE controller family"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by ubucris23 on 2011-02-03
I got a new Toshiba laptop and i am not able to use the Realtek Lad adapter . 

Especially, I installed _ubuntu 9.04 _. For some reason it was a driver r1869 installed. The LAN Ethernet card seemed to work(the LEDs were on) but the Networkadapter in ubuntu could not find the card. I could not connect to the internet. 

So I removed the r1869 driver, and I installed the r8101 official driver from realtek. When i type lsmod, i see only r8101 from drivers. 

Everything seems to be good, since ifconfig -a shows the ethernet eth0 interface. 

However , when i enable the driver, the led on the LAN card stops being On and the LAN adapter seems not work. The inux finds the hardware(also from lspci ) , but the hardware does not work any more.  The kernel log says that  r8101 : eth1 link is down , r8101 not support EEE ....

The interesting thing is that if i will not shutdown the PC , the LAN ethernet will not work in Windows also ( is recognized but not working).

If i shutdown, i can use again the LAN adapter in windows, but if i load the driver r8101 in ubuntu , i got the problem again. 

Please if you have any idea where the problem comes .



Thank you

---

