---
title: "backend cannot find HDHomerun after reboot"
date: 2008-07-10
forum: Mythbuntu
---

### Post by allene222 on 2008-07-10
If I reboot, I get these errors:

HDHRChan(10137dc1/0), Error: Unable to send discovery request
                        eno: Network is unreachable (101)

Then the HDHR tuners show up as unavailable.

If I restart just the backend, all is fine.

It has been suggested that I need some delay between bringing up the network and starting mythbackend.

It was also suggested that I change the IP from DHCP to static.  That worked.  I would consider this a bug as there is nothing in my setup that I did to trigger this.  Should I report it somewhere?


Allen

Mythbuntu 8.04 running on ASUS M3A with AMD 5400+, HDHR, 2 ea air2pc, Nvidia 6200, SATA hd and dvd.

---

### Post by superm1 on 2008-07-11
Don't worry about making it static.  Just configure it to not use network manager.  Open up network-admin (no sudo).  Pick your connection and change it from roaming to just DHCP.  Reboot

---

### Post by allene222 on 2008-07-11
Thanks for the reply.  I hate to admit I never heard of roaming mode. It was no problem for me to assign an IP address in the router so it is static now and it worked.  Unless there is an advantage to DHCP, I will stick with static.

I don't know if I assigned roaming mode during setup or if Mythbuntu did it by default.  Clearly if I did it, that was a mistake.

Thanks again,

Allen

---

### Post by superm1 on 2008-07-15
> **allene222 said:**
> Thanks for the reply.  I hate to admit I never heard of roaming mode. It was no problem for me to assign an IP address in the router so it is static now and it worked.  Unless there is an advantage to DHCP, I will stick with static.

I don't know if I assigned roaming mode during setup or if Mythbuntu did it by default.  Clearly if I did it, that was a mistake.

Thanks again,

Allen
Roaming is the default (you didn't pick it), but it doesn't work for everyone.  So long as you got it solved, that's all that matters I suppose :)

---

### Post by allene222 on 2008-07-16
Someone should tell the mythbuntu folks to change the default in that distribution.  
something connected to a cable doesn't need to roam ,imho.

---

### Post by superm1 on 2008-07-16
> **allene222 said:**
> Someone should tell the mythbuntu folks to change the default in that distribution.  
something connected to a cable doesn't need to roam ,imho.
When the machine is installed, it's not aware of whether you are using an ethernet connection, wireless connection, or what you will change.  Using network manager leaves the most flexibility.

With the changes in network-manager-0.7, this should be a lot more usable and a more sensible default.

---

### Post by allene222 on 2008-07-18
Well, as long as the network comes up before Myth looks for the HDHomerun I guess it will be OK.  Otherwise, there should either be a different default for the network, or a delay before giving up on finding the HDHomerun.  Otherwise, everyone with a fast computer has to discover this over again.

Allen

---

