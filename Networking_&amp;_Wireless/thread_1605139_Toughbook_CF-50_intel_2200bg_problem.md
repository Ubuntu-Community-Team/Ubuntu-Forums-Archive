---
title: "Toughbook CF-50 intel 2200bg problem"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by jmatwyko on 2010-10-24
Fresh install today of 10.10
 
I replaced the original 2200 3b as it was only "b" with a intel 2200bg. Now I have the usual Radio Frequency Kill Switch is On: The main problem here is the toughbook doesn't have physical switch for wireless or a keyboard fn button combination to enable or disable wireless module. Also, BIOS doesn't any settings for wireless either.
 
The wireless is eth2 and when I try to turn it on I get this:
 
~$ sudo iwconfig eth2 power 1
Error for wireless request "Set Power Management" (8B2C) :
Set failed on device eth2 ; Input/output error.
 
I am going to have to try different mini-pci card because I have no way to toggle Kill switch?
 
thanks,
jm

---

