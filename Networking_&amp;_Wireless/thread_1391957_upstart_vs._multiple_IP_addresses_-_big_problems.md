---
title: "upstart vs. multiple IP addresses - big problems"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2010-01-27
I have run into a problem that I've tracked down to being a conflict between the "Upstart" init system, and how it handles multiple (alias) IP addresses per physical interface.  The summary of the problem is that the interfaces are being configured in the background in parallel with the starting of daemons.  One "feature" of this (apparently intended for pluggable devices that would add or remove an interface) is that the network daemons are restarted each time an interface is added (and presumably deleted).  But this is a disaster when applied to alias IP addresses.

I first saw the effects of this when during booting Ubuntu Server, the screen showed a message about OpenSSH daemon being restarted ... several times a few seconds apart each.  At the time I didn't know what was causing that, but didn't worry because it ultimately was running when I needed it.

But now that I am deploying these servers for specific duty with many IP addresses per system (per network interface), the symptoms are becoming serious, and I need a solution.

1.  The IP addresses are coming online too slowly.  Apparently the time it takes to restart each daemon is being added to each address being configured.

2.  It appears to be disrupting some daemons sometimes.  Occaisionally, some daemon just ends up being hung somewhere, or dies.  Too many restarts.

3.  Sometimes few or even no alias addresses get configured.  This might be due to a daemon getting hung, and the whole sequence just not finishing.

4.  The "nsd" name server as packaged by Ubuntu doesn't deal well with this at all.  It needs all its IP addresses to be up when it starts, or else it won't start.  The Ubuntu package of it doesn't including any if-up script at all, although I'm not sure that would do any good.

What I need is a way to configure all these alias IP addresses so they are all configured immediately when the point in time is reached to bring up network interfaces for the first time.  These are all static, and all are aliases on ethernet NIC cards plugged into PCIe cards, or integrated in the mainboard.  None of them are pluggables.  I did run a manual test of "ifconfig" in a loop configuring 2540 alias IP address on eth0 and it only took 2 seconds (no if-up triggers or daemon restarts here). So I know it's fast if nothing else is done between these steps.

Even for pluggable physical interfaces, I see no reason to even try to step through every alias (if it has aliases) with a daemon restart.  If an alias IP address is added on later, then I can understand doing it.  But if you have a list of 100 aliases for a physical interface, they really should all be done ... or at least attempted ... at once, and do any triggers needed after that.

So, how can I configure or modify Ubuntu Server 9.10 to do that?

I have each alias listed in the "/etc/network/interfaces" file with a separate "auto" and "iface" section for each one, with sequential sub-interface numbers appended to the interface name.  I tried it without those sections (e.g. just "address" and other items in sequence) and that prevents the system from even coming up (bootable CD to the rescue to undo that).  At least cntrl-alt-del did reboot it.

Any ideas?

I tried to attach the /etc/network/interfaces file, but I don't know if it worked because I see no confirmations about it.  if it didn't attach and you need to see it, say so, and I'll just paste it in a followup.

---

### Post by bryanl on 2010-01-27
From a conceptual viewpoint as I understand it, you will need to change to rule set used by upstart for starting the services. You need to change the service startup dependency to be something other than 'network available'. In other words, the process that sets up the IP address needs to flag upstart when the work is done and that flag needs to be used in the upstart rules as a dependency for starting the services.

I might be way off base as I have no experience with implementations, rules, and the particular procedures you use. This is just how I understand things from what I have read about upstart. I hope it will provide some ideas for an approach to your problem that might help you find a solution. Perhaps some upstart and IP address expert will show up and provide some operational details and then we'll both learn something!

---

### Post by Skaperen on 2010-01-27
My knowledge of the upstart init system is somewhere between zilch and nothing.  But I'm doing a little reading now so I can get close to making it be somewhere approaching a wee bit.  I do know IP addressing, so I'm OK there.

For the time being my workaround is adding a legacy style start-stop script /etc/init.d/inet-alias which runs /etc/network/alias-up or /etc/network/alias-down (files I also added) which just does the IP aliasing right there.  I removed the alias addresses from /etc/network/interfaces and this is working right now.  So I've got my workaround.  But I see the value of the event driven init system, and I hope there is a way to do this "the right way" within its design.  If not, I hope it can be added.

Ultimately I think it's more of a network config issue rather than an init or upstart issue.  The IP addresses should be configurable as a group or set for a single interface, rather than treating them as separate interfaces, at least for the user space perspective (it might make more sense to leave them as is inside the kernel).  For years I have wanted to rewrite "ifconfig" to do that smarter (and add CIDR style address/prefix notation, too).

So here's hoping that someone who knows the "official way" comes around.

---

