---
title: "Wireless networking doesn't work in Ubuntu Studio 9.04"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by brncao on 2009-06-17
My wireless network doesn't work in Ubuntu studio 9.04 (64bit). I tried to configure it from Network by entering my network password, ESSID, and set DHCP to automatic. Then I went on firefox and typed in google.com to see if it works, but I got "cannot find page" or something like that meaning there's no connection. Can anyone tell me how to get connected? It works fine in Ubuntu, but not Ubuntu Studio.

---

### Post by cotcot on 2009-06-17
Maybe the lease time (typically 2 hours) from the ubuntu install is not yet released ? (supposing it is a dual boot, you swapped from ubuntu to ubuntu studio and your provider only allows 1 lease.

It is only a guess.

---

### Post by frodon on 2009-06-18
Moved to Networking & Wireless forum.

---

### Post by GoodEgg on 2009-06-24
The Network Settings panel [System>Administration>Network] that comes with Ubuntu Studio 9.04 only supports WEP encryption for some reason. 
If your router uses WPA-PSK ubuntu studio won't connect to it as is...

The normal Ubuntu distro uses 'Network Manager', which does support WPA-PSK and other encryptions. 
Unfortunately installing Network Manager in Ubuntu Studio hasn't worked for me..

---

### Post by Co.Sinecure on 2009-08-15
Anyone have a solution/explanation for the lack of WPA support in ubuntu studio?

---

