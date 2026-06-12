---
title: "I have to do it everytime!!!"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by EI51 on 2009-08-12
Hi Their,
Everytime I boot up Ubuntu Hardy I have to retype my WPA passkey to get a connection, then I'm up and running but I still have to do it everytime.  Is there a better way to save that info? I'm also wondering if there is something I need to change in the WPA sinificant config file so it will connect at boot?  Any suggetions? Thanks in advanced.

---

### Post by aysiu on 2009-08-13
Go to /home/*username*/.gnome2/

And rename the keyrings directory.

Then the next time you log in, you'll be prompted to set up a keyring password. Leave the password blank.

---

### Post by EI51 on 2009-08-13
Ok, that sounds easy enough. What should I rename the directory?

---

### Post by aysiu on 2009-08-13
> **EI51 said:**
> Ok, that sounds easy enough. What should I rename the directory?
*keyrings.old*, I guess.

---

