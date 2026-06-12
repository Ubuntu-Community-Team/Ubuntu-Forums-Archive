---
title: "WEP key demanded on every startup"
date: 2011-12-23
forum: Networking &amp; Wireless
---

### Post by b9k9kiwi on 2011-12-23
Ubuntu 11.10

I have my WiFi connection set to automatic logon and, up until recently, could logon using my keyring password only.  Recently, though, the system has demanded the WEP code as well which, although not exactly a chore, is something of a nuisance.

I am presuming that an update has reset something somewhere by overwriting a config - but what/where?

Any clues or hints would be appreciated.

---

### Post by Paddy Landau on 2011-12-23
Your keyring is encrypted for security. It is automatically unlocked when you log in by entering your password -- but, of course, not when you have automatic login.

To the best of my knowledge, there are only two ways around this:

[LIST=1]
[*]Remove the password on your keyring (not advised for obvious reasons).
[*]Don't have automatic login (this is what I usually recommend). With this, you type your password just once, when you log in, and everything works after that.
[/LIST]
Also, the WEP protocol is outdated and can be cracked within seconds -- you might as well turn it off. I would strongly recommend that you change your router's security from WEP to WPA.

---

