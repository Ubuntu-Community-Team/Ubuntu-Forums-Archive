---
title: "WiFi can connect everywhere but home network"
date: 2012-03-06
forum: Networking &amp; Wireless
---

### Post by MonthOLDpickle on 2012-03-06
I have a HP Pavilion dm1 with a Ralink 5390. I use 32 bit Ubuntu (64 bit W7) and my wifi is having an issue with my home wifi.

I can connect everywhere else but home. I go to connect (wifi can see my network), enter in password and it sits there doing its animation thing.

Than the password window pops up again. Its the right password, I checked.

How can I force or make it connect to my home wifi?

---

### Post by Bucky Ball on 2012-03-06
Could you provide the Ubuntu release you're using and the output of:

```
iwconfig
```... from a terminal. Incidentally, why are you running 32bit and not 64?

You have static IP addresses set up or the router is serving you an IP address (or your ISP is)?

If you right click the network icon and check wireless, are the details correct there to match your router (ESSID, security, etc). Try putting password in there rather than the pop up window and make sure you're using the right security type - WEP, WPA - for the details in your router.

---

### Post by MonthOLDpickle on 2012-03-06
> **Bucky Ball said:**
> Could you provide the Ubuntu release you're using and the output of:

```
iwconfig
```... from a terminal. Incidentally, why are you running 32bit and not 64?

You have static IP addresses set up or the router is serving you an IP address (or your ISP is)?

If you right click the network icon and check wireless, are the details correct there to match your router (ESSID, security, etc). Try putting password in there rather than the pop up window and make sure you're using the right security type - WEP, WPA - for the details in your router.

I have Ubuntu installed on a USB. That is why I have a 32 bit Ubuntu, which I believe is fine. Its just in case i have to pop it into some one else's machine.

I will post the results when I get up tomorrow. Also I believe the ISP or router provides IP. Nothing is special on the router.

---

