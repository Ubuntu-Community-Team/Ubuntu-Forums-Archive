---
title: "Non-root user cannot connect to wifi"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by Paresh on 2009-09-10
Hi

I have a laptop dual booting vista and ubuntu

I have a standard admin account (first user on install) and a user account set up with Desktop profile (no other changes yet).

The admin can connect to the wifi network and so can the user if logged on at the same time.

However, if the laptop is restarted and the user logs in without admin logging in, you get the authentication dialog with the key pre-filled in but the user cannot connect.

At the moment, the user can only connect if admin logs in first.

Is there any fix for this?

---

### Post by kimberlite on 2009-09-10
Try to modify user's setting (applications-administration-users and groups menu). You need to be a superuser to do so. Select the user you want to allow to connect to wifi, than "properties" button than "user'rights" tab. There you will find "connect to ethernet and wifi network". You should select the box to allow this option for your non admin user.

---

### Post by Paresh on 2009-09-11
This is done, but I still have the same problem.

is there anything else I should look for?

---

