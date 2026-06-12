---
title: "Wicd and encryption keys?"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by Sanus Compleo on 2009-05-01
So... Why doesn't Wicd work with an encryption key?

---

### Post by 73ckn797 on 2009-05-01
Please be more specific of your situation.

---

### Post by kerry_s on 2009-05-01
use the tiny drop down arrow> click advanced settings> click use encryption

---

### Post by Sanus Compleo on 2009-05-01
Sorry for not being specific folks, I'm running 8.10 on a Dell Inspiron 600m, and recently I needed to set a static IP, so I went and got wicd.  Trying to connect to the internet that way with the passphrase (The correct passphrase at that) did not work, it got all the way up to "Obtaining IP Address" then stalled until it went to "No connection" again.  At home I disabled the encryption so I could at least connect to the internet.  Right now I'm at a friend's house and need to connect to the internet, I wouldn't ask him to remove his encryption, but I do need to get on the internet.  If anyone could help, that'd just be fantastic.  Encryption is WEP btw.

---

### Post by kerry_s on 2009-05-01
have you rebooted since installing wicd?
did it uninstall network-manager or are they both running?

---

### Post by yogo on 2009-05-01
> **Sanus Compleo said:**
>   Encryption is WEP btw.


Just select WEP (HEX) and make sure you are using HEX, if you use asii, that is Windows and Ubuntu will not be able to authenticate.

---

### Post by Sanus Compleo on 2009-05-02
Of course I rebooted, and yes I was using ascii characters.  How would I go about getting the hex characters?  And why is there even an option if Ubuntu can't support it?  I thought I left those problems behind with Microsoft.

---

### Post by yogo on 2009-05-02
> **Sanus Compleo said:**
> Of course I rebooted, and yes I was using ascii characters.  How would I go about getting the hex characters?  And why is there even an option if Ubuntu can't support it?  I thought I left those problems behind with Microsoft.
   This is the easy part, just Google WEP key generator and choose HEX.

This will do it for you.

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

ETA There is not an option, you just entered asii where you should have entered HEX.

---

### Post by Sanus Compleo on 2009-05-03
Okay, got the Hex Key, set it in as WEP (HEX) for the encryption aaaaaaaand nothing.  I have the right passphrase as well as the exact hex translation.  Still nada.  Any other ideas?  Maybe the Open Source gods just hate me?

---

