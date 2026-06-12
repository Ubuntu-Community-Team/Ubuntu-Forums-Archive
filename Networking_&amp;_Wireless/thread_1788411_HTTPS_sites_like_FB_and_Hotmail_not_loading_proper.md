---
title: "HTTPS sites like FB and Hotmail not loading properly"
date: 2011-06-22
forum: Networking &amp; Wireless
---

### Post by WallOfShame on 2011-06-22
Greetings,
I am using Lenovo G550 laptop wid Intel Dual Core 2GHz, 2GB RAM, 250GB HDD, etc. Earlier I had 2 partitions 187GB (Windows 7) and other 33GB of Lenovo drivers. I split 187GB to 143GB (Windows 7) while remaining 44GB for Ubuntu 10.10!
Everything's been working fine except for internet. I am unable to load many https sites like fb, hotmail, etc. Gmail is working absolutely fine.
I did some research on this forum and disabled ipv6! I also checked for firewall and it was disabled. Then I also configured Open DNS and checked if it is working fine. But nothing has helped.
When I connect to these sites without 's' in https (i.e. only http) these sites load fast. I enter my username n password and then I am redirected to a compulsory https site which then takes me to a page like this (shown in thumbnails)! I have tried Chrome n Firefox 3.6 (which have SSL and TLS checked in preferences)! All these sites are working fine on Windows 7. But I don't want to use Windows 7 every now and then because it has become too slow and boring! Please help me with this. 
I connect to internet using DSL wired (BSNL Broadband 256Kbps)
Thanking in advance!

---

### Post by carverj on 2011-06-23
> I also checked for firewall and it was disabled. 

And how about your modem/router that connects you to the internet. Could that be blocking the secure socket layer port?

---

### Post by WallOfShame on 2011-06-23
> **carverj said:**
> And how about your modem/router that connects you to the internet. Could that be blocking the secure socket layer port?
I am using Huawei SmartAX MT882. I don't think that modem is blocking it! Because Gmail is working fine with https. Also on windows 7 all the sites are working fine with same modem.

---

### Post by dineshs on 2011-06-24
How do you connect to internet?Do you use a PPPoE dialler(modem in bridge mode) or Is the connection always ON (Modem in PPPoE mode with username and password stored in it)?
You may try a different MTU (default is 1500, so try 1492 or 1482).
If your modem is in bridge mode and if you are using network manager DSL connection,click network manager icon-edit connections-DSL tab-select the connection-edit-wired tab-change MTU to 1492 and apply.
If you are using PPPoE mode ,click network manager icon-edit connections-wired tab-select the connection-edit-wired tab-change MTU and apply.
Run ```
sudo service network-manager restart
``` and see if there is any difference

---

### Post by Sepiraph on 2011-06-25
Looks like the issue is with displaying https pages on Facebook and Hotmail/Live.com.  One of the errors that I see from my browser is NS_ERROR_NET_TIMEOUT.  This issue occurs when using both Firefox and Chrome (I tried in Opera and it doesn't work either).

---

### Post by WallOfShame on 2011-06-26
> I tried in Opera and it doesn't work either).
I also tried Opera. FB works only sometimes when i reboot! It doesn't work afterwards. Why are the stylesheets not loading? It loads only text! How to overcome the timeout issue?

---

### Post by parthsv1991 on 2011-06-27
same problem on same 10.10 version:(

---

### Post by Sepiraph on 2011-08-18
I noticed that the issue is now fixed (using firefox 5)

---

### Post by WallOfShame on 2011-12-21
> **Sepiraph said:**
> I noticed that the issue is now fixed (using firefox 5)

Yes! The problem has been solved thanks to the new version of firefox. 
(I think the problem occurs when linux communicates with an ASP .NET Microsoft server)

---

