---
title: "CIFS Mount and Umount"
date: 2011-06-22
forum: Networking &amp; Wireless
---

### Post by amainejr on 2011-06-22
I've been looking through the forums and kind of hit a stand still with what I'm trying to do.  I've got an install of server 11.04 in a virtual machine with windows 7 as the host.  I've connected to windows 7 using cifs in the /etc/fstab file.

What I am wanting, is to be able to limit access to one specific user, in a manner that the network file mappings will not be visible by anyone else, except root obviously.  The other option I would settle for, is to only mount those shares when I login with that user.  I know how to set it up with the login action, but how can I make sure that no one else can access it while I am logged in on that uid?

---

### Post by amainejr on 2011-06-22
Ohh, I forgot to mention.  CIFS only allows me to pass credentials to windows for the administrative user.  I've changed windows security permissions to add the intended user to the share and given it full control, but I get an access denied error.  Any thoughts on this?

---

