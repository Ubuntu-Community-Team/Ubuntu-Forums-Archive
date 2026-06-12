---
title: "NFS share stops randomly"
date: 2012-09-15
forum: Networking &amp; Wireless
---

### Post by ussndmac on 2012-09-15
I have a PC runing UbuntuStudio 12.04. (call it UBS)

I have nfs client setup. Worked fine with an nfs share previously setup on another machine.

I setup a new PC with Ubuntu 12.04-1 and nfs server (call it UBServ). On this machine I setup a share.

Switched UBS to point to UBServ for the share.

This happens to be a disk of music.

Now when playing music on UBS, it randonly stops in the middle of a song for some period of time, then starts to play again.

I'm not sure where to begin to troubleshoot this, any pointers appreciated.

Thanks,
Mac

---

### Post by luvshines on 2012-09-18
The places to look for might be the NFS server logs to check if server was available at that time
Also the network traces may help you analyse what is causing the hangs

---

