---
title: "I don't have ethernet"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by mr.suchy on 2009-12-05
Hi,

Sometime I have this problem, tern on computer and I don't have Ethernet. I use ndiwripper and I use WiFi to connect to the net. What can I check to fix this problem ? Thanks for help

Best regards!

---

### Post by lrcaballero on 2009-12-05
Are you dual booting??? asumming that you are dual booting with Windows, are you able to connect with Windows and/or are you having this problem with Windows as well??? if you are there is a Windows update that is causing to have limited connectivity and local connection only. This is the update in Windows that you can go into remove Programs window and uninstall it! (KB974455) once you unistall it restart your computer and see if that works!!! also you can go into network conncetions in windows and disable Pv6 in both your wireless and wired. Let me know if this hekp you!

good luck

Luis

---

### Post by mr.suchy on 2009-12-05
@lrcaballero thanks for replay. I don't have windows on this computer. Right now I change max address in my mobile computer so I can write this. 

On Ubuntu I can ping router (wifi) but I don't have internet. ON mobile computer (windows XP) everything works good. Thanks for any help!

---

### Post by Iowan on 2009-12-05
If ylu can ping the router, I suspect that means Ubuntu gets an IP address, and I presume it's in the right subnet. We are gonna need you to provide some more information - if the request is not clear, please ask for help (sometimes I neglect to fill in details). From a terminal, check **route -n** ( post results) and post contents of */etc/resolv.conf*

---

### Post by mr.suchy on 2009-12-06
OK when I write ```
route -n
``` I have no results. The same results I have from ```
sudo gedit /etc/resolv.conf
```

I install one again ndiswrapper from [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

And this time I instal Wicd in this software I see my wirless network but I can get an IP adress. Yesterday I have an IP from AP now I don't.

In Wicd I set "ndiswrapper" to my default driver.

Best regards!

---

### Post by mr.suchy on 2009-12-06
I put static IP and I connect to AP but still I don't have connect to the ethernet. 

```
mrsuchy@mrsuchy-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
0.0.0.0         192.168.1.2     0.0.0.0         UG    0      0        0 wlan0
```

and ```
sudo gedit /etc/resolv.conf

nameserver 84.205.161.138
nameserver 84.205.160.1

```

When I ping eg. google.com I have "unknown host."

---

