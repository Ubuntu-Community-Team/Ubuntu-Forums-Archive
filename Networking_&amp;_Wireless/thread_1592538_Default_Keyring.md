---
title: "Default Keyring"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by joshh88 on 2010-10-10
I just did a fresh install of 10.10 and whenever i log on it request the password for default keyring(the same as sign in password) in previous versions of ubuntu it never asked and automatically started the wireless; now it asks and tells me the password is incorrect. I can hit cancel a numerous amount of times and it will eventually allow me to connect, but that doesn't seem like a good fix in my opinion. This also happened when I tried out lubuntu 10.04 which I promptly removed due to the menu style. Thanks in advance :)

---

### Post by joshh88 on 2010-10-11
I forgot it also asks me to input the password for the wireless everytime.

---

### Post by K_REY_C on 2010-10-11
Yes --- this seems to be a fairly common issue. It is happening to me as well.

Under "Passwords and Encryption Keys" I had a "login" and a "default" (and default contained everything from Gwibber to network manager passwords). I deleted the default and now when I try to re-set-up services for Gwibber it tells me that the application is creating a "default" keyring to store it in.

How do we make Gwibber (and other apps) default to the "login" keyring?

Thanks,

KYLE

---

### Post by K_REY_C on 2010-10-11
FYI: Just saw a potential solution here --- [http://ubuntuforums.org/showthread.php?p=9938975](http://ubuntuforums.org/showthread.php?p=9938975)

And the potential solution works.

---

### Post by joshh88 on 2010-10-11
Awesome thanks worked like a charm

---

### Post by repunante on 2010-10-13
> **K_REY_C said:**
> FYI: Just saw a potential solution here --- [http://ubuntuforums.org/showthread.php?p=9938975](http://ubuntuforums.org/showthread.php?p=9938975)

And the potential solution works.

Great, thanks, that issue was driving me crazy.

---

