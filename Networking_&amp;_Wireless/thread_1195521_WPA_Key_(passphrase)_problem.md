---
title: "WPA Key (passphrase) problem"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by dougbott on 2009-06-23
Okay, So I am trying to manually scan and find my AP. and connect to it.
I am able to find non-secure AP and connect with no problem. But when I try and enter my Key for my WPA2 encod-ation ;) I get this error message stopping me from connecting. I have searched the forums, and maybe have missed a link to the same problem. If there is a link someone send me there... if not I would appreciate the help

Thanks..

BTW

this is my basic syntax, and other important information.

**iwconfig wlan0 essid "Ordinator" key s:<ASSCI passwd>**

and the error message i get is

[B]Error for wireless request "Set Encode" (8B2A) :
     SET failed on device wlan0 ; Invalid argument.[/B]

Any information would be great, I have check ifconfig, and iwconfig Manuals, and they arn't hinting to something.

Thanks.

---

### Post by kevdog on 2009-06-24
You can't pass the WPA passphrase using the format you describe -- thats for a WEP key.  You need to use wpa_supplicant to complete the handshake.  I wrote a tutorial on how to do this --- connecting manually -- link in my signature.

---

