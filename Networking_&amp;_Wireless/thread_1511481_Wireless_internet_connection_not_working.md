---
title: "Wireless internet connection not working"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by barbimi on 2010-06-16
I'm using a WUSB54GC network adapter to connect to my home wireless network. My network was not visible, so I added it and it shows connected, but when I launch the browser, I can't get a connection. I'm using Ubuntu 10.4. All other computers on the network connect fine and I disabled my firewall to see if that made a difference. Any help would be much appreciated.

---

### Post by b k on 2010-06-16
> **barbimi said:**
> I'm using a WUSB54GC network adapter to connect to my home wireless network. My network was not visible, so I added it and it shows connected, but when I launch the browser, I can't get a connection. I'm using Ubuntu 10.4. All other computers on the network connect fine and I disabled my firewall to see if that made a difference. Any help would be much appreciated.
 
Hi there, first confirm your wireless adapter device ID .
 
May I suggest you go to *Applications*, *Accessories*, *Terminal* and do :
 
```
lsusb
```
 
[COLOR=red][COLOR=black]Somewhere [/COLOR][/COLOR]in the output there should be this device ID:
 
[COLOR=blue]13b1[/COLOR]:[COLOR=blue]0020[/COLOR]
 
If the device ID is not there, please post output of *lsusb*
 
Next do this:
 
```
lsmod
```
 
Also post the output of *lsmod*
If the rt73 driver is somewhere in the output from *lsmod*, 
 
then try the solution at post #3 of this link [http://ubuntuforums.org/showthread.php?t=1492307](http://ubuntuforums.org/showthread.php?t=1492307)
 
Good luck and post back

---

