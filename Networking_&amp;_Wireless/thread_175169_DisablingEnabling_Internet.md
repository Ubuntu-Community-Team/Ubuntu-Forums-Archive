---
title: "Disabling/Enabling Internet"
date: 2006-05-12
forum: Networking &amp; Wireless
---

### Post by lukeblack on 2006-05-12
Hi

I was wondering whether anyone could tell me what command line script I need to run in order to disable/enable my internet (eth0?). I found the type of functionality I want in this GUI:

System > Administration > Networking

However I was wondering how I can achieve similar results using the CLI. And by the the way, I am using a DHCP router for my internet access at the moment. Any help would be greatly appreciated.

Thanks in advance,
Luke :KS

---

### Post by 5-HT on 2006-05-12
For your setup using DHCP:

To disable
```
sudo ifconfig eth0 down
``` 
To enable*
```
sudo ifconfig eth0 up
sudo dhclient eth0
``` 

*If you were not using DHCP, there should not be a need for the 'dhclient' bit.

EDIT: You could also do this a shorter way by doing  ```
 sudo ifdown eth0 
``````
 sudo ifup eth0
``` (sudo dhclient eth0 still applies if using DHCP)

Hope that helps.

---

### Post by lukeblack on 2006-05-12
Works like a charm, 5-HT. Thanks so much!

---

