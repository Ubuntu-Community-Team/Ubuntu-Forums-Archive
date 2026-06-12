---
title: "Windows7X64Pro can't see Ubuntu 11.04 on the network"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by country0129 on 2011-07-19
I have samba running on Ubuntu 11.04 Laptop box. I can see and access all the Win7 x64 Professional desktop shared folders from the Ubuntu box. When try to browse the network from the Windows 7 Professional X64 Desktop file browser, the Ubuntu Laptop doesn't even show up. Both are in the same workgroup. Both have shared folders and drives. 

I can ping the Ubuntu box from the command line from Win7. I typed \\192.168.1.45 (the laptop's router address) from the RUN command. It said the laptop wouldn't allow connection. Samba shares are set for "visible" & "writeable." The username is set for my access; yet no joy. 

I ran the Win7 trouble shooter, and it said that my $Print share folder wouldn't accept connection. I deleted that share; yet still no joy.
 
Also, if this may have something to do with it, when I boot up or reboot, I get a message, "Can't update .iceauthority."
 
I've googled this to try to find a fix, and am still studying it.  Can this have any coincidental effect by being related to one another?

How do I correct the situation?




Baldheadedbecauseofpullinghairout

---

### Post by country0129 on 2011-07-19
BTW, Ubuntu 11.04 is 32 bit on a Gateway laptop.  Win7Pro on an HP desktop.  Desktop LAN to DSL router (LAN).  Laptop to router via wireless.

---

### Post by 2F4U on 2011-07-19
> **country0129 said:**
> BTW, Ubuntu 11.04 is 32 bit on a Gateway laptop.  Win7Pro on an HP desktop.  Desktop LAN to DSL router (LAN).  Laptop to router via wireless.

Do you have a firewall running on the Ubuntu PC that may prevent access?

---

### Post by country0129 on 2011-07-19
I installed UFW and GUFW. Opened GUFW and the "ENABLED" checkbox isn't. So it isn't running, is it?  Everything about the firewall is default.  I've never enabled it.

---

