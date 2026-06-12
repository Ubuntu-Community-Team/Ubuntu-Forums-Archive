---
title: "USB dongle/bluetooth question"
date: 2012-08-25
forum: Networking &amp; Wireless
---

### Post by goodbye-windows(tm) on 2012-08-25
I have a USB dongle that works with my logitech mouse, which (I think) means it is bluetooth.

Can the logitech usb transceiver be used for communication other bluetooth devices?? I do understand that I probably can't use multiple wireless devices at the same time.

I'd like to use the usb transceiver to communicate with my cell phone, which is bluetooth capable.

And, I'd like to use my usb transceiver to communicate with the laptop to make calls using skype or google voice.

Are these things possible???

I tried searching for an answer, but got all kinds of hits, all presuming I knew bluetooth already-which I don't. 

Appreciate all info.

TY.

Art

---

### Post by Kirk Schnable on 2012-08-25
If the mouse "just worked", it's not Bluetooth.  It's probably a proprietary 2.4Ghz wireless variant that will only work with that mouse.

If, on the other hand, you used the Bluetooth icon up by your network manager\clock and you paired the mouse, then it is certainly Bluetooth.

If you plug it in, and give us the output of the command:
```
lsusb
```
We may be able to figure it out for you if you aren't sure.

Kirk

---

### Post by goodbye-windows(tm) on 2012-08-25
Also, one other question.............

Is a usb plugin transceiver used to create a wireless connection between my wireless router and my laptop the same as a wireless usb transceiver that is used for bluetooth communication to and from other wireless bluetooth devices?

TY.

Art

---

### Post by Kirk Schnable on 2012-08-25
No. WiFi is not Bluetooth.

Here is an example of a USB Bluetooth dongle:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833340012](http://www.newegg.com/Product/Product.aspx?Item=N82E16833340012)

Here is an example of a USB WiFi dongle:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833315091](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315091)

Bluetooth and WiFi are two different standards completely.
[http://en.wikipedia.org/wiki/Bluetooth#Bluetooth_vs._Wi-Fi_.28IEEE_802.11.29](http://en.wikipedia.org/wiki/Bluetooth#Bluetooth_vs._Wi-Fi_.28IEEE_802.11.29)

Kirk

---

### Post by goodbye-windows(tm) on 2012-08-25
> **Kirk Schnable said:**
> If the mouse "just worked", it's not Bluetooth.  It's probably a proprietary 2.4Ghz wireless variant that will only work with that mouse.

If, on the other hand, you used the Bluetooth icon up by your network manager\clock and you paired the mouse, then it is certainly Bluetooth.

If you plug it in, and give us the output of the command:
```
lsusb
```We may be able to figure it out for you if you aren't sure.

Kirk

Thanks Kirk,

Here's the output:

```
mine@mine-Aspire-3680:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
 mine@mine-Aspire-3680:~$
```

Art

---

### Post by Kirk Schnable on 2012-08-27
I can see how this might be confused with Bluetooth.  But rather than Bluetooth, this looks like a Logitech proprietary "Bluetooth-like" radio.  It looks like you CAN have multiple devices connected to this at once, but they must be Logitech Unify supported. 

So it's not Bluetooth, as I suspected.

Kirk

---

