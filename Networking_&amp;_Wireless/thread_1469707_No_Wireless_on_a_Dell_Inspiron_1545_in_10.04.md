---
title: "No Wireless on a Dell Inspiron 1545 in 10.04"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by Cerin on 2010-05-02
I just bought a basic Dell Inspiron 1545 and installed Ubuntu 10.04. Everything seems to work fine, except for wireless internet. I tried using the "Hardware Drivers" dialog to install the propreitary Broadcom STA driver, but that did nothing.

I then tried following the advice at [http://ubuntuforums.org/showthread.php?p=8747122](http://ubuntuforums.org/showthread.php?p=8747122) to install Linux headers, modify the driver's sourcecode, and recompile, but that mysteriously fails as well.

Can anyone please help me how get my wireless working?

---

### Post by Megaptera on 2010-05-02
Hi,
This worked on my Dell 1545 with 10.04, I know it's shown in the link you quote but have you tried it? Remembering to re-boot afterwards.

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by Cerin on 2010-05-02
No, I don't think that's the problem. "Hardware Drivers" shows the "Broadcom STA wireless driver" is "activated and currently in use".

I've rebooted, but the Network Manager applet shows that "wireless is disabled". So it's simultaneously activated and disabled. This thing's driving me nuts.

---

### Post by Justice Bucket on 2010-05-16
Any solutions? I'm in the same boat...

---

### Post by kage52124 on 2010-07-01
I have the same problem with this laptop.  All drivers are installed and I can get the internet working IF I press the wireless switch (normally F2, but this keyboard is backwards it seems; F2 will switch on/off internet, while Function+F2 behaves as it would on a 'standard' keyboard) BEFORE typing the password.  This seems to catch it early enough so that it can scan and find a wireless connection.

If done too late, pressing the button will activate the wireless, but it never will find a connection, even after several hours of being on.

Any ideas?

P.s. Model number PP41L

---

### Post by kage52124 on 2010-07-21
bump

---

### Post by Cerin on 2010-07-21
The solution for me was pressing the "wireless" button to toggle the wireless on. I've never had a PC laptop before with builtin wireless, so it was a basic newbie mistake on my part (why do you need a button to turn wireless on?!).

Once I toggled that, Network Manager finally showed a signal and I could connect using the proprietary driver.

---

### Post by corncob on 2010-07-21
I'm on my wired desktop right now so I can't check it out but isn't there something like
```
rfkill list all
``` ?
And if it shows something is blocked:
```
rfkill unblock all
```

---

### Post by bkratz on 2010-07-21
> **Cerin said:**
> The solution for me was pressing the "wireless" button to toggle the wireless on. I've never had a PC laptop before with builtin wireless, so it was a basic newbie mistake on my part (why do you need a button to turn wireless on?!).

Once I toggled that, Network Manager finally showed a signal and I could connect using the proprietary driver.



There are times, like riding in an airplane, where wireless devices must be shut-off ( just in case it has some effect on the plane).

---

### Post by DJohnson1966 on 2010-07-22
Result, it works, press the f2 key once the log in page is there and then log in, never got it to work on my d505, but it works on this inspiron 1545 ;)

---

### Post by kage52124 on 2010-07-27
Please not that pressing that key quickly is only a workaround, please do not consider this completely solved as I'm still having trouble with it.

---

