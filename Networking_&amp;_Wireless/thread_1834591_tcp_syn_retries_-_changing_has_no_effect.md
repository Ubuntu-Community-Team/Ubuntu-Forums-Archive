---
title: "tcp_syn_retries - changing has no effect ??"
date: 2011-08-27
forum: Networking &amp; Wireless
---

### Post by gmallard on 2011-08-27
Changing:

net.ipv4.tcp_syn_retries

from 5 to any other value has no effect on initial TCP connect timeouts.

Furthermore, the default of '5' is documented here:

[http://manpages.ubuntu.com/manpages/natty/man7/tcp.7.html](http://manpages.ubuntu.com/manpages/natty/man7/tcp.7.html)

with a result of 180 seconds.

What I see on my system is 3 seconds only.

Even after a permanent change in sysctl.conf and a reboot, I still see 3 seconds.

This system is 11.04, natty with current maintenance.

Is there something I am missing, or is this a bug?

Misc Info: This type of change works as exactly advertised on my Redhat/Fedora systems ......

Would appreciate any help or guidance.

---

