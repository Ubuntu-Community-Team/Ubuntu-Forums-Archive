---
title: "Slow/no connection"
date: 2013-03-23
forum: Networking &amp; Wireless
---

### Post by El Tito on 2013-03-23
Hi. I was running kubuntu 12.10, connected via wlan0, everything running smoothly (firefox and ktorrent).
I decided to download a couple of magnets and afterwards my torrents slowed down and stopped.
When I tried to connect to internet, simply I could not reach my router; 
ping 8.8.8.8 -> destination host unreachable

I tried to restart the service and I got a wonderful: kdeinit4 segmentation fault (I cannot remember anymore data from this crash), and executable:networkmanagement_configshell PID3088 signal:segmentation fault (11).

I rebooted and everything went back to normal until I started again the ktorrent, and the same story repeated. To discard
 variables, I installed qbittorrent but the same outcome. Network manager shows that I'm connected. If I disable/enable wireless, no networks are displayed in the list. Now my laptop is requesting the router key repeatedly (it does not matter if you introduce the key, the message keeps spawning). 

In a desperate try to get things back to normal, I updated to raring. That neither solved the problem. Any ideas?

Thanks!

---

### Post by ManamiVixen on 2013-03-23
[http://en.wikipedia.org/wiki/Copyright_Alert_System](http://en.wikipedia.org/wiki/Copyright_Alert_System)

You may have triggered it with torrents.

---

### Post by SeijiSensei on 2013-03-23
If you're using a residential wireless router, you may be running into the problem of too many simultaneous connections.  By its very nature bittorrent creates a large number of TCP connections to all the peers.  Most wireless routers have relatively small memories that fill up fast if your trying to connect with dozens or hundreds of peers.  This is an entirely separate issue from bandwidth limits.

Try setting the maximum connection limit in your torrent client to a low number like 25 and see if that solves the problem.  If so, you can try increasing the ceiling until the router becomes non-responsive.

And, no, I don't think the new copyright systems are to blame here.  For one thing, you get six "strikes" before you can be disconnected, and the ISP is supposed to notify you after strike one.

---

### Post by El Tito on 2013-03-24
Thank you @ManamiVixen and @SeijiSensei for your quick reply and help.
The mafia has not reached my country, yet ... but there is a draft bill waiting to be approved.
For now, I suppose my ISP is innocent. 
I tried to reduce the number of connections, but no matter what, after a while my torrent client freezes,
or stalls. If I do not start ktorrent or qbittorrent, everything runs smoothly. 
I do not believe reinstalling the torrent clients will solve the problem, and I would prefer not to reinstall linux.
I have java 8 installed, but ktorrent is written in Qt isn't it?, so this would not have influence in theory. Also, is it possible
that a torrent has malicious code waiting to release the payload (in this case, impeding me to connect to internet)?

---

### Post by El Tito on 2013-03-24
Previously I didn't have any problems with the default config of ktorrent. In theory I have an agreement with my ISP of 100MB (download) and 10MB (upload).
Global max connections 500
Max connections per torrent 100
Max number upload slots per torrent 4
DHT enabled and encryption(preferred).
Global upload rate limits 50KB (default)
I have not mentioned that in spite of shutting down the torrent client, I cannot connect to any page.

Thanks again.

---

### Post by SeijiSensei on 2013-03-26
> **SeijiSensei said:**
> Try setting the maximum connection limit in your torrent client to a low number like 25 and see if that solves the problem.  If so, you can try increasing the ceiling until the router becomes non-responsive.

[QUOTE=El Tito]Global max connections 500[/QUOTE]

500 >> 25

---

### Post by El Tito on 2013-03-26
Yes, sorry, it is just the default values that used to work without further modification. Now it is running with 400 max connections smoothly (same router, same ISP, same agreement, different location). The last couple of days I lowered the values, and yes, that let me surf. What I don't understand is why now everything seems fine. At least an ubuntu reinstall is 
avoided by now. 

Thank you very much @SeijiSensei.

---

### Post by SeijiSensei on 2013-03-26
Perhaps you weren't able to establish all those connections in the original location for bandwidth reasons.  As I said, this is usually a problem with too many TCP connections needing to be managed by the router.  Routers use a technology called "network address translation," sometimes referred to as "masquerading," where the router  replaces the source IP address in each packet with its own external address.  In order to know what to do with return traffic intended for the machine behind the router, it has to build a table of mappings.  Residential routers generally have smallish memories that can be overwhelmed when these tables have to manage hundreds of simultaneous connections.

---

