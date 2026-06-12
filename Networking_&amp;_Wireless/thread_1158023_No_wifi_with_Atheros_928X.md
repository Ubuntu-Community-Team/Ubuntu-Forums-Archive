---
title: "No wifi with Atheros 928X"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by Giancarlo.Pasquini on 2009-05-13
After one month of work I am still stuck to connect to wireless.
Machine Toshiba Satellite Pro. Networkcard Atheros 928X.
OS Ubuntu 8.10.
With the WI FI switch in the off position ,the PC loads the ATH9K driver. the Command Iwconfig correctly shows the card. The networking shows correctly and it is correctly grayed out. 
If I put the WIFI switch in the ON position, the networking is no longer grayed out but before connection is established the PC will freeze up completely, a hard reset is the only way out.
I have tried backports.I have read many how to and blacklisted the ATH9K to load in turn ATH5K , ATH_PCI and Ndiswrapper. With all of these drivers command IWCONFIG does not show the WIFI card.
Now I have upgraded to the last Ubuntu 9.10. With this release the PC does not freeze anymore  regardless of the position of the WIFI switch but the WIFI connection is always grayed out. Iwconfig shows the wireless card. 
WIFI correctly works with windows so HW problems can be ruled out.
Any ideas

Thank you.

---

### Post by bluestreek on 2009-05-13
Try disabling bluetooth. This worked for me but the connection is very unstable. It stays connected to the AP but if you put any traffic through it bugs out and drops activity for about 10 seconds. Overall ath9k is a very bad driver.

---

### Post by Peter09 on 2009-05-13
Here is a thread that may help

[http://ubuntuforums.org/showthread.php?t=1135445](http://ubuntuforums.org/showthread.php?t=1135445)

---

### Post by Giancarlo.Pasquini on 2009-05-14
Thank you for both your answers. This week end I will try to disable bluetooth. I had already tried the Post from Volanin to no use. I will let you know

---

