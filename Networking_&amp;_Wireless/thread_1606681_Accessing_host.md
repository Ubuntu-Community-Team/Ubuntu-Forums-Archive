---
title: "Accessing host"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by zlot on 2010-10-26
Hi. I'm relatively new to Ubuntu - been using it for maybe a year. I've been learning a lot, but have a long way to go. While I'm typing, permit me to ask 2 questions:
I once had a Windows drive from my host machine mounted in an Ubuntu VM, but now it's gone. I remember writing an addition to fstab, and doing something else to see the available partitions/drives, but have no idea what I did. Any help along those lines would be appreciated.
BUT....!
....before we can go there, I have to be able to ACCESS the host in order to do this. I can SEE it, but I can't log onto it!!! This is driving me nuts. It's a Windows 7 host. Other VMs can access it properly...and IT can access Ubuntu. All firewalls are down. Everything else seems to be working fine. I can access other windows VMs in Ubuntu, although none of them are Windows 7 - XP, Server 2008. I suppose I should check and see if I can log onto a 7 VM - I have one. I'll do it later. But for now, if you got any ideas, I'd be delighted to entertain them! BTW, when I try logging on it just fails, sits there, and looks at me! Ya gotta love this linux! Before you give me a simplistic answer, please realize I at least sort of know my ### from a hole in the ground; I am successfully logging on to other machines, and logging on to THIS machine from the host!
Thanks in advance!
~Z~

---

### Post by kreggz on 2010-10-26
Maybe the VM network card is in NAT? You will need bridged to connect to it.

---

