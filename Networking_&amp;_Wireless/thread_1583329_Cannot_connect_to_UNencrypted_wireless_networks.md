---
title: "Cannot connect to UNencrypted wireless networks"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by tallmtt on 2010-09-27
Here is a situation I have never come across (though I have only been using linux since 2004).

I am running ubuntu 10.04 and using Wicd Network Manager.

I can connect to my WPA encrypted home network, but if I go to my coffee shop to use their unencrypted wifi - I cannot.

Even using the terminal.  I think it is the way the device sees the network - but I don't know how to fix it.

I have a screenshot with wicd here:

[IMG]http://img805.imageshack.us/img805/4342/screenshotcq.png[/IMG]

And one with connecting to the essid here:

[IMG]http://img84.imageshack.us/img84/2288/screenshot1bb.png[/IMG]

Afterwhich, dhclient was unable to obtain an ipaddress - just like wicd above. 

My iphone connected to this network easily without encryption or needing to use the browser to authenticate, etc.

Any ideas on how to fix this?

Specs:

Samsung NC10
lspci: 
```
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```
lsmod:  
```
mac80211              205050  1 ath5k
ath                     7611  1 ath5k
mac80211              205050  1 ath5k
ath                     7611  1 ath5k
```

---

### Post by gordintoronto on 2010-09-27
Did you reboot at the coffee shop, or just resume from suspend or hibernate?  There may be a widespread problem with going from a secure network to an unsecure one, without rebooting.

---

### Post by tallmtt on 2010-10-10
Sorry for taking so long to respond. 

Yes, I started from a fresh boot up.

I am going to reinstall the OS and see if that fixes it.

---

### Post by Fritsl on 2011-01-08
I am new to Linux / Ubuntu, and I am quite surprised that I have the excact same problem:

Any encrypted network is fine, but my wireless cannot connect if the network is unencrypted.

Ubuntu 10.10

---

