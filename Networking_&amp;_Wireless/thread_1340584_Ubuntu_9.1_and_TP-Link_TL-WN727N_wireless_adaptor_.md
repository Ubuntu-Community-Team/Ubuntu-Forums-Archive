---
title: "Ubuntu 9.1 and TP-Link TL-WN727N wireless adaptor issues"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by austinbyrne on 2009-11-28
Hi All,

I am having trouble with a Wireless USB adaptor TL-WN727N and Ubuntu 9.1. Without installing an additional drivers Ubuntu seemed to install the adaptor as soon as it was plugged in but when it will not connect to my wireless router. 

The list of wireless networks available that is finds names are nonsense. Instead of displaying the network name e.g. netgear it is load of symbols and alpha numeric characters. Sice I cant tell which on is my network as my neighbors also have wireless routers, I tried creating a new network with a SSID name same of my wireless router. Ubuntu appears to connect to it but I don't think it actually is connected to it because if I give it a different SSID name it still connects! None of the signal strength bars are lite up when it is "connected" to the wireless router. Also the ip address that it gets via the dhcp is 10.43.33.1 which is also wrong.

I also tried installing the windows drivers that came on the CD via the ndiswrapper again with no joy.

Any help with this would be much appreciated.

Thanks,
Austin.

---

### Post by raineater on 2010-07-15
Here's what worked for me.
1. remove ndiswrapper
2. install wicd - which replaces network-manager
3. edit /etc/modprobe.d/blacklist.conf to add the following - which I found
 at [http://community.linuxmint.com/hardware/view/1518](http://community.linuxmint.com/hardware/view/1518)
```
#disable the misbehaving RALink drivers.
#The WN727N only needs the rt2870sta driver.
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib

```4. reboot and use wicd to setup connections

This is on an AMD T64x2 system.  I bought the device because Unbuntu has the RALink drivers and didn't expect quite so much searching and tweaking.  In the end the solution is pretty simple, I didn't even have to compile anything but this short list of steps for the solution.  ;)

---

