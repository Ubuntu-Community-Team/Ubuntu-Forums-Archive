---
title: "eth0 gone after updates"
date: 2006-05-24
forum: Networking &amp; Wireless
---

### Post by wparsons on 2006-05-24
I recently did some updates, and upgraded to "dapper".. After a reboot eth0 is totally gone.  Any suggestions on where to start, or am I looking at a reinstall?

---

### Post by Qrk on 2006-05-25
One of the updates may have renamed eth0 to eth1, but most people didn't have problems. If you've manually edited eth0, or added a line in /etc/network/interfaces that corresponds to eth0, you should try changing it to eth1.

---

### Post by msibleyj on 2006-05-25
I'm having the same problem.  So, there is no way to change eth1 back to eth0?  Or, should I just leave it like it is?

---

### Post by wparsons on 2006-05-25
[QUOTE=Qrk]One of the updates may have renamed eth0 to eth1, but most people didn't have problems. If you've manually edited eth0, or added a line in /etc/network/interfaces that corresponds to eth0, you should try changing it to eth1.[/QUOTE]

I don't think thats the problem.. The result from 'ifconfig -a' doesn't list any ethX at all.  The network card is still listed by lspci, and shows up in the device manager though, its light is also on, as well as the light on the router.

---

### Post by wparsons on 2006-05-25
I've done more digging, and looked at /etc/network/interfaces, and also in 'man interfaces'.. I tried 'ifup -a' and it gives me an error saying that eth0 is an unfound device..

---

### Post by timothyp on 2008-01-10
Same problem here
even adding new hardware doesn't help.

It's listed and dmesg even says it's there

---

### Post by timothyp on 2008-01-10
I inserted a live cd and checked the modules that were loaded

The one that got my attention was
cx24123 which is the driver for my US Robotics PCI card.
(Might be different one for you, check with lsmod)

After booting back into my normal install I ran
modprobe cx24123 and my interface magically returned :)

But then I noticed some voodoo magic.
You see, assuming it was indeed a module problem, that
would mean I'd have to load it again after rebooting.

And then I realized, my IP settings were correct even before executing
modprobe the first time... so booting my live cd fixed it.

Perhaps the software caused it to lock up or something? But how?

(I rebooted like a thousand times before)

---

