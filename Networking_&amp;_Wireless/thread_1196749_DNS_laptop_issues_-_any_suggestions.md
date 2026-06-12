---
title: "DNS laptop issues - any suggestions?"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by dmravaet on 2009-06-25
So, Firefox and Opera will connect to IP addresses but will NOT resolve domain names. W3m, ping and Update Manager, OTOH, resolve domain names just fine.

I've been using OpenDNS for some time now (set up in resolv.conf and on the wireless router, as well). At one point I tried going back to using the defaults on both simultaneously. Then I tried each without the other, also to no avail.

One more thing which may or may not be an irrelevant coincidence: this all happened at about the same time as when I changed the router from WPA to WEP (this was done to accommodate an older piece of hardware which now needs to connect wirelessly, so I can't just go back to WPA to try to solve this, much as I'd like).

Anyone have any suggestions on what I might try next?

---

### Post by snek on 2009-06-25
I had a similar problem here at work.. Somehow commenting out a few ip's in resolv.conf using # was something Ubuntu didn't like.. Did you maybe do the same?

---

### Post by dmravaet on 2009-06-26
No, sadly, nothing's commented out in resolv.conf

resolv.conf:
```
search hsd1.mn.comcast.net.
nameserver 10.0.0.1
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 68.87.77.134
nameserver 68.87.72.134
nameserver 208.67.222.222
nameserver 208.67.220.220
```

One thing I tried was messing with dhclient.conf:
```
send host-name "<hostname>";
prepend domain-name-servers 208.67.222.222,208.67.220.220;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, host-name,
	netbios-name-servers, netbios-scope;
timeout 30;
```

I've omitted any commented lines for dhclient.conf there. 

Also, I've tried using it with and without the second line (prepend domain-name-servers...) and with and without "domain-name-servers" on the fourth line (double-checked all 4 combinations of the two, actually)...

---

### Post by dmravaet on 2009-06-29
Still having issues with this - any ideas out there, anyone?

---

