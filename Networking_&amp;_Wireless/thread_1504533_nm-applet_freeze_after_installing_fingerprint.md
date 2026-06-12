---
title: "nm-applet freeze after installing fingerprint"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by willyboy666 on 2010-06-08
i got problem ,yesterday i installed libpam and the fingerprint stuff(and i got it to work )
after i restarted the pc ,the network manager could not connect anymore .

nm-applet freeze when i press on it (sometime it doesnt start)
i am not able to connect to internet with cable or wifi.

i suspect that the keyring has something to do with it??


please help

---

### Post by willyboy666 on 2010-06-08
any help

---

### Post by Bombenbach on 2010-06-16
Don't use fingerprint to log in, but enter your password instead. It's O.K. to use fingerprint for sudo and gksudo and stuff like that , but **not** on the login screen. For more information see this bug
[https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/529338](https://bugs.launchpad.net/ubuntu/+source/seahorse/+bug/529338)

---

