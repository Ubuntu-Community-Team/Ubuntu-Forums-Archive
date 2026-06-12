---
title: "Installing MRTG in Hardy Heron (8.04)"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by marcoahernandez on 2009-01-19
Hi everybody,

I'm new in Linux world, first, Windows sucks, I got tired of it.
So I'm trying Ubuntu now, I need first of all monitoring a routers network. I'm trying to use MRTG, I've been trying to install it I succeeded but when I configuring the IPs and some others parameters but it doesn't work.

Does anybody has an advise about it???

Best Regards,
[email]marcohnunez@gmail.com[/email]

---

### Post by jonobr on 2009-01-19
Hello

HAve you tried looking at the MRTG homepage and other resources on the web?

Heres a good reference

[http://oss.oetiker.ch/mrtg/doc/mrtg-reference.en.html](http://oss.oetiker.ch/mrtg/doc/mrtg-reference.en.html)

Heres info on setting up a target.
If doing SNMP to a device isnt working, you could either have the wrong community strings, or SNMP agent on the target may be disabled.

Good luck

> PER TARGET CONFIGURATION

Each monitoring target must be identified by a unique name. This name must be appended to each parameter belonging to the same target. The name will also be used for naming the generated webpages, logfiles and images for this target.
Target

With the Target keyword you tell mrtg what it should monitor. The Target keyword takes arguments in a wide range of formats:

Basic

    The most basic format is "port:community@router" This will generate a traffic graph for the interface 'port' of the host 'router' (dns name or IP address) and it will use the community 'community' (snmp password) for the snmp query.

    Example:

     Target[myrouter]: 2:public@wellfleet-fddi.domain


    If your community contains a "@" or a " " these characters must be escaped with a "\".

     Target[bla]: 2:stu\ pi\@d@router



---

