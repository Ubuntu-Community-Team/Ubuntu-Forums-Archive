---
title: "firewire tuner not available  on slave backend"
date: 2008-11-04
forum: Mythbuntu
---

### Post by 4dognight on 2008-11-04
I have a slave backend with an attached cable stb via firewire. Everything works fine except for one annoying thing. If I restart my backend, the tuner on the slave status is always set to unavailable. The only way to get it back to available is to reboot the whole server, not just the mythbackend on the slave.Correct me if I am wrong, but I would expect the slave to reconnect to the master BE , and the slaves tuners then should become available. Is this just a quirk due to it being a firewire tuner?

---

### Post by newlinux on 2008-11-05
Sometimes after restarting a slave backend I've had to restart the master to see them all... Do your slave backend logs have any errors in them after restarts? In your master backend log does it show that it has added the slave (trying to determine if the master just doesn't see the slave, or it sees it but thinks the tuner is unavailable).

---

