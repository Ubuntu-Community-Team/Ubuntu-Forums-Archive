---
title: "VPN weird issue - ping returns 2 hosts!"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by aaronp on 2010-10-25
Hi guys,
I've set up vpnc on my Ubuntu machine at home to connect to my work network and then I generally RDP into my work PC (Win XP Pro).
On most occasions this works fine but every now and then lately when I try to RDP it goes to login but then just hangs on the 'unlocking' screen (after the username/pw prompt) for a couple of minutes, before just throwing me out of the RDP session.
I've tried it with Citrix as well, trying to Remote into the same PC and get the same result.

I decided to do a bit more investigation this time and ping my machine (while connected to VPN). The result I got back was strange. When I ping my own machine (host = xyz022313) it returns alternating ping responses from different host names but the same ip address. I'm figuring this is the reason for the problem but have no idea how to fix it or why it happens.

Any ideas?

```

PING xyz022313.xyz.priv (172.20.107.42) 56(84) bytes of data.
64 bytes from xyz01078 (172.20.107.42): icmp_req=1 ttl=122 time=60.0 ms
64 bytes from xyz022313.xyz.priv (172.20.107.42): icmp_req=2 ttl=122 time=59.9 ms
64 bytes from xyz01078 (172.20.107.42): icmp_req=3 ttl=122 time=62.4 ms
64 bytes from xyz022313.xyz.priv (172.20.107.42): icmp_req=4 ttl=122 time=59.2 ms
64 bytes from xyz01078 (172.20.107.42): icmp_req=5 ttl=122 time=59.6 ms
64 bytes from xyz022313.xyz.priv (172.20.107.42): icmp_req=6 ttl=122 time=59.8 ms
64 bytes from xyz01078 (172.20.107.42): icmp_req=7 ttl=122 time=60.4 ms
64 bytes from xyz022313.xyz.priv (172.20.107.42): icmp_req=8 ttl=122 time=60.5 ms
64 bytes from xyz01078 (172.20.107.42): icmp_req=9 ttl=122 time=59.9 ms
64 bytes from xyz022313.xyz.priv (172.20.107.42): icmp_req=10 ttl=122 time=59.8 ms

```

Note, if I try 'ping xyz01078' after this it tries to ping 172.20.106.36 but comes back as destination host unreachable.

thanks
Aaron

---

### Post by Nostalos on 2010-10-25
While I can't even begin to guess at the RDP issue. If it's Windows 7, I've had lots of issues with rdesktop to Win7. There is probably nothing wrong with your system as far as returning the 2 differing hostnames.  It is returning from the same IP in the proper sequence so your connection is fine,  your DNS server/VPN Server just appears to have a conflict on reverse resolving the IP address to a name.

You most likely would want to bring it up to the system administrator owning the VPN solution.  Most likely a load balanced DNS servers where one server does not contain the proper information.

---

