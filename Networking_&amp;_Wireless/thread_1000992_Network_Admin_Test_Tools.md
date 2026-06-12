---
title: "Network Admin Test Tools?"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by EvilMarshmallow on 2008-12-03
I was wondering: what sorts of open-source tools are best for network testing?  Specifically, I'd like to check the speed and load on various segments of my network.  I'd like to locate bottlenecks and see if I can improve network performance.  Ideally I'd like something web-based, maybe with a database and reporting capability?

Occasionally I run across proprietary tools but I don't have that much of a budget to spend on it.  I don't need all the bells and whistles, just some basic tools.  Any suggestions?

---

### Post by jonobr on 2008-12-03
Hello


For speed testing you could use Iperf, although it fails your GUI requirements :D
It will allow you test UDP and TCP uplink and downlink using different packet sizes.
It can test latency, throughput,jitter and banwidth and will give you a good indication of link intergrity.

It a pain to get started but once running is a good tool.
Its not in ubuntu by default, so you will have to search for it. 

Once you get it set up once you could script and automated it so that you can manually run the script or automate it via a cron job.

On the Gui front, I would recommend for what you are looking for , you should investigate using SNMP for reporting server availbity, usage, packet counting, in ,out, jabbers, runts and so on.

Every network box will have a snmp agent on it allowing you to query statistics.
There are lots of tools out there for getting info via CLI or Gui.
The most favoured is a package called MRTG and is used by people wanting exactly what your asking for.

If people require a network managmanet station which allows for more GUI'ness and ability to monitor alarms , traps and other things such as graphs over time, I would recommend you look at OPmanager from adventnet,
This is a simple SNMP NMS and for under 20 nodes its free.
[http://manageengine.adventnet.com/products/opmanager/index.html](http://manageengine.adventnet.com/products/opmanager/index.html)

If your network is standard boxes , cisco. juniper and other servers, there are default MIBS , however, for some devices you may need to contact the vendor and ask for their specific mibs to query certain objects.

---

