---
title: "NetworkManager randomly not resolving dns"
date: 2005-12-26
forum: Networking &amp; Wireless
---

### Post by glacierre on 2005-12-26
(I'm not sure if this is the proper forum for this post, as it's on networking but not hardware, sorry if I misplaced it)

I'm using network-manager in my laptop, it works fine most of the time, but sometimes (I think randomly) it stucks and stops resolving dns. 

The fail doesn't seem to be paired to booting (since sometimes it doesn't work after a fresh boot) or changin networks, and cannot be solved connecting to another  wired or wireless network, just have to reboot (and cross fingers)

I know a workaround for this, just make an 
[INDENT]echo nameserver ip_of_linked_router >> /etc/resolv.conf
(needs root privileges)
[/INDENT]and it should work on most networks, network-manager wipes resolv.conf each boot (I think), so this will get erased when you shut down.

Although I can go on with this it's a bit irritating (and certainly not user-friendly), ¿is there a smart solution?

---

