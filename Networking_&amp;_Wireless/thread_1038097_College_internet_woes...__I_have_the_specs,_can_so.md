---
title: "College internet woes...  I have the specs, can somebody help me set it up?"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by tegnoto89 on 2009-01-12
I keep getting kicked off my college internet service and it takes multiple attempts to reconnect..  The school suggests some settings for setting it up; can somebody help me out with this?

This is what the school gives me:

There is no official support for configuring linux ...
The latest Ubuntu and other distributions appear to work well out of the box with the exception of specifying the auth servers.
... if you get the supplicant compiled on other versions, here are the fundamental settings.

    * WPA-1 protocol (WPA).
    * TKIP session encryption.
    * PEAP authentication type.
    * MSCHAPv2 password encryption.
    * AuthServers secure1.syr.edu;secure2.syr.edu; 

These settings are NOT required for AirOrangeX and can be ignored:

    * Anonymous Identity
    * Client Certificate File
    * CA Certificate File
    * Private Key File
    * Private Key Password 



I've tried using Wicd, but I couldn't connect at all with that, so I'm afraid to install it again or I won't be able to come here for support.  HELP!!!  Thank you!!

---

### Post by stanz on 2009-01-12
Yeah, they always gave me the "no support for linux" jive...
To me - its work on their end - to do...to get you on their network.
It's password and authentication stuff that will get you on...

Sry I can't be of any better help...  ;)

---

### Post by tegnoto89 on 2009-01-13
Could this just be a "password nagging" issue?  I saw something about that on the documentation, but I didn't understand how to fix it...?

---

### Post by stanz on 2009-01-18
Hi...
Still no fix for ya?
"password nagging issue"?  - I would think that if it never accepts what you've entered.
The admin at my old school was kewl, and all he did was use the same login/password info - that any m$ user - used.
We did this in his office and 'wha la'.

Will they work with ya?

---

