---
title: "Can't RDC to Windows 7 VM hosted on another Ubuntu Workstation"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by PirateFanAZ on 2010-02-06
I have two Ubuntu 9.10 machines running on my home network.  On one of the machines I have a Windows 7 RC1 desktop running on a VMWare VM under VMWare Player 3.0.  The VM was created with VMWare Player 3.0 as well.

I want to be able to remote desktop, using TSClient, from the other Ubuntu 9.10 workstation to the Windows 7 VM.  I can ping the first workstation from the second workstation (by IP address) but I can't ping the VMWare Windows 7 desktop (by IP address) that's hosted on the first workstation.

I can ping the VMWare Windows 7 desktop from the workstation that's hosting it (by IP address) and I can get a TSClient remote desktop connection running from the hosting workstation.

Any suggestions would be most appreciated.  If I missed another support thread, howto or the like please just point me to it, I'm more than willing to do the digging myself.

Thanks.

---

### Post by PirateFanAZ on 2010-02-08
I found the issue.  After playing around I noticed that the network of the virtual machine was set up to use NAT to share the host's IP address.  After I reconfigured the VM to use a Bridged configuration for the network the Windows 7 VM received its own IP address on my home network and became "visible" to the second workstation.

I can now use TSClient to connect to the VM from the second workstation.

---

