---
title: "eth0 coming unconfigured"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by decoherence on 2011-04-06
Hi all,

I have an issue where eth0, which I have manually configured, unconfigures its IP address. I can be right in the middle of a telnet session to a switch or router and suddenly the thing locks up. I do an ifconfig and, sure enough, eth0 has lost its IP address. I reset it and the session sometimes comes back (along with whatever happened to be in the buffer.)

NetworkManager is disabled.

I have never seen this behavior before. Has anyone else? I'm using 10.10. My co-worker who is doing similar work at another site isn't having this problem. He's using 10.04.

thanks,

---

### Post by Iowan on 2011-04-06
It's been awhile, but I (vaguely) remember a thread where DHCP still kicked in and (re)assigned an address.

---

### Post by decoherence on 2011-04-09
Thanks, I'll keep an eye out for errant dhcp processes!

---

