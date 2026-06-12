---
title: "DNS resolve intermittent failure and slow the rest of the time"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by lildigiman on 2013-06-07
Suddenly, yesterday morning when I first went to use my computer, I noticed incredibly slow and unreliable internet (Surfing the web and anything else in the terminal as well). 

Things I've tried:
[LIST]
[*]Restart computer (of course, this also happened again after re-configuring settings in steps below)
[*]Tested my personal network and DHCP, DNS, etc. thoroughly with other computers and noticed no issue with anything; internet was fine on them
[*]Confirmed that this computer's internet works as it should on another operating system
[*]Re-installed my network card's module
[*]Changed my DNS to 8.8.8.8 even though my DNS was working fine on other machines
[*]dpkg-reconfigure network-manager[/CODE] (in order to have my /etc/resolv.conf reset)
[*]disable dnsmasq
[*]change /etc/nsswitch.conf host line from ```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
``` to ```
hosts:          files dns
``` as described by [this bug]("http://bugs.launchpad.net/ubuntu/+source/nss-mdns/+bug/94940").
[*]^The last two bullets simultaneously
[*]re-installed network-manager and it's gnome counterpart completely
[/LIST]

By now, it's clear I've realized that this problem is DNS related on my local machine. To prove it, I can ping google.com and get very long pauses between each ping *if* it even manages to ping at all and not result in an unreachable host. *However*, when I ping google by its IP address, my ping results are fast and working each and every time.

I wish I could tell you what changed between the night I went to sleep and the next morning when I awoke, but I haven't found anything.

Any idea what this might be? Your constructive feedback is greatly appreciated!

Thanks in advance!

---

### Post by lildigiman on 2013-06-07
The is no easy way to say this, so I'll just say it. After spending hours on this, I gave up on everything else and simply restarted my windows DNS server, and that fixed it. It makes absolutely no sense that it affected only one machine of many on the network (albeit the only linux machine, which *should* *not* make any difference!!).

If anyone has any clue as to why my windows DNS server was acting up, causing my single linux box to fail miserably, please let me know! Thanks!

I still don't understand how when I even switched to another DNS server (8.8.8.8) I *still *had issues. It seems like that should have worked given the fact that it was my local DNS server that was failing!

---

