---
title: "smbfs network share boot problem"
date: 2005-03-02
forum: Networking &amp; Wireless
---

### Post by buzst on 2005-03-02
I have sucessfully set-up a 8 user samba network that includes win xp desktops, ubuntu desktops, and 3 wireless ubuntu laptops. The desktops all work fine, however a "cannot find network" error is generated on the laptops at boot up when the boot process tries to mount the smbfs (homes) shares. If I do a "mount -a" in a terminal after boot everything mounts  fine. I'm thinking that because the laptops are wireless the boot process is not giving them enough time to find the network (the wired desktops use the same commands and work fine)). Any thoughts on how to delay the boot process when the shares are mounted to give them time to find the network? Or, am I missing something and is the problem caused by something else?

---

