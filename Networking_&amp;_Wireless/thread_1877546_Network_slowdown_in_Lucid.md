---
title: "Network slowdown in Lucid"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by syrag on 2011-11-08
For the last couple of weeks my network has been extremely slow in Lucid, especially DNS lookups. Karmic does not have this problem on the same hardware.

I've changed the network driver back to r8168 from r8169. I've searched the forums and done everything suggested, e.g. disabled ipv6, edited nsswitch.conf, and I've installed bind9 to run as a caching dns server (Primary nameserver 127.0.0.1). Nothing helps. This occurs also in Mint 11.

Using wireshark I see a lot of DUP ACKS. This doesn't seem to be as bad with r8168 driver, but I haven't quantified the difference. 

Oh, and Karmic works fine with the r8169 driver. I was beginning to suspect my router, but since Karmic works fine it has to be something else.

Any help is appreciated.

Editing to add: This is a wired connection.


Editing to add info:
from syslog:```

named[1199]: success resolving . . . after reducing the advertised EDNS UDP packet size to 512 octets

named[1199]: success resolving . . . after disabling EDNS

```

---

### Post by syrag on 2011-11-16
Bump.

Does anyone have any idea what's going on here. Lucid is slow (but not always, just 99 percent of the time) and Karmic is always fast, 100 percent of the time. Same hardware.

Any idea on resources other than these forums to look?

Any ideas on other distributions other than Ubuntu or Mint, which is also broken? Since Karmic is no longer supported I'm forced to switch distros if I can't get this fixed.

---

### Post by JKyleOKC on 2012-01-12
I'm also on Lucid and am having a possibly related problem; syslog is showing multiple timeouts when attempting to do DNS lookups, finally ending with success after disabling EDNS.

I did a google search and find dozens of postings involving such situations, covering a wide range of distributions. It's not just limited to Debian and its offspring, but I didn't find anything that would shed light on exactly what's causing the problem, or for that matter what "EDNS" is. My best guess, based on my syslog reports, is that it has something to do with IPv6 lookups.

The strange thing in my case is that after a timeout and "cannot contact the server" message, immediately re-trying the same URL usually gets through with no problem. That makes me suspect that the actual cause may be at my ISP's DNS server rather than in my own system.

Hopefully somebody will chime in with some solid fact, or at least some hints on how to troubleshoot this problem...

---

### Post by syrag on 2012-01-12
My problem turned out to be my router. My apologies to Ubuntu for blaming the distribution. (That still doesn't explain why Karmic worked flawlessly.)
I unplugged my router for about a minute, plugged it back in and it has worked since.

---

