---
title: "network manager keyring access"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by pullrode on 2009-07-04
I am using jaunty jackalope and since changing my login password, network manager asks for default keychain access on startup.
It will not accept the new password and I have to enter the old one to get wireless network access.
How can I change this?

Pullrode

---

### Post by Brandon Williams on 2009-07-05
When you change your login password, it does not automatically update your keyring password. Go to 'System -> Preferences -> Encryption and Keyrings' and change the unlock password for your login keyring to make it match your new login password. As long as the two match, the login keyring will be automatically unlocked when you login via gdm.

---

