---
title: "Wired networking and dual boot"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by bearozo on 2009-06-15
I use Ubuntu on my machines but my son has one with dual boot, Windows XP and Ubuntu.
If one reboots to ubuntu it can not get a connection unless one reboot several times etc.
the connection is an ipCop router/firewall using DHCP.

Is there a way to fake a mac address different from the one in windows so I can give it a permanent lease in ipCop ?

---

### Post by DGortze380 on 2009-06-15
> **bearozo said:**
> I use Ubuntu on my machines but my son has one with dual boot, Windows XP and Ubuntu.
If one reboots to ubuntu it can not get a connection unless one reboot several times etc.
the connection is an ipCop router/firewall using DHCP.

Is there a way to fake a mac address different from the one in windows so I can give it a permanent lease in ipCop ?

MAC Address is specific to hardware, it is the same in Windows and Ubuntu.

---

### Post by x22 on 2009-06-15
MAC addrs, tho associated with hardware--net cards--can
be changed.  It's called "spoofing"--

[http://www.klcconsulting.net/Change_MAC_w2k.htm](http://www.klcconsulting.net/Change_MAC_w2k.htm)

that's one way.

---

### Post by bearozo on 2009-06-15
> **x22 said:**
> MAC addrs, tho associated with hardware--net cards--can
be changed. It's called "spoofing"--
 
[http://www.klcconsulting.net/Change_MAC_w2k.htm](http://www.klcconsulting.net/Change_MAC_w2k.htm)
 
that's one way.
 
Thanx :)
 
Spoofing it is called, it can be done in ipCop so I knew it is possible in Linux as well
but I do not know how.
 
I will look into what is offered in the link (tommorow when I come home from work)
but I'd rather do it in ubuntu if possible.
 
It is an onboard net "card" and they can be a little ankward.

---

### Post by Iowan on 2009-06-15
Are you doing a full power-down reboot, or just the 3-finger salute?  I've seen threads where a full reboot is necessary to reset drivers (both from Ubuntu and from Windows.)

---

### Post by bearozo on 2009-06-15
> **Iowan said:**
> Are you doing a full power-down reboot, or just the 3-finger salute? I've seen threads where a full reboot is necessary to reset drivers (both from Ubuntu and from Windows.)
 
Both, it seems I have to do it a few times before reset so a spoofing would be better IMO.
 
After some more searching I found this:[http://www.irongeek.com/i.php?page=security/changemac](http://www.irongeek.com/i.php?page=security/changemac)
so I think I will be able to sort it out :)
 
Thanx for the replies you all.

---

