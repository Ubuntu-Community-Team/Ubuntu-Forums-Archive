---
title: "how to connect to wireless router through lan"
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by anuragupadhaya on 2009-09-22
i am new to ubuntu and i am using ubuntu 9.04 aka JAUNTY

i have a my internet connection through wireless router and connection to it though wifi works fine.

but the router also has 4 extra lan ports. when i try connecting to router through lan, it doesn work, most probably because i use a wpa/wpa2 key to secure my internet network.

So, my question is how can i specify a network key to connect to router through lan?

---

### Post by Iowan on 2009-09-22
WPA is a wireless security standard - it *shouldn't* be causing problems with the wired ports. What kind of "doesn't work" :) are you getting with the wired attempt? I presume you are attempting to get DHCP address via **dhclient**. Is the router configured to serve DHCP leases on the wired ports?

---

### Post by anuragupadhaya on 2009-09-23
yeh u got it right.
even i don think wired connections have anything to do with wpa security, and yes DHCP is enabled in router. what should i do??

when m attempting for wired connection, it is trying to connect for some 15-30 seconds then it says "wired connection disconnected"

i do think router is configured to serve dhcp leases on wired ports.

---

### Post by cariboo on 2009-09-23
Disable your wireless connection, then you should be able to coonect to your router, or connect a computer that has a wired connection only.

---

### Post by anuragupadhaya on 2009-09-23
> **cariboo907 said:**
> Disable your wireless connection, then you should be able to coonect to your router, or connect a computer that has a wired connection only.

i tried as you said, that is connecting to router after disabling wireless and rebooted the system too. But it is not getting connected. What should i do now??:confused:

---

### Post by Iowan on 2009-09-23
For the unlikely chance it might help, try [this]("http://ubuntuforums.org/showthread.php?t=1156441") one.

---

### Post by anuragupadhaya on 2009-10-03
its a late reply but the problem got solved.
the mistake was on my part.:oops:

actually to connect and disconnect many computers on the fly with my router, i had enabled MAC address filtering. Because of that new mac addresses were not getting allowed to access internet though router. As my machine had same Mac address but because of this reason only it wasn getting connected via LAN. As soon as i disabled the mac address filtering option, it got connected.:P

---

