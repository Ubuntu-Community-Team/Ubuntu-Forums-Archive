---
title: "how do I see wireless"
date: 2011-03-16
forum: Networking &amp; Wireless
---

### Post by hill0093 on 2011-03-16
I installed ubuntu alongside windows 7 and 
don't know how to hook it up to the internet like win7.
I have only wireless where I am now.

---

### Post by hill0093 on 2011-03-16
Works on ethernet cable. I suppose I need to 
know how to get a wireless driver, right?

---

### Post by adduds on 2011-03-16
no drivers are usually built into linux unlike m$

you should be able to go to system --> prefs --> network connections 

under wireless set up your connection

running iwconfig should show wlan0

or ifconfig whichever..

if it doesn't check if ubuntu recognizes your card

running 
```
lspci -v | grep Wireless

```

---

### Post by hill0093 on 2011-03-17
I had ubuntu running on another computer a few years ago.
I think I remember that there was a repository where
it rather automatically downloaded the right stuff.
Am I wrong? How do I do such?

---

### Post by grahammechanical on 2011-03-17
What you may be looking for is under System>Administration>Additional Drivers. Activate any driver that is available.

Do you see a network manger icon in the top panel. When connected by ethernet it looks like two arrows going opposite directions. Left click it. Do you see a list of available wireless networks? If you do then wireless is working. Select your network and enter the wireless key or pass phrase. Not your log in password. Make sure that the encryption is the same as the type being used by the modem/router.

Regards.

---

