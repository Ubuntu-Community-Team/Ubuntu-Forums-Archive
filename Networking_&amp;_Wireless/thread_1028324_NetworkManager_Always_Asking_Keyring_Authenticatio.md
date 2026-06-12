---
title: "NetworkManager Always Asking Keyring Authentication"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by vonsperb on 2009-01-02
I'm using autologin in Ubuntu 8.10 and whenever I boot up my system, the NetworkManager Applet asks for Keyring authentication. I think it's because it needs access to my wireless network key. Anyway, how can I get rid of this anoyance? Is there a way to grant permanent access to NetWork Manager for the Keying? Thanks!

---

### Post by Martin Marshalek on 2009-01-02
Yes, there is! I just found it!

First do this (for me it was already installed):
```
sudo apt-get install libpam-keyring
```

Then run this command:
```
echo "@include common-pamkeyring" | sudo tee -a /etc/pam.d/gdm
```

And, just in case your keyring password isn't the same as your login, run this to change your keyring password:
```
/usr/lib/libpam-keyring/pam-keyring-tool -c
```

---

