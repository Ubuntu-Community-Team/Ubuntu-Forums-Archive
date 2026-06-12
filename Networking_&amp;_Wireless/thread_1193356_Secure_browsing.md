---
title: "Secure browsing?"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by joris1977 on 2009-06-21
Since a while i am realizing that browsing and checking mail on a public hotspot is not very secure.

This blogpost pointed me in the right direction how to secure browsing:

[http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://ubuntu.wordpress.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)

That is good and works nice, but i would like something not only for firefox, but also for thunderbird and xchat

Would it be difficult to setup openvpn over ssh to secure internet access. Or it this not something openvpn can do. And how do I set it up?

:confused:

---

### Post by kevdog on 2009-06-21
OpenVPN is easy to setup, but for only a few apps or for a few open ports, tunneling through ssh would be easier.  I find the easiest solution (either tunneling ssh or running a OpenVPN server) is easiest running a compatible router capable of using the dd-wrt firmware that has an openvpn server built-in -- its compiled in the firmware.  Of course you have to configure this, however its very easy to do.

---

