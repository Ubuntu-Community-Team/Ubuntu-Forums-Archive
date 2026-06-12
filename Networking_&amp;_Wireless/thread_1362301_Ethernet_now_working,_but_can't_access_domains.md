---
title: "Ethernet now working, but can't access domains ?"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by oygle on 2009-12-23
Hi,

I had problems with getting my ethernet going, see [here]("http://ubuntuforums.org/showthread.php?t=1361558") ; it is working okay now, after modifying the IPv4 settings.

I can ping to each computer, and can ping to an IP address on the internet, but I cannot reach any domains.

This would suggest I need to also specify the DNS side of things on the 'client' computer, however I would have thought that, as the client is using the gateway computer to access the internet, then all the DNS side of things is handled by the gateway computer.

Here is the setup ..

Internet <==> Gateway computer <==> hub/switch <==> Client computer

There has been a fresh install of Karmic on the client computer.

Everything works fine on the gateway computer, all but domains work fine on the client.

(Firewall is not an issue, as it is setup okay).

Do I need to add the DNS side of things on the client computer, in the IPv4 tab for 'auto eth0' ?

If I do, can someone explain why please, as I really would have thought that, the gateway computer does all that side of things.

Thanks,

Oygle

---

### Post by oygle on 2009-12-23
Oh well, I don't know why, but adding in the DNS side of things, in the IPv4 tab, has solved this, plus a NM restart.  :D

Can now access domains okay.

Still, it doesn't 'explain' why the gateway computer didn't do that 'work', that is, handle the DNS side of things for the client computer.

Oygle

---

### Post by Iowan on 2009-12-23
The client needs to know where to go for DNS information. Even if the gateway provides the information, the client still needs to know to go there.  It's possible that you could have a different machine providing DNS, you'd need to tell the client to go there instead.

Frequently, DHCP server provides the address of the nameserver(s).

---

### Post by oygle on 2009-12-23
Thanks Iowan, that explains it for me.  :)

---

