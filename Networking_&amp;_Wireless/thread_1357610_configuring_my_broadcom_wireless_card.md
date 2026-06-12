---
title: "configuring my broadcom wireless card"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by herbert tamayo on 2009-12-17
Hi, I've recently installed ubuntu 9.10 in my hp dv2-1010la, this laptop has a broadcom based wireless card, so, after the installation i got a notification that it suggested to me to install the BRM43 wireless driver - the privative broadcom driver, I took the advice and I installed it but my wireless card could not be configure.

I went to check if the driver was correctly installed and it looks that is active, but doing ifconfig wlan0 it doesn't respond, also i went to check the /etc/network/interfaces file and only is up my wired NIC card. so my questions are:

1. what is the command to check if the BRM43 driver is up? 
2. if my wireless card is down, it means that doesn't work with broadcom driver?, should I installed ndiswrapper?
3. if the wireless card works with ndiswrapper it can be work in "listening mode"?
4. is there some log file that can help me to check what is happening with my wireless card?

all the best

---

### Post by gentlemen on 2009-12-17
if the driver works it would list it in System -> Administration -> Hardware Drivers.

if you're using driver version bcm43xx -- b43 which is what my broadcom card uses (and solved my wireless issues), all i had to do was install b43-fwcutter, which i found on

[http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware)

it has a lot of info.

hope this helps

---

