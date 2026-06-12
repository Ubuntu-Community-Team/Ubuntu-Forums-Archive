---
title: "RTL8185 does not work in Hardy"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by fpereira76 on 2009-01-07
Hi all,

I've been trying to configure a RTL8185 wireless PCI card in my Ubuntu Hardy Heron amd64 desktop. I am trying to use Kernel  2.6.24-22-generic and the driver rtl8180 that comes with linux-backports-modules-hardy package. 

From Network Manager, I can see all AP around me, including mine (WAP-TKIP). However, I cannot connect to it; authentication times out. I have an Ubuntu'ed notebook (32 bits, rt61 pcmcia card) which perfectly connects to the AP, so I think the problem is in the rtl8180 driver.

I've tried to use wifi-radar, to configure wireless driver directly (in /etc/network/interfaces), to use ndiswrapper with MS Windows 32-bit drivers. I've even tried to compile the rtl driver shown in [http://willdaniels.co.uk/articles/howto-guides/10-howto/12-r8180-hardy](http://willdaniels.co.uk/articles/howto-guides/10-howto/12-r8180-hardy) but I got no different result. Every time I try to connect with wireless, authentication times out. A log file is included to show what happens...

Does anyone knows what could be happening ?

Thanks for any help !

---

### Post by albinootje on 2009-01-07
> **fpereira76 said:**
> 
From Network Manager, I can see all AP around me, including mine (WAP-TKIP). However, I cannot connect to it; authentication times out. I have an Ubuntu'ed notebook (32 bits, rt61 pcmcia card) which perfectly connects to the AP, so I think the problem is in the rtl8180 driver.


Searching for this error in your log :
> 
"dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason"

shows this : [http://ubuntuforums.org/archive/index.php/t-178619.html](http://ubuntuforums.org/archive/index.php/t-178619.html)
which offers a solution.

You can try also wicd : [http://wicd.sf.net](http://wicd.sf.net)

---

### Post by fpereira76 on 2009-01-09
Thanks, but this message does not seem to be the real problem. It also appears in my notebook, which correctly connects to the AP.

Fortunately, I could manage to fix the problem by using the driver that is available at [http://willdaniels.co.uk/articles/ho...12-r8180-hardy](http://willdaniels.co.uk/articles/ho...12-r8180-hardy). The problem was that it builds novel ieee80211-rtl stack modules (IEEE 802.11 stack for the RTL chipset), but there are other modules with the same name in the /lib/modules dirs (for RTL8187-usb driver). After a depmod -a, r8180.ko became dependent of the wrong ieee80211-rtl stack modules.

I solved the problem by modifying /etc/modprobe.conf and by using install/remove commands creating a fake module (which I called r8180pat) to insmod/rmmod the correct module files. After that, everything was ok.

It is worth to notice that Network Manager does not work with that driver, since the former requires Wext, but the latter only supports IPW. Nevertheless, the site above also mentions that and shows how to configure WPA appropriatedly by modifying /etc/network/interfaces.

I hope that rtl8180 driver will come back to the linux-modules package soon.

---

### Post by albinootje on 2009-01-09
> **fpereira76 said:**
>  Fortunately, I could manage to fix the problem by using the driver that is available at [http://willdaniels.co.uk/articles/ho...12-r8180-hardy](http://willdaniels.co.uk/articles/ho...12-r8180-hardy). The problem was that it builds novel ieee80211-rtl stack modules (IEEE 802.11 stack for the RTL chipset), but there are other modules with the same name in the /lib/modules dirs (for RTL8187-usb driver). After a depmod -a, r8180.ko became dependent of the wrong ieee80211-rtl stack modules.


Cool that you fixed it yourself! :)

Can you edit that webpage link that you gave ?
It's invalid. 
You probably copied and pasted it too quickly from the forums (with the "...").

---

### Post by fpereira76 on 2009-01-12
Sorry, I've copied it directly from my first post. Here is the correct link:

[http://willdaniels.co.uk/articles/howto-guides/10-howto/12-r8180-hardy](http://willdaniels.co.uk/articles/howto-guides/10-howto/12-r8180-hardy)

---

