---
title: "How to increase the Tx power of my wireless cards?"
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by zozza on 2011-07-29
Hello,
 
I have a wlan0 which is Atheros AR928X and wlan1 which is Alfa AWUS036H

 I thought I could set iwconfig wlan0 txpower [higher than 20] but any value more than 20 results in:
 
 Error for wireless request "Set Tx Power" (8B26) :
     SET failed on device wlan0 ; Invalid argument.
 
I get the same error for wlan1 when trying a value higher than 27.

 Is there a way of increasing the TX power and if not then why not?

 Many thanks.

---

### Post by bkratz on 2011-07-29
> **zozza said:**
> Hello,
 
I have a wlan0 which is Atheros AR928X and wlan1 which is Alfa AWUS036H

 I thought I could set iwconfig wlan0 txpower [higher than 20] but any value more than 20 results in:
 
 Error for wireless request "Set Tx Power" (8B26) :
     SET failed on device wlan0 ; Invalid argument.
 
I get the same error for wlan1 when trying a value higher than 27.

 Is there a way of increasing the TX power and if not then why not?

 Many thanks.


I am sure those levels are the maximum available (of course that depends on your device and country). You will not be able to go any higher than the allowed limit to protect others against your signal.

---

### Post by chili555 on 2011-07-29
If you have increased the power up to the point it errors out then I'm afraid that's as far as the manufacturer built in to the card. That's done so the card doesn't overheat and fail, melt or use a lot of power in a laptop, where battery life is a significant selling point. As well, in some places, transmit power is subject to legal limitation: [http://en.wikipedia.org/wiki/Wi-Fi](http://en.wikipedia.org/wiki/Wi-Fi)> In general, the maximum amount of power that a Wi-Fi device can transmit is limited by local regulations, such as FCC Part 15 in USA.I know of no way to circumvent these limitations.

---

### Post by chronos00 on 2011-09-09
What you need to do is to disable the above stated limitations.
For an example, you can check the following URL:
[http://www.clshack.it/en/backbox-ubuntu-alfa-network-awus036h.html]("http://www.clshack.it/en/backbox-ubuntu-alfa-network-awus036h.html")

In short, you need the following commands:

```
sudo iw reg set BO
iwconfig wlan1 txpower 30
```

We aware that using more power than the default configuration is risky and at you responsibility. This is because the wireless chip may state that it "can" transmit with higher power, but the device's manufacturer probably did not place the appropriate heat sink in order to accomplish this. Result: toasted wireless interface.

Once again, use this configurations carefully, and don't leave the card working in high power mode unattended.

Regards!

---

