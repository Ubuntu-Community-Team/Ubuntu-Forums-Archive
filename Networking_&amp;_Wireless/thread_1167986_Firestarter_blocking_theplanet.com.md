---
title: "Firestarter blocking theplanet.com"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by GrimJack on 2009-05-23
This is weird.

Firestarter is preventing me from accessing any site hosted by theplanet.com, but I have no filter set to do that.

Any site on that host I try (Metafilter, for example) causes Firestarter to block a 44 byte event from the host on high-numbered ports, like 40627, 40648, 40660.  The service type is listed in Firestarter as unknown.  Nothing else from any host is having this issue.  When I tell Firestarter to allow connections or services from that host, the site remains inaccessible.  I have ICMP filtering to allow PINGs and PONGs.  If I turn Firestarter OFF, the problem goes away, so I believe that would point to Firestarter as the issue.  But no idea why.

I've got two other PCs on my home network, Gentoo and WinXP.  Neither machine, which both have software firewalls, has this issue.

Odder still is that it wasn't always like this.  I'd *guess* the issue started a few months back and I've not had any urgency in fixing it, but I've time this weekend to do so.  Google's not been much help when I search for things like: theplanet firestarter and various port numbers.  I also cannot find any listing which defines those ports as needed by a given service, protocol, etc.

Any thoughts?

---

### Post by cariboo on 2009-05-23
Firestarter is just a gui front end for iptables, which is the default firewall installed with Ubuntu. There is no need to run firestarter all the time, as it is only used for setting firewall rules. Another thing to keep in mind is the Firestarter is unmaintained, so you may want to change to either ufw, which is a command line interface for setting firewall rules, or gufw which is the gui front end.

---

### Post by GrimJack on 2009-05-23
Thanks for the reply.

I understand Firestarter is just a front-end GUI for iptables. The reason I run it all the time is to be alerted when there is an event, such as the one I've described. I know it's iptables that's doing the heavy lifting, but it's Firestarter that alerts me that it's happened at the moment it occurs. (And I discovered it was no longer maintained some time ago when I tried to emerge it on Gentoo.)

I installed gufw at your suggestion, but it has no provision for alerting me when an intrusion is detected. And I do run logcheck, so I will see system messages about intrusion events, but only well after they've occurred. With Firestarter, it's an instant-alert, then just right-click, Look-Up Hostname.

The issue is about more about what changed, or needs to be changed, in Firestarter to make it play nice with sites hosted on theplanet.com. Or if (maybe) an update to iptables no longer plays nice with the existing Firestarter.

---

