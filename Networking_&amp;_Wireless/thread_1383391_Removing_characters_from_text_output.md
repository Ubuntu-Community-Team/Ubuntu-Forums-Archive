---
title: "Removing characters from text output"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by buee on 2010-01-17
I'm working on MRTG and I'm looking to graph uptime on remote machines.  There have been other occasions that I've needed this function.

When I probe my SNMP device, I get this output:

```
HOST-RESOURCES-MIB::hrSystemUptime.0 = Timeticks: (2229625) 6:11:36.25

``` 

What I want is this:

```
2229625
```

So I need to delete the first 51 characters of the line and the last 13 characters of the line.  I can't just use grep because that number changes 30 times a second from what I can tell.  Somewhat like using head and tail to pick one line out of a paragraph.  Is there a way to do this?  Preferably with bash as that's really the extent of my knowledge.

---

### Post by sisco311 on 2010-01-17
```
**command** | sed "s_.*(\(.*\)).*_\1_"
```
or
```
**command** | awk -F "[()]" '{print $2}'
```

---

