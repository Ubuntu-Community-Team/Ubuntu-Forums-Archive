---
title: "Using iwconfig"
date: 2005-02-16
forum: Networking &amp; Wireless
---

### Post by brushhead on 2005-02-16
Sorry if this is a real newbie question, but when I try and set up my USRobotics WiFI card (USR2210) the kernel detects it OK apparently and maps it as being wlan0.  


I also manage to get the icon at the top of the screen to state what the link quality is like too.  

The thing is I matched up the channel number to my access point, but the 'Access point' readout from iwconfig is different every time I Down/Up it via ifconfig.

Is the AP name actually the MAC address of the AP or soemthing else?  Also when I state that it is a managed node, and then state ap any the whole machine locks up.

I am also running it without WEP as most people say it is easier to get ti working before turning WEP back on.

FYI it's a Dell Inspirion 1000 laptop.

Any ideas folks?

Cheers,

Rob.

---

### Post by alastair on 2005-02-16
Yes, a little confusing sometimes. Things are not quite "there" yet.

This "ap" value is just the MAC. Forget abount setting "managed" mode - it's probably the default.

You can set "ap" using something like :

iwconfig wlan0 ap <MAC of access point>

You can also add this to the file :

/etc/network/interfaces

e.g. something like :

iface wlan0 ....
...
wireless_ap <MAC of access point>

---

