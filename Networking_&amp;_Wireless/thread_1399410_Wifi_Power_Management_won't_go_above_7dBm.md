---
title: "Wifi Power Management won't go above 7dBm?"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by rockyrobin on 2010-02-05
I'm currently using an Alfa AWUS050NH with Ubuntu Karmic and have it working with the default rt2800usb driver.

When I try to change the txpower setting I can only get as far as 7dBm. anything above this gives me the following error:

```
sudo iwconfig wlan0 txpower 8
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Invalid argument.

```

I've had a google about and came across:

```
iwpriv wlan0 highpower 1
```

Giving the following result:

```
wlan0     no private ioctls.
```

If anyone can offer me any suggestions on possible fixes would be very grateful.

---

