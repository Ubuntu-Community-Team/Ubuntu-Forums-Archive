---
title: "Impossible samba file sharing"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by aigore on 2009-02-04
Hi everybody,
I have installed hamachi on my linuxserver ubuntu 7.10 and i can ping and remote ssh operation from a windows machine.
So hamachi works fine.
The server is installed in my office where shares some drives via samba with no problem.
I tried everything to acces samba shares connecting with hamachi, but no way to work.
I tried
"sudo iptables -A POSTROUTING -t nat -o ham0 -j MASQUERADE",
also tried to add my ham0 device and ip to smb.conf
but nothing to do.
I don't really know if it is some iptables matter, or some smb configuration. Please, can anybody help me.....please??? 
:frown:](*,):-k:confused::confused::confused:

---

