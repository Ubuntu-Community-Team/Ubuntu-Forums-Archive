---
title: "Wireless 'fun' with the Netgear WG311v3"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by RedAphex on 2009-12-27
So I've been doing IT related work for years but I'm relatively new to the Linux environments. I really got into Linux for the amazing programming functionality & excellent security.

That said, my internship into Linux has felt more like a hazing than I would prefer. I've been fighting with getting 2 different wireless cards working for far too long and any advice would be greatly appreciated.

Originally I had a Linksys WMP54GS (which uses the Broadcom firmware) and after much research & experimentation I finally decided to simply set the project aside and use the wired connection. **Recently I picked up a Netgear WG311v3 and figured I would give the wireless setup another shot.**

**Here's some of what I've tried with the Netgear**

[LIST]
[*]Disabled my onboard LAN in BIOS.
[*]Downloaded / installed Ndiswrapper 1.55
[*]Downloaded Netgear's WinXP WG311v3 drivers.Loaded drivers into Ndis using -i switch.
[*]Confirmed PCI ID is correct for my device.
[*]Ndis: **Driver loaded, hardware present**
[*]Ran the config switches for Ndis for aliases & modprobe.
[*]Tracked down the ndiswrapper alias file and renamed it ndiswrapper.conf (because I'm anal.)
[*]Performed *sudo depmod -a* and *sudo modprobe ndiswrapper*
[/LIST]
 After running *iwconfig* I still see **no** interface listed.  The only interface in *ifconfig* is the loopback.  Obviously it didn't load correctly so I check my system log and see the error:

**Kernel is 64-bit & driver is 32-bit.  Bad Mojo.**

Being a Linux newbie this is a little confusing to me. My system is 32-bit so why would my kernel be 64? Are all Linux kernels 64-bit or is there one that I could replace it with without having to figure out how to create my own? I've also read that others with this problem have tried using 64-bit Vista drivers with no success so I figure the other option at this point is to make the kernel itself compatible instead. I loath having to do something this drastic however.

I've been following _[this thread]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/success-netgear-wg311v3-400257/?highlight=Success%3A+Netgear+WG311v3")_

According to this link: _[it should work with Debian at least.]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WG311v3")_

So perhaps I should, once again, try to load the appropriate Debian packages or just switch to it. Does anyone have any suggestions on what would work well for me?

_[My system log]("http://redaphex.10fast.net/syslog.doc")_

---

