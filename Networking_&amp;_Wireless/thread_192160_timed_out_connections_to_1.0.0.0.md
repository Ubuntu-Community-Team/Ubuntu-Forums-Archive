---
title: "timed out connections to 1.0.0.0"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by g00n on 2006-06-08
** looking to moving this to a software or config section ** 
I'm seeing this on all of my linux/unix systems.

My SunOs 5.10, Ubuntu, slack... 

I've been able to stop it from happening by removing the router DNS servers from /etc/resolv.conf leaving just the actual ISP DNS servers.

After this connections work like they're supposed to.

.. 

It's odd that all my unices have this problem but my windows boxes don't.

I've tried to "disable ipv6" on them with /etc/modprobe.d/aliases (not sure this disables ivp6 though.. and it made no difference.

i've seen these questions all over with all distros, all kinds or problems.. and they're all being mis diagnosed with.. "are you connected to the net".. if I weren't connected.. fixing my /etc/resolv.conf woudln't make the difference.. 

So it has to be a DNS resolution issue.. 

My personal configuration is .. 
Qwest DSL with the black actiontec wifi router/modem.. 
issue happens both wireless and wired.

and fixing the resolv.conf fixes it.

Any ideas?

---

