---
title: "un-used interfaces in /etc/network/interfaces"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by sunixadm on 2010-01-20
Hi all,

I keep getting these messages in /var/log/messages
eth3: Link down, cable problem?
eth4: Link down, cable problem?

I have eth0 eth1 and eth2 configured in /etc/network/interfaces, but not eth3 and eth4.  eth1, eth2, eth3 and eth4 are on the same physical PCI card.

What changes do I need to make where to stop receiving the error messages regarding eth3 and eth4 in /var/log/messages?

I am running 2.6.31-17-generic #54-Ubuntu SMP x86_64 GNU/Linux

Regards,
Joe

---

### Post by chili555 on 2010-01-20
You might try adding these lines:```
#auto eth3
iface eth3 inet dhcp

#auto eth4
iface eth4 inet dhcp
```I believe this tells the system that we are aware of eth3 and eth4, but since the 'auto' part is commented out, we do not want them to start. More importantly, in my opinion, it tells the system that we, not Network Manager, Wicd or other networking systems, will manage the interfaces.

I have not encountered this exact problem before, so I am guessing just a bit here. Please post back and let me, and the searchers, know the result.

---

### Post by Iowan on 2010-01-20
As a permutation, try: ```
auto eth3
#iface eth3 inet dhcp

auto eth4
#iface eth4 inet dhcp
```Hopefully one of the two will tell the system "Yes there are interfaces, but don't worry about them."
Another option would be to comment them out completely (all four lines).

---

### Post by sunixadm on 2010-01-21
Hi Chili555,

I implemeted your suggestion by adding:
#auto eth3
iface eth3 inet dhcp
#
#auto eth4
iface eth4 inet dhcp

To the end of /etc/network/interfaces and that did the trick.

Thanks for the quick response.
-Joe

---

