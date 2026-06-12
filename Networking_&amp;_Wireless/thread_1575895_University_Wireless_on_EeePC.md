---
title: "University Wireless on EeePC"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by Epidural on 2010-09-16
I'm using the 10.04 Netbook Remix on an Asus EeePC. My home router connects fine with WPA-Personal, but the University (U of Ottawa) campus wireless does not.

The IT department told me to:
-Install wpa_supplicant
-User certain network criteria (PEAP Version 0, etc)

I've set the criteria, and "wpasupplicant" is installed, however "wpa_supplicant" does not exist when using apt-get.

The wireless will not connect; it simply keeps asking me for the userid/password, which I know to be correct.

Do I need to find this wpa_supplicant somehow? Or would the problem be elsewhere?

---

### Post by msrinath80 on 2010-09-16
Use these[1] settings. Certificates can be found in /etc/ssl/certs. Also this[2] might help. It's easier than rocket science. Give it a go :)

References:

[1] [http://www.ccs.uottawa.ca/connect/wireless/config-wpa-vista.html](http://www.ccs.uottawa.ca/connect/wireless/config-wpa-vista.html)
[2] [http://www.ccs.uottawa.ca/connect/wireless/config-wpa-linux.html](http://www.ccs.uottawa.ca/connect/wireless/config-wpa-linux.html)

---

### Post by Epidural on 2010-09-16
I can connect on Windows7 (Starter). The second link you sent me is the exact printout that the IT people gave me; however it's just not working. As I said, I can't find the "wpa_supplicant" package, and "wpasupplicant" is already installed. 

Could there be an error in their instructions? Or would this be one of those "Oh, we need to reset your account" situations?

I can't connect right now (in my res room), but during my next class I'll try to connect using their settings AND the "Thawte Premium Server CA" certificate found in the certs directory and post the results.

---

### Post by msrinath80 on 2010-09-16
I'm pretty sure, the certificate is necessary.

---

