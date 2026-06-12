---
title: "No longer any display of &quot;SYN_RECV&quot;"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by stn21 on 2009-08-03
Hi,

for some reason netstat, /proc/net/tcp and any other utility except tcpdump do not display the socket-state "SYN_RECV" anymore.

This used to work up to Ubuntu 8.04
It does not work with Ubuntu 8.10 or 9.04

I have been researching this since 8.10 and so far the only explanation I found is that it does not work in that version because of that version. There were no changes in my network-configuration that I know of and so far I can think of no way that I could have caused this.

Any ideas on how to get netstat to display SYN_RECV again? Remember: /proc/net/tcp does not show the SYNs either. But tcpdump shows that SYN-packets arrive.

What is wrong here?

THX

---

