---
title: "Unlock Keyring Prompt for wireless."
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by FahadMKS on 2010-03-25
Hi.. I am getting a prompt namely unlock keyring when i start up my PC and when i type in my password my wireless gets connected automatically... I didnt have this issue before.. My wireless onnection used to start up automatically when i start my PC... Please tell me what is this issue and how to take it back to normal.

---

### Post by quixote on 2010-03-26
Is this happening every time you connect to the wireless?  It can happen once in a rare while for no apparent reason, but it shouldn't happen constantly.

Did anything change between when it worked normally and now?  Any upgrades applied?  Also, which version are you using?  Jaunty 9.04?  karmic 9.10?  Or maybe kubuntu?

One thing to remember is that at least in gnome (ie ubuntu rather than kubuntu), the system won't let you both login automatically and get on the wireless automatically.  If you set one to be automatic, the other will demand a password.

---

### Post by macogw on 2010-03-26
Most likely, you did one of the following:
- Turned on autologin
- Changed your password

The keyring is automatically unlocked when you type your password to login *IF* your keyring and user password match.  

If you want to take the security risks involved in having autologin AND a keyring with no password... you can go to Applications -> Accessories -> Encryption-something-or-other  then right click on the login keyring and change its password to blank.

If you changed your user password, then do the above but change your keyring password to match your new user password.

---

### Post by jcoles on 2010-03-26
Go to System > Preferences > Network Connections. Select the Wireless tab. Select your connection and then select the Edit button. You'll have to authenticate. At the bottom of the settings, make sure that "Available to all users" is enabled. Select Apply.

On the next restart, your wireless network access will start without asking for the keyring password.

---

### Post by FahadMKS on 2010-05-08
Thanks Guys.  You all are great and have helped me with the issue.

---

