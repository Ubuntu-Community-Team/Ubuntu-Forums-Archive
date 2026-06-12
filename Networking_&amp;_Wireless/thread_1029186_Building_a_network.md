---
title: "Building a network"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by gramsyn on 2009-01-03
I have a PC (which is connected with a LAN cable to the wireless router) and a laptop. I have found the wireless connection from the laptop and I can connect to the Internet. How can I set up a network with the PC and the laptop?

---

### Post by superprash2003 on 2009-01-03
you mean sharing files?? for this you need samba [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html)

---

### Post by ieee488 on 2009-01-03
> The following packages have unmet dependencies:
  samba: Depends: samba-common (= 2:3.2.3-1ubuntu3) but 2:3.2.3-1ubuntu3.3 is to be installed
  smbfs: Depends: samba-common (= 2:3.2.3-1ubuntu3) but 2:3.2.3-1ubuntu3.3 is to be installed
E: Broken packages


How do I resolve that?

EDIT: 
nevermind, [https://answers.launchpad.net/ubuntu/+source/samba/+question/42691](https://answers.launchpad.net/ubuntu/+source/samba/+question/42691) removed the problem

---

### Post by Iowan on 2009-01-04
> **gramsyn said:**
>  How can I set up a network with the PC and the laptop?You didn't mention which OS is on what computer.  Samba will work.  If both machines are Ubuntu, there are at least a couple more options: NFS and SSHFS.

---

