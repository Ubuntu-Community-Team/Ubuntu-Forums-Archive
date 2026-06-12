---
title: "Unable to mount CIFS"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by badger_fruit on 2010-07-14
Hello all.
I am getting an error when I try to mount a CIFS file-system via terminal:

cifs_mount failed w/return code = -22

If I Places > Connect to server, it will open just fine. The share is also accessible from all the other computers on the network.

Google search brought me here to an archived thread which gave a different error number (!)
Please, if anyone has any ideas I am open to them!

Desktop is Ubuntu 10,4LTS/Gnome; fresh install with no additional packages installed (so it's possible I am missing something but not sure what!)

Thank you for reading and any help anyone can offer!

---

### Post by badger_fruit on 2010-07-14
[SOLVED] Stupid Ubuntu (ahem, read that as: my user error!!); didn't detect my network and add all the servers to the HOSTS file like it should ;)

Mounting with IP address instead of DNS name has resulted in a successful mount :)

---

