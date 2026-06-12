---
title: "Monitor Mode Help"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by squawskier on 2009-03-21
Hello, I am trying to set my wireless card into monitor mode with the following command: 
sudo iwconfig wlan0 mode Monitor Channel 11

but I get the following error:
Error for wireless request "set Mode" (8B06)
   SET failed on device wlan0; Device or resource busy.

Is this a wireless card issue or am I doing something wrong?  Any help would be much appreciated!

Eric

---

### Post by helgman on 2009-03-22
I'd guess it's a card problem since the command works fine on one of our laptops. I've had problems like that, the card used a different set of tools. Try Google and the cards chipset.

Regards,
Helgman

---

### Post by kevdog on 2009-03-22
Please tell us more about your card - the chipset -- and driver you are using.

---

