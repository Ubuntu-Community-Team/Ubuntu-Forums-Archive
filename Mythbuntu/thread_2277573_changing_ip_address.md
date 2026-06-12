---
title: "changing ip address"
date: 2015-05-09
forum: Mythbuntu
---

### Post by deanie44 on 2015-05-09
Hi everyone.  I have the Hd Homerun Prime as a tv tuner in Mythbuntu.  It is a great tuner, but changes ip addresses every week.  I cannot give it a static ip  because it is not a commercial unit.  The card is attached to a Belkin wireless router via cable.  I have been searching for an answer to solve this problem, but have not found a solution.  Can anyone help me?  Any help will be appreciated.  deanie44

---

### Post by steeldriver on 2015-05-09
Are you able to set a DHCP address reservation on the router? that is probably the simplest solution

---

### Post by deanie44 on 2015-05-09
I do not know how to set a DHCP address reservation on the Belkin router.  Can you point me in the right direction to figure this out.

---

### Post by steeldriver on 2015-05-09
You would need to look at the documentation for your particular model of router e.g. [http://www.belkin.com/pyramid/AdvancedInfo/F5D8235-4/Advance/reserveIP.htm](http://www.belkin.com/pyramid/AdvancedInfo/F5D8235-4/Advance/reserveIP.htm)

---

### Post by Bucky Ball on 2015-05-10
Setting a static IP:

> Static IP assignment
A static IP address can be configured using the following command (the quotes are required as shown):

Format:  hdhomerun_config <old ip> set /sys/ipaddr "<new ip> <subnet> <gateway>"
Example: hdhomerun_config 169.254.34.98 set /sys/ipaddr "10.10.20.43 255.255.255.0 10.10.20.1"

Note: The TECH requires a gateway when used to stream multicast, even if on the same subnet

From [here]("http://www.silicondust.com/hdhomerun/hdhomerun_tech.pdf"). 

Reserving an IP on the router is another option.

---

