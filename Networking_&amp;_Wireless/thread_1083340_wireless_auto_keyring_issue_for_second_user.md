---
title: "wireless auto keyring issue for second user"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by tinytim174 on 2009-02-28
I'm the superuser, and when i log in after boot, the wireless just starts.  Doesn't prompt for the WEP key or the unlock keyring pwd.

Then if I switch user, to say 'user2', that user also just gets an auto wireless autologin.

However, if after re-boot, 'user2' logins in, they are prompted for the WEP key.  Afterwards, seahorse requests the unlock key, yet however many times that pwd is entered, it keeps requesting it.  Yet if you hit 'deny', the wireless connection starts.

I have gone to 'Applications > Accessories > Passwords and Keyrings', (as 'user2', however under 'Edit > Preferences', it will not accept the pdw.  I cannot add passwords either when i click on the 'password' tab (as it wont accept the password).

How can I get 'user2' to remember the WEP key and have access to the keyring?

---

### Post by tinytim174 on 2009-03-02
If someone could even suggest a 3rd party wifi manager, that stores wep keys and keyring for all users, then I'd happily give it a go

---

### Post by Yashiro on 2009-03-02
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by tinytim174 on 2009-03-06
thanks for that.

wicd works very well (after having to reconfigure the wep key).  also, for others, the gateway is your internal address, but range 254, something like 192.168.1.254 for example.

the dns1 is the dns your isp gives you, should be available in your routers config page.

The ip address is the address of the machine your using wicd on (so not necessarily your external ip)

---

