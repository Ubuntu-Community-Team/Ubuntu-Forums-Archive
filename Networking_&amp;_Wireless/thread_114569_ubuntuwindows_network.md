---
title: "ubuntu/windows network"
date: 2006-01-08
forum: Networking &amp; Wireless
---

### Post by pieboy314 on 2006-01-08
<-- ok, first linux newbie

got my network and samba and shares all set-up

I can log into all the windows machines from ubuntu machine,

and I can "see" the unbuntu machine from my windows machines, however I am unable to log into or navigate the unbuntu machine because I am unable to provide a username and/or password.

I suspect that it is looking for root username and password, but of course I am attempting play by the ubuntu rules and stay away from su and root logins.

---

### Post by gruepig on 2006-01-09
You need to create samba usernames/passwords (which are different from your login usernames/passwords; use the same username, but a different password).

From the command line, 'sudo smbpasswd -a <username>' to add the account and password or 'sudo smbpasswd <username>' to change the password once you've done the initial add.

You can probably also do this from the gnome or kde menus somewhere (maybe in users & groups).

---

