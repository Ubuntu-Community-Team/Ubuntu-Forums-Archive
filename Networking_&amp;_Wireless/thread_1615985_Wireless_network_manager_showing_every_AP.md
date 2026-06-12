---
title: "Wireless network manager showing every AP"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by W3N4 on 2010-11-07
Hi,
I need a wireless network manager which shows every access point with the same SSID which I can connect to.
NetworkMannager which is default network manager in Ubuntu shows just the nearest AP which doesn't work properly in my case. Therefore I need to connect to another AP which is a bit further but work well.

Is there something like that ?

---

### Post by P4man on 2010-11-07
network manager does show all APs :confused:

edit: oh wait, you have duplicate SSIDs. Well.. I have no idea, never tried that.

---

### Post by W3N4 on 2010-11-08
> **P4man said:**
> edit: oh wait, you have duplicate SSIDs. Well.. I have no idea, never tried that.
Yeah, that's my point. The APs have the same SSID (the same internet connection).

I should've explained it better.

---

### Post by SeijiSensei on 2010-11-08
That's bad practice for exactly the reasons you're having a problem now.

If all the APs provide the same connectivity, what difference does it make which one you connect to?

---

### Post by W3N4 on 2010-11-08
As I said, the only AP which is shown to me doesn't work properly (sometimes, I can't even connect at all). Therefore I would like to connect to another one.

---

### Post by spiky001 on 2010-11-08
Have you tried to scan from terminal ```
sudo iwlist "wireless interface" scan
```

---

### Post by W3N4 on 2010-11-08
This is what terminal returns whwn I attempt:
```
wireless interfa  Interface doesn't support scanning.
```

---

### Post by spiky001 on 2010-11-08
the wireless interface should be something like wlan0 that is what my wireless is yours might be different, ifconfig will tell you what it is

---

### Post by puppywhacker on 2010-11-08
you can also do the scan without writing the wlan0, it will just try all devices, including the wireless one.
```
sudo iwlist scan
```

The point of this scan is that it will show you the accesspoints. The ESSID is just a name for the wireless accesspoint that you can choose also if you have 2 AP's with the same name, the connection is done based on the mac address that will show in the iwlist scan.

you can then use this address to bind to the other accesspoint with the same name

```
sudo iwconfig wlan0 ap 00:02:CF:98:D8:E2
```

Ofcourse replace wlan0 with your device name, and the 6 hex with your own mac address

---

### Post by W3N4 on 2010-11-08
Yeah, it is wlan0. 
So, I have the list of the APs. But how to connect to any of them ?

//Solved, to puppywhacker: thanks a lot :)

---

### Post by spiky001 on 2010-11-08
Do they now have different ssid's? is that what you was looking for

---

