---
title: "Broadcom Wifi Card: No Signal"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by Levitation on 2009-01-25
I have a Broadcom BCM4306 802.11b/g Wireless LAN Controller (rev 03) PCMCIA Wifi Card. Installed Bcm43xx and b43-Firmware from Cafeugo (b43-fwcutter would not install) ...The card is recognized, BUT, Wifi Radar indicates NO Signal for the half dozen networks that show up (I am getting a signal for those same networks on my other <Windows> laptop). The icons under SSID all have "?". And here is the strangest thing: The message at the bottom says "Connected to <network> (IP address: xxx.xxx.x.xxx). But I cannot connect to the Internet! Oh yes, the LEDs are lit/flashing on the card.

Any ideas for a relatively painless fix?

Merci for your time and thought.
 
Dapper (6.06) on a Toshiba Satellite Pentium II 366 MHz, 191 MB RAM

---

### Post by Ayuthia on 2009-01-25
If you are on Dapper, you might try using ndiswrapper instead.  I am not for sure about how well things worked for the bcm43xx module for that kernel version.  If I recall correctly, I used ndiswrapper when I was using Feisty and I was using a 4306 rev 03 card.  Here is a link on how to install it:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Hope that helps.

---

