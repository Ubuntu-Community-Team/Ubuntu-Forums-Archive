---
title: "Linux shares appear under &quot;windows network&quot; - why?"
date: 2011-06-14
forum: Networking &amp; Wireless
---

### Post by pink_book7 on 2011-06-14
Hi

I have three machines running Ubuntu and two running Windows.  I have shares set up on all the machines and can happily access them all from each machine.  However, the one of the Ubuntu machines behaves slightly differently to the other two.  When I browse the network on the "odd" machine I have to open the windows network, then workgroup and then I can see all the machines on the network.  However, when I use the other two Ubuntu machines the linux shares show immediately under network, I don't have to go off and explore the windows network.

Does anyone know how to fix the "odd" machine?

Thanks

---

### Post by Joe of loath on 2011-06-14
The 'Windows share' will be samba, which is a windows protocol. Hence, it shows up under 'Windows network'.

---

### Post by doas777 on 2011-06-14
compare the file /etc/samba/smb.conf on the odd box with one of the normal (ubuntu) ones, and see what is different. feel free to post them both if you like.
it is likely that the workgroup parameter is different.

---

### Post by dandnsmith on 2011-06-14
My Ubuntu PC behaves as your 'odd' machine, but the samba config uses the same workgroup name as the Windows PCs.

---

