---
title: "Realtek 8187b Ndiswrapper"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by killertaru on 2009-03-08
I have Ubuntu 8.10 and a toshiba a215-s7437 
I been having problems with the driver that ubuntu automaticly uses.
I believe its r8187 or rtl8187b 
I have installed Ndiswrapper and used the .inf for windows 98, and ndiswrapper will say device is detected 





But in the network-applet it shows 
Wireless Networks (Realtek RTL8187b)
---List of networks----
Wireless Networks (Realtek RTL8187b)
--same list of networks as above----

I have added this to my /etc/modprobe.d/blacklist
```
blacklist rtl8187
blacklist r8187
```

I trying to get the two lists of SSIDs to be one. 
Useing Ndiswrapper as the main driver.  

And in Network-applet's Connection Information it has two tabs
Auto "SSID NAME" (default)
Auto "SSID NAME"


Both tabs say that the Driver is ndiswrapper


**Edit 

Networkapplet shows: 
Both Auto eth0 are greyed out because no cable is connected

Wired Network (Toshiba America Info Systems RTL8101E/RTL8102E PCI Express Fast Ethernet controller)
Auto eth0
WIred Network (Toshiba America Info Systems RTL8101E/RTL8102E PCI Express Fast Ethernet controller)
Auto eth0
Wireless Networks (Realtek RTL8187b)
---List of networks----
Wireless Networks (Realtek RTL8187b)
--same list of networks as above----

---

### Post by Crafty Kisses on 2009-03-08
What are the results of the following command?
```
ndiswrapper -l
```

---

### Post by killertaru on 2009-03-08
username@ubuntu:~$ ndiswrapper -l
net8187b : driver installed
	device (0BDA:8197) present (alternate driver: rtl8187)
username@ubuntu:~$

---

### Post by Mazin on 2009-05-31
Hello, it looks like this is extremely tardy, but that's only an illusion.

Your computer is still automatically using the default driver instead of ndiswrapper.  You need to add rtl8187 to the blacklist file located in /etc/modprobe.d/ (if memory serves correctly).  You should probably then reboot, at which point Linux will NOT load rtl8187 and use ndiswrapper instead.

---

