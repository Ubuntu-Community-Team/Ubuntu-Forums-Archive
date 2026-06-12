---
title: "keyring troubles"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by u_kapaley256 on 2009-09-24
Hi,
i recently changed from gnome to xfce and reinstalled empathy.
But the keyring had messed up and empathy tells me 'authentication failure'
I removed all the keyrings
Then i found out about seahorse(slightly late i think)
so i created this new keyring over there and it does ask me for the password to my empathy accounts but when i enter them i get the message 'access to the keyring is denied'

As far as i know empathy is the only client that allows me to do voice chat with gtalk

What do i do?

Thanks.

---

### Post by donato roque on 2009-09-30
What seahorse is asking is the password for the folder which includes empathy.  Empathy automatically stores passwords in seahorse.  Seahorse wanted the password when the keyring (folder) was created.  Please make sure that seahorse is automatically synching with a server of your choice. 
If all else fails delete the keyring (right-click) and start from scratch.

---

