---
title: "Spurious iptables entries - source?"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by mjmaisey on 2009-05-09
I'm running a fairly clean Jackalope Netbook Remix with standard updates + one or two extra packages (list of installed packages attached).

This morning I suddenly had problems accessing the network - nothing working, could not even ping hosts on the LAN despite DHCP coming back OK. Traced it to iptables entries:

---
martin@martin-laptop:~$ sudo iptables -L
[sudo] password for martin: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
LOG        all  --  127.0.0.0/8          anywhere            LOG level warning 
DROP       all  --  127.0.0.0/8          anywhere            
DROP       all  --  anywhere             224.0.0.1           
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
DROP       all  --  anywhere             224.0.0.1           
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  anywhere             224.0.0.1           
LOG        all  --  anywhere             anywhere            LOG level warning 
DROP       all  --  anywhere             anywhere            
---

I can flush the chains and change the default policy, which restores connectivity temporarily. But the odd thing is that I have absolutely no idea what's setting them and - annoyingly - restoring them on boot. I could be going mad and have forgotten something major, but the only thing I can remember doing recently is to install Hatari and Aranym, neither of which should be fiddling with iptables presumably. To be on the safe side, I have completely uninstalled these but whatever's setting them is still persisting.

Does anybody have any ideas where I might look to see what's causing this?

Cheers,

Martin

---

### Post by mjmaisey on 2009-05-09
Hmm, trawling through logs and it seems the aranym package has dependencies on ipmasq and bridge-utils, which could explain some of the changes...

---

### Post by mjmaisey on 2009-05-09
Yup, one of those was the culprit - removed and it's now fine.

---

