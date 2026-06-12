---
title: "Help with Cisco VPN and RSA SecureID"
date: 2010-04-22
forum: Networking &amp; Wireless
---

### Post by mlhudson on 2010-04-22
For work I occasionally must access a VPN. On my Mac setup was pretty seamless:
 
- installed VPN client and imported .pcf profile
- installed RSA SecureID client and imported token.
- ran both apps, RSA app asks for PIN and generates numeric passcode.
- logged in to VPN and entered RSA generated passcode.

How exactly to I repeat this on Ubuntu/Xubuntu? 

- Thanks to the wiki.ubuntu.com, I've got the Cisco VPN client plugin installed and active. 
- I was able to import my .pcf profile.
- Connection fails with out "secrets" and it asks for a password that I don't have.

That's as far as I can get. What do need to do to get netork-manager to act like the Mac RSA SecureID app? Or what else to need to install?

Thanks ahead of time to anyone who can help with this!

---

### Post by mlhudson on 2010-04-22
Follow up

Non-preferred workaround is this (and this may not be secure):
-On Mac, input the PIN and generate the Numeric Passphrase
-In Network Manager, connect to VPN, enter Passphrase generated on the Mac. Connection established.

Need 2 systems to log in?

---

