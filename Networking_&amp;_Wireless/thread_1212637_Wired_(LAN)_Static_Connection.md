---
title: "Wired (LAN) Static Connection"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by seb.el on 2009-07-13
Hi,
new to Ubuntu, happy to receive some basic information.


Installed Ubuntu 9.03 and don't have a WiFi Card in my new Desktop. The Internet via Cable works seamless on my Acer Netbook with this Acer Linux as well as on an Apple MacBook.


As Connect automatic via DHCP does not work I would like to try Static Connection. In the OS help I found
Static Connection: Click IPv4, Click Manual, and then "Enter your details and click ok".

Right,... what details? I believe I need to fill Address, Netmask and Gateway.


Anybody has a suggestion what I should write? I found in a different thread IP 192.1.2.102
Would that work? What would I need for Netmask and Gateway?

Hope my hardware is not the fault.

Thanks and Regards,
Sebas.

---

### Post by cariboo on 2009-07-14
What you need to enter is an ip address that is in the same netblock as your Acer Netbook. For example if the ip address of your netbook is 192.168.1.100 the ip address for your desktop could be 192.168.1.101. so to set the static ip address using network manager you would enter:

```
ip addres:   192.168.1.101
netmask    255.255.255.0
gateway    192.168.1.1
```

THe gateway address should be the ip address you use to acces the management interface of your router.

---

### Post by seb.el on 2009-07-14
Thanks for your response
. All your information provided is correctly working with a static LAN on my Acer.
I confirmed on the MacBook and Netmask is there called Subnet Mask and  Gateway is called Router.

Anyway, I understand that Ubuntu should easily automatic connect via DHCP to wired router. Therefore, I should have an Hardware failure. Well, I'll check that.

Cheers!
Sebas.

---

### Post by seb.el on 2009-07-14
Ok, I just come back from the store and where we just plugged the cable in and it Network/Internet worked directly using DHCP as well a static.

The helpful guy explained me that he has heard of several people having trouble with the Router "Siemens Gigaset SX 762 WLAN dsl" connecting directly. He told me to contact "Une" (local communication company). There might be a fix in the Router settings.

Well, I chose to buy myself a "D-Link WUA-1340 Wireless G USB 2.0 Adapter", plugged it, entered my password, and I have fast Internet running on my Ubuntu system.

Just writing this down, in case anybody in the future would like to know my experiences with that products... don't hesitate to contact me in case you want to know more.
Sebas.

---

