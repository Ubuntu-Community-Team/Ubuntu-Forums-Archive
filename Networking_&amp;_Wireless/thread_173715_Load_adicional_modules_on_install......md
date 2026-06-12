---
title: "Load adicional modules on install....."
date: 2006-05-10
forum: Networking &amp; Wireless
---

### Post by und3rtug4 on 2006-05-10
I there!

I'm using one ISA nic (3COM Etherlink III 509B) and I need to load the adicional module 3c509 on install, so that ubuntu can detect my nic!

But i just dont know how to load adicional modules on install!

Could it be: server netcfg/dhcp_disable=true sudo modprobe 3c509??

Would thank any help on the subject!

---

### Post by und3rtug4 on 2006-05-11
It has been a quite hard quest searching  for the "golden" bottleneck on this subject! With all BIOS configurations done and so, ubuntu still does not detect the 3COM Etherlink III 509B! 

If the system is installed and them modprobe the 3c509 module, and ifconfig eth0 up, the card kinda goes up (show the link signal at the router), but still no networking ("Network unreachable").

It was also posted somewhere, by someone who have the same nic, that the module is not loaded by the installer, and i cant see how to get it loaded on install!

Well, a new nic was obtained, but the quest stills on.......

...... WILL THE OLD ISA NIC WORK ON ONE OF MY UBUNTU MACHINES???

;)

---

