---
title: "Home network"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by gsamsa on 2008-12-29
Hi,

I have 8 linux PCs at home, scattered by several places (bedrooms, kitchen, basement, living room, etc). What i would like to have was a common HOME folder, and common authentication too. A way that an user could authenticate in any computer and have his wallpapers, configurations, some docs, etc. Adding an user would mean also that the new user would be able to authenticate in any random PC.
How can i implement this system? Can you point me in the right direction? 
Thank you.

---

### Post by albinootje on 2008-12-29
> **gsamsa said:**
> Hi,

I have 8 linux PCs at home, scattered by several places (bedrooms, kitchen, basement, living room, etc). What i would like to have was a common HOME folder, and common authentication too. A way that an user could authenticate in any computer and have his wallpapers, configurations, some docs, etc. Adding an user would mean also that the new user would be able to authenticate in any random PC.

If you trust all users on your local network you can choose NFS + NIS.
NIS for authentication, and NFS for the /home
That's fairly easy to do, but usernames+passwords will go as plain-text over the network traffic.

Much more secure is LDAP with SSL and Samba, but that's not so easy to set up for the first time.

---

