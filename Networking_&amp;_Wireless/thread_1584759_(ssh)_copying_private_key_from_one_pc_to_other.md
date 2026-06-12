---
title: "(ssh) copying private key from one pc to other"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by infestor on 2010-09-29
i am logging on to ssh server from my laptop and i have my private key there but i would like to logon also from my desktop at home so how can i copy the key?

---

### Post by Jeroensum on 2010-09-29
Just copy the key you have on your laptop to your desktop with something like scp.

And this is a mini-mini-mini how to:

[I]user@laptop$ scp .ssh/id_rsa.key desktop:/home/user/.ssh/
[/I]

id_rsa.key should of course be replaced with the actual filename of your actual key ;)

---

### Post by infestor on 2010-09-29
i guess copying private keys is not the way to go...i have to generate a new pair.

---

