---
title: "IPv4 in IPv6 tunnel"
date: 2009-08-29
forum: Networking &amp; Wireless
---

### Post by erizzaaaaa on 2009-08-29
Hello,

I've been playing with the 2.6.28 and 2.6.29 kernels, and discovered the "ipip6" tunnel mode in the "ip" man page. If I guess correctly, this should be the IPv4-in-IPv6 tunnel, is that correct? Can anyone confirm this?

However I didn't manage to create any tunnel, e.g. using the command:

 # ip tunnel add mytun mode ipip6

as root, produces "Cannot guess tunnel mode" error message.

Is it possible at all to create this kind of tunnel? If yes, how?

Thanks,

---

