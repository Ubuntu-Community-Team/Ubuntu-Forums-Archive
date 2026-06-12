---
title: "HW RF Kill switch doesn't work in 8.10 Intrepid Ibex"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by josergc on 2008-12-17
Hi all,

I have just updated from Ubuntu 8.04 to 8.10 and I have got a problem turning on the wireless connection.

My laptop has a Intel PRO/Wireless 3945ABG [Golan] Network Connection which driver is iwl3945 and module iwl3945 that can be enabled and disabled pressing a button in the laptop. This button was working before updating but it doesn't work anymore. In dmesg I cannot watch the message with I press the button and the Ubuntu 8.04 it was working.

In the NetworkManager this card is not shown as well.

I tried also plug an USB Wireless dongle (NetGear, Inc. MA111 WiFi (v1)) but the NetworkManager says "the wireless network is disabled". It doesn't give me any option to use it but I watch that the iw* commands can get information from the air, how do I connect using the command line?

Thank you in advance!

---

### Post by josergc on 2008-12-17
Hi all,

I have discovered that if I press the radio kill button to turn on it when the splash screen with the logo of Ubuntu and the loading bar appears, the wireless is indeed turned on, but I cannot turn on when I am running in X already.

There is one thing more, with the wireless turned on in X, if I turn off it pressing the radio kill button, this works, but I am not able to turn on the wireless again. The only solution is reboot the computer again.

Any suggestion??

Thank you in advance,

Kind regard,

---

### Post by josergc on 2008-12-17
PS: I forgot a small detail: In this new version of Ubuntu, the LED of the wireless turn on when I turn on the radio. In the previous version 8.04, this LED was not working, but in the version 7.10 this LED was working as well.

Cheers!

---

