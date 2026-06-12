---
title: "server backup to network file server"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by dave37 on 2009-07-16
Currently running a very successful soho Ubuntu file server (desktop 8.04 lts with samba) serving to a windows xp network on my wife's small office

 No domain, just file and folder permissions set by samba.

As her office and business are growing, we see the need for a backup to the server.  We do backup to NAS hourly and offsite using rsync nightly, but should the file server die, we need a second server to step in, hopefully automatically.  As off lease pc's are cheap and quite efficient in Linux, if anyone has a howto or directions to a howto on setting up a redundant server, please reply.

Thank you!

---

### Post by paulisdead on 2009-07-16
I think this might be kind of overkill, but you could look into a samba/heartbeat solution for automatic failover.  If you wanted to, you could add DRBD to keep things constantly in sync, instead of using rsync hourly.

Basically heartbeat will create a virtual IP, and whichever of the 2 nodes can get the most pings to locations you specify, gets control of the virtual IP.  If one listening on the virtual IP goes down, the other one takes over on the virtual IP.

DRBD is like RAID1 over the network, and can keep 2 volumes on different computers in sync.  This should at least minimize data loss, should a fail over take place, and the first server goes kaput.  If you're comfortable with hourly updates with rsync, and don't need constant synchronization, then you should be able to stick with that.

I've not tried this for samba myself, but looks like there's a lot of howtos out there for it if you just google for "heartbeat samba."  I've so far only been using this for tomcat and postgresql at work, but it's been working great.

---

