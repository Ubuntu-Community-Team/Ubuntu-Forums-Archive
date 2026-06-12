---
title: "Netgear wg311v3 Questions"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by JohnJD on 2010-03-27
My wireless card is working fine.  The only problem is that every time I restart the computer, I have to run "sudo modprobe ndiswrapper" to get it to work.  The help guide ([https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)) said to run "sudo ndiswrapper -m" to get it to work every time.  When I run that, this is what I get:
```

johnny@johnny-desktop:~$ sudo ndiswrapper -m
[sudo] password for johnny: 
module configuration already contains alias directive


```

Any clues?

---

### Post by prshah on 2010-03-28
> **JohnJD said:**
> I have to run "sudo modprobe ndiswrapper" 

Edit (or create if it does not exist) the file /etc/modules.conf. At the end of the file, add a single line```
ndiswrapper
```

Now, when you restart, the ndiswrapper module should be loaded automatically. Please post back if you have problems.

---

### Post by JohnJD on 2010-03-28
Works perfectly.  Thank you!

---

