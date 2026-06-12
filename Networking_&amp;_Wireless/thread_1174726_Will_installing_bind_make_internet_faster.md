---
title: "Will installing bind make internet faster???"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by Barriehie on 2009-05-31
Title says it all.  Excluding updates wouldn't having the DNS local speed up my browsing?

Thanks,
Barrie

---

### Post by steeleyuk on 2009-05-31
It would speed up the initial DNS lookup but after that you wouldn't notice any difference.

Much better off using OpenDNS for home usage...

---

### Post by spd106 on 2009-05-31
It'll make DNS lookups quicker, but it won't improve download speeds and management overhead would be more trouble than it's worth, unless you have a medium to large network.

I think you would see more gains by just switching your DNS to a different provider such as opendns.com or installing a web proxy such as squid-proxy.

---

### Post by whoop on 2009-05-31
It should make it a little faster (technically speaking), however if you are experiencing (too) slow internet speeds, this is not the solution (unless there is something wrong with the dns server(s) you are using).

It also varies per system/ISP etc. As a test I ping-ed google and sniffed the traffic:
Arrival time at dns server:
16:09:42.628632000
Arrival time at google server:
16:09:42.641536000

So me having my own dns server (on the same machine) would give me a 0.12904000 second speed increase. Not worth it in my case, and you also use more cpu and ram and diskspace with your own dns.

Conlusion for me, it's all negligible...

---

### Post by Barriehie on 2009-05-31
I guess it's a patience thing... ;)  I've tried adding opendns and my system is resolutely sticking with lv.cox.net.  I even deleted it and it came back.  I just hate seeing FF doing the looking up blah blah blah thing for several seconds!

Thanks All for your replies,
Barrie

---

### Post by whoop on 2009-05-31
> **Barriehie said:**
> I guess it's a patience thing... ;)  I've tried adding opendns and my system is resolutely sticking with lv.cox.net.  I even deleted it and it came back.  I just hate seeing FF doing the looking up blah blah blah thing for several seconds!

Thanks All for your replies,
Barrie 
Are you using a router and dhcp? Maybe that's why your dns settings are being reset.

---

### Post by Barriehie on 2009-05-31
> **whoop said:**
> Are you using a router and dhcp? Maybe that's why your dns settings are being reset.

No router, computer to cable modem, cable modem to COX.  It does say my address is dhcp.

Barrie

---

### Post by shel-hall on 2009-05-31
If you install BIND on another machine on your network, not on your workstation, you can achieve speed gains in two ways:

1.  Long-term local caching of DNS entries, limited only by the server's uptime and the DNS entries' time-to-live.

2.  Less traffic on your 'net connection (DSL, cable, whatever).

A third possible source of speed gain is to have your DNS server become "authoritative" for domains from whom you wish no actual content, primarily advertising servers.  By redirecting all requests for, say, doubleclick.com to 127.0.0.1, you can reduce the traffic on your 'net connection.  See [http://pgl.yoyo.org/adservers/](http://pgl.yoyo.org/adservers/).

You could, of course, run BIND on your workstation, but the processing overhead, especially if you go with the third suggestion above, would probably outweigh the speed gain resulting from the decreased 'net traffic.

-Shel

---

