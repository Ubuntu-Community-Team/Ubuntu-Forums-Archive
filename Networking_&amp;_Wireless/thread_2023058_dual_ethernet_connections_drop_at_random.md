---
title: "dual ethernet connections drop at random"
date: 2012-07-11
forum: Networking &amp; Wireless
---

### Post by ericpeac0ck79 on 2012-07-11
Hi, I see a few other threads related to similar problems, and I've  tried several of the solutions listed in them, to no avail...

i am running Maverick Meerkat x64 based distro
I have two realtek gigabit ethernet cards. (one onboard, one pcie x1)
both NICs are set to static ip's.
I have VMWare workstation installed, and I've set it to use the 2nd NIC, but not the first one.

my linux network connection will just drop at random.
i  have to open terminal and go "sudo ifconfig eth0 down" and "sudo ifconfig  eth1 down", then wait a minute and bring them both back up.
this can make it ok anywhere from 30 seconds to 4 hours.
some days, i only have to do that once, other days I have to do it 30 times.
I have put a new switch and new ethernet cables in place, but still have same troubles.

but the win 7 virtual machine networking stays ok - never any problems. *weird*

I'm not a *complete* linux noob [IMG]http://forums.linuxmint.com/images/smilies/icon_lol.gif[/IMG] , but I don't really know where to begin troubleshooting this.
I did read many other threads and I set "[ifupdown]
managed=true" in nm-system-settings.conf. (managed was initially set to false)
but this has not helped.

can anyone help?

(p.s.,  i have to use Meerkat b/c I've had not good results trying to  install vmware workstation on any later kernel.... and unfortunately,  there are a few windows based apps that i HAVE to run for work)

---

### Post by ericpeac0ck79 on 2012-07-16
anybody? help?.... plz?

---

