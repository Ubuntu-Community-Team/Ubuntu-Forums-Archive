---
title: "I want to password protect the wireless network selector"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by yaakov-belch on 2009-08-07
In short: 

How can I ensure that normal users can't connect to the wireless LAN but administrators can?

In more detail:

With the standard setup, ubuntu (remix/netbook) automatically connects to the available wireless LAN and allows all users to select a network to be used (by clicking on the "Wireless connection" icon).

I want to protect this action with the administrator password:  On normal bootup, no automatic connection should be established and normal users shall not be able to select a wireless network connection (that means: no Internet for normal users).  However, the administrator shall be able to select a wireless network after authentication.

How can this be achieved?

Thanks for any hints...

---

### Post by yaakov-belch on 2009-08-09
[B]Non-perfect solution

[/B]Here is what I did to solve my problem.  This solution is not perfect: It will cause problems when automatic security updates arrive for wicd.  So, if you know any better solution, please let me know.

**(1) Replace network-manager by wicd:** WICD is another network manager.  It is somewhat more configurable than the default network-manager.  For my purposes it's important that I can set it not to connect to the Internet automatically on startup.  It may be possible to achieve the same effect with network-manager.  I didn't try this...

**Note:** I first removed network-manager which automatically disconnected the wireless LAN connection --- making it more difficult to install any new software.  In particular, the old network-manager is gone; so I could not go back to the previous state and use it to connect.  Fortunately, I had an ethernet cable and used eth0 to install wicd.

**(2) Change ownership and permission for wicd-client:** WICD consists of two parts: A server (which does the real work) and a user client that accepts the requests from users and passes them on to the server.  I then logged in as root and issued these commands:
```
[INDENT]chown *admin-user* /usr/bin/wicd-client
chmod a-rwx /usr/bin/wicd-client
chmod u+rx /usr/bin/wicd-client[/INDENT]
```(*admin-user* should be replaced by the user name of the administrator).  Due to these commands, the wicd-client program is now owned by the *admin-user* and nobody else is permitted to read or execute it.

As a result, the *admin-user* can connect to the Internet as usual but all other users are unable to do so.

**What's bad about this solution?** When Ubuntu's package system wants to write to the wicd-client program (e.g. for installing security updates), this will either fail (due to the restictive permissions) --- leaving the system without the security update.  Or it will succeed and reset the normal access rights --- reverting to the original state where everybody can connect to the Internet.

---

