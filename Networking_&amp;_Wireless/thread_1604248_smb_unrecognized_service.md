---
title: "smb unrecognized service"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by savaan on 2010-10-23
I'm trying to set up basic file sharing between two computers in my home. Both are using Ubuntu 10.04. I've installed samba and swat on both. From my computer I can see my wifes and mine on the network, but from hers ... nothing. 
I tried to use the command 
sudo /etc/init.d/samba start but this just brought back "command not found"

What am I missing?

---

### Post by Scunizi on 2010-10-23
Since a lot of services have been moved away from init service, the correct way to start stop restart samba is now "sudo service smbd start/stop/restart".. also if you have netbois running on the network there's sudo service nmbd start/stop/restart .. have fun!

---

### Post by kevinatkins on 2010-10-23
It's possible your wife's machine doesn't have the Samba service installed. Check that first....

---

