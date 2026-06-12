---
title: "Can't connect to wifi using any network manager"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by xdeathcorex on 2010-12-26
Hey guys, i was fed up after i can't connect to wifi using ubuntu. the problem happened after my router is being replaced to a new one  because the old one got struck by lightning. good thing i dual-boot my laptop so i can access the internet using Windows 7 now.

i use the default network manager to connect to wifi before, but it all seem to be failed after the replacement of router. i also used Wicd but it failed to connect either. it says in the notification "disconnected: bad password" but the password was right. my wifi used WEP password with open authentication.

i even remove the WEP password and try to connect, but it failed. all i can do is to boot in windows 7 and surf internet there. what could cause this problem? is it the router, the telephone line? i can set the router settings if i want, but i don't know what causes the problem.

thanks

---

### Post by hugmenot on 2010-12-26
In wireless it is often problematic to find out why the key is wrong. There is no clear feedback.

Please verify exactly what type of key is being used now.

WEP can use four numbered keys: key index 1, 2, 3 and 4.
Also, WEP can use hex, ascii, and passphrase (which is hashed).

The length of the key can help to eliminate which type it should be. 5 and 13 characters is ascii, 10 and 26 is probably hex, and everything else must be passphrase.

And finally it could be something else than WEP, maybe WPA.

---

