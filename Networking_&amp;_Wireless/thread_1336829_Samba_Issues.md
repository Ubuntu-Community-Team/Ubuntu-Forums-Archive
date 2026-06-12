---
title: "Samba Issues"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by chessnerd on 2009-11-24
I am trying to set up samba sharing on my laptop. 

I have configured the firewall the same way that it is configured under my desktop (which can detect other computers) and I have read and taken all the advice from [this guide]("http://ubuntuforums.org/showthread.php?t=1169149") and yet this computer cannot see any other computers (Windows or Linux) in the network, but the other computers can see it.

Any help would be appreciated and I am willing to provide any additional information necessary to get this working.

---

### Post by chessnerd on 2009-11-24
Further digging revealed that I missed one of the firewall settings (didn't open the tcp 445 port) and accidentally had a line commented out in smb.conf.

After a reboot Samba was working.

---

