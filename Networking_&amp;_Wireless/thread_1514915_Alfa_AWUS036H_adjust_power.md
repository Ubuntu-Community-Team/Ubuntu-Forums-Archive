---
title: "Alfa AWUS036H adjust power"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by Matt1999 on 2010-06-21
I am using Ubuntu 10.04 64-bit and I purchased a new ALFA AWUS036H wireless card. I would like to know if this "1Watt" wireless card is configured for full power. 
 
iwlist wlan0 txpower results:
 
wlan0 unknown transmit-power information.
Current Tx-Power=27 dBm (501 mW)
 
It appears to me that I should be able to increase the power. "iwpriv wlan0 highpower 1" does not work. 
 
Do I need to patch the new default driver that comes with Ubuntu 10.04 64-bit with the aircrack one following these directions: [http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187) ?
 
Monitor mode and a injection tests seem to work fine with the driver I have installed. 
 
Matt

---

### Post by chronos00 on 2011-09-08
Could you solve this?

Is there a simple way of accomplishing this without recompiling drivers each time?

Thank you!

---

### Post by chronos00 on 2011-09-09
Looking into it some more, I found the solution myself :)

Here it is:
[http://ubuntuforums.org/showpost.php?p=11233055&postcount=4]("http://ubuntuforums.org/showpost.php?p=11233055&postcount=4")

Regards!

---

