---
title: "Wifi won't connect"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by ftornell on 2011-04-26
Hi,
Just reinstalled ubuntu 10.10 x86 on an old laptop.
The wireless doesn't seem to work and I have no idea how to solve this.

In gnome I can see NetworkManager display the network ESSID.
I have entered the key but no success, it tries to connect and then times out after about 1-2 mins.

I have tried to change the encryption from WPA2, to WPA to WEP to nothing but the same issue.

In a terminal/shell running ifconfig/iwconfig I can see eth1 as the networkinterface.

How can I investigate this further. If there was an IRQ collission or something it would not be showing the ESSID right?

Any hints appreciated!

---

### Post by josephmills on 2011-04-26
you are not connected via eth0 and wlan0 are you? if so make sure that you disconnect the eth0 first then try signing into your wireless. also have you tried to go from no password to wep to wpa2? also have you gone into your passwords and encryption keys and deleted anything that would get in the way? I am sure that none of this will help but give it a shot rules some things out.

---

### Post by ftornell on 2011-04-27
Hi,
No eth0/cable is connected.

Have 3 other wifi computers running wpa2 without any problems in ubuntu.

Have also reset the wireless router but it did not help...

---

### Post by josephmills on 2011-04-27
all right lets take a deeper look ```
lspci -nn
``` and a ```
rfkill list 
```

---

