---
title: "New router - laptop works, desktop doesn't"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by Maheriano on 2009-11-18
I bought a D-Link DIR-628 switch (or router as people call them) and had a hell of a time getting my laptop to connect to it. I had to reboot my modem, reboot the router, reboot my computer, deactivate encryption, reactivate, change SSID.......finally I got the laptop to connect and now it's bulletproof. I can change any of the settings on the router and reconnect on my laptop, it works great.

Now I'm trying to get my desktop to connect via wireless as well and it's not working....kind of. I have the router broadcasting at 2.4Ghz on both N and G. My laptop is N and my desktop is G. If I remove encryption on the router, I can connect both no problem, but if I enable encryption, only my laptop will connect, my desktop will not. The symptoms on the desktop are that it'll see the SSID, I can click on it, it asks me for the password, tries to connect, then asks for the password again.

Any ideas? Can this router not use both G and N at the same time? That wouldn't make sense if it works without encryption. Is it just because I've never paired the 2 before and it's being cranky like my laptop was?

---

### Post by teward on 2009-11-18
Try doing this instead:

Encrypt the connection with **only a password, not MAC filtering**.  Then, try broadcasting as G only; see if it works.  Then try broadcasting as N only; see if it works.  If N works with both computers when G is disabled, then you're fine.

Also, try connecting your desktop to the router directly via an ethernet cable, and see if it works.


if its due to MAC filtering, did you add the MAC address of your desktop to the allowed list?

---

### Post by Maheriano on 2009-11-18
There's no MAC filtering enabled.

---

### Post by williejones on 2009-11-18
So you can connect both without password? Then the desktop has no connection issue, but has secured connection issues.  Are you running the same versions on both the laptop and desktop?

---

### Post by Maheriano on 2009-11-19
Yes, Ubuntu 9.1 on both laptop and desktop. I tried setting the router to broadcast G only and both will connect with WPA2 encryption enabled on G. But if I broadcast G and N, it will only connect on the laptop.

---

### Post by teward on 2009-11-19
Wow, so we narrowed it down to that your desktop doesn't like the conflicting signals.  Did you try broadcasting only as N?

If you did, what happened?

I've seen this in networks where they have the router and a wireless accesspoint nearby each other (two conflicting signals :P), and only one device could connect:  my laptop.  I have similar problems here at Carnegie Mellon University, where I am attending school, and my desktop and laptop both can't connect to the wifi at once, partly because it broadcasts both G and N.

But, I digress.  Perhaps its your Desktop's network card not being able to differentiate between the two signals.  Are they both broadcasting on different channels?

---

### Post by Maheriano on 2009-11-20
Got it! I realized all I had to do was go into the admin section of the router from my laptop and click the REBOOT button to reboot the router, then it worked perfect. I had been unplugging it to reboot it but apparently that doesn't work. So all is well, thanks for your suggestions!

---

