---
title: "Is automount causing shutdown problem?"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by JKyleOKC on 2011-05-04
I've had an annoying situation with Lucid LTS 10.04.2 for quite some time. When I shutdown or restart, the "Deconfiguring networking" message appears; there's then a long delay before another message that /net is busy and cannot be unmounted, followed by a forced change to read-only after which the shutdown or restart takes place.

This machine is configured with two network cards in addition to the integrated network adapter on the motherboard (which is disabled in BIOS) since it serves as my primary router for my LAN. I've removed NetworkManager and have configured /etc/network/interfaces to provide control of the interfaces.

At boot time, it comes up with no ability to access the internet; when I issue the "route" command it hangs without showing any default gateway. If I then manually do "sudo route add default gw 66.143.xxx.xxx" everything works, but the "route" command then shows multiple default gateways. This may all be related to the long delay when attempting to shut down networking.

What other information would be relevant to finding answers to this annoyance? All ideas are welcome!

---

### Post by JKyleOKC on 2011-05-11
In digging into my shutdown problem I've found a pattern of automount activity. Here's a portion of today's syslog: ```
May 11 12:11:25 mehitabel automount[1181]: attempting to mount entry /net/xubuntu
May 11 12:11:25 mehitabel automount[1181]: mount(nfs): mounted xubuntu:/ on /tmp/autobLC7mP
May 11 12:11:25 mehitabel automount[1181]: mounted /net/xubuntu
May 11 12:12:18 mehitabel automount[1181]: 2 remaining in /net
May 11 12:13:33 mehitabel automount[1181]: 2 remaining in /net
May 11 12:14:48 mehitabel automount[1181]: 2 remaining in /net
May 11 12:16:03 mehitabel automount[1181]: 2 remaining in /net
May 11 12:17:01 mehitabel CRON[23700]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 11 12:17:18 mehitabel automount[1181]: expiring path /net/xubuntu
May 11 12:17:18 mehitabel automount[1181]: unmounting dir = /net/xubuntu
May 11 12:17:18 mehitabel automount[1181]: expired /net/xubuntu
May 11 12:21:22 mehitabel automount[1181]: attempting to mount entry /net/xubuntu
May 11 12:21:22 mehitabel automount[1181]: mount(nfs): mounted xubuntu:/ on /tmp/autocnwdZh
May 11 12:21:22 mehitabel automount[1181]: mounted /net/xubuntu
May 11 12:22:18 mehitabel automount[1181]: 2 remaining in /net
May 11 12:23:33 mehitabel automount[1181]: 2 remaining in /net
May 11 12:24:48 mehitabel automount[1181]: 2 remaining in /net
May 11 12:26:03 mehitabel automount[1181]: 2 remaining in /net
May 11 12:27:18 mehitabel automount[1181]: expiring path /net/xubuntu
May 11 12:27:18 mehitabel automount[1181]: unmounting dir = /net/xubuntu
May 11 12:27:19 mehitabel automount[1181]: expired /net/xubuntu

```During this period I was not doing anything on the computer; it was sitting on a remote-desktop link to a vbox VM on another machine and displaying an email message.

Questions:
1. What is triggering the repeated mounting, at irregular intervals?

2. What do the "2 remaining" report lines mean?

The path being mounted is in fact a second machine (the one that's hosting the remote-desktop link), and my automount configurations are essentially "out of the box" as installed via Synaptic...

---

