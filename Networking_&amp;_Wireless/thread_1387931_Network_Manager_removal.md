---
title: "Network Manager removal?"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by sandfly357 on 2010-01-22
Hi all,
I'm thinking about removing Network Manager, as it's doing nothing but causing me pain, and simply configuring my single network connection by entering data in config files (just like the old days!)

Problem I have is this: I have two separate routers, each connecting to a different phone line. I have a number of systems, some configured to use router A, some to use router B.
Router A only has wired connections, no wireless. Router B has both. The systems are a mix of OS's - Windows XP, Vista, Kubuntu Karmic and Suse 10. Router B is a DHCP server, Router A is all static addresses.

On my Kubuntu Karmic system (a desktop, no wireless), Network Manager insists on configuring the sole eth0 interface as "Auto" - which points to Router B as the default route and picks up an assigned address from the DHCP server. However, I only want it to use Router A with a static IP address. I have set this up in Network Manager - it is the only configuration profile visible to NM.

So why does NM not use it? Where is the "Auto" profile being read from, and why does this take priority over the NM profile I expect to be used?

And to make life more complex, if I change the interface on the fly, by selecting the icon and the profile I want, the whole KDE windowing system locks up apart from the console window, and I have to reboot to fix it. This cannot be right? If I try this on my ubuntu laptop (also Karmic) all works well, and I can switch from Router A to Router B without crashing the whole thing.

Has anyone done a simple guide to how NM selects and configures interfaces? Is is a "must-use" app, or can I replace it with something better? Or just get rid of it and edit the network config files manually (and if so, where are they?). I only have one NIC, and it's not going to need changing once it's configured, so why do I need an app to manage it anyway?
Something is far awry here, and I cannot fathom out what, so any pointers would be really helpful, thanks.

---

### Post by chili555 on 2010-01-22
> Or just get rid of it and edit the network config files manuallyCertainly. In a desktop environment, where the machine is not going to be hauled down to the coffee shop, in my opinion, NM is worse than useless.> if so, where are they?/etc/network/interfaces

Here is a sample interfaces file for a static address:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.117
netmask 255.255.255.0
gateway 192.168.1.254
```More information can be found here:```
man interfaces
```Post back if you need additional guidance.

---

### Post by sandfly357 on 2010-01-23
Thanks chili555, I took the plunge and disabled NM - all now appears to be working OK, so shan't be using that again! Still not able to work out why NM was behaving in the way it was, but I'm not going to worry too much about it now.... thanks for the advice.

---

### Post by dmizer on 2010-01-23
Rather than configuring by hand in the config file, you could install gnome-network-admin, the old network tool that appeared in system > admin > network.

---

