---
title: "Logging network speed"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by t0p on 2009-02-12
I use a 3G mobile phone to connect my computer to the internet.  At certain times the connection speed is extremely variable.  I would like to log network speed, so I can do various statistical analyses on the figures.

Network speed is shown by the System Monitor (System > Administration > System Monitor).  But this just shows what the speed is at that moment.  I want to find/keep a log of network speed over an extended period, but I can't find where Ubuntu is logging this data.  I thought it would be somewhere in /var/log, but that doesn't appear to be so.

Can anyone tell me where I might find the data?  Or of a way I could extract the data from the graphical System Monitor?

---

### Post by jonobr on 2009-02-12
HEllo


You could use or investigating using SNMP.

You can search for it in synaptic.

The SNMP protocol allows you to query a lot of information from your system.

You query things called object identifiers,

These perform various functions, some which may be of interest to you are,
packets in or out of an ethernet interface.
Errored pakets, bytes transferred and so on.

Each one is represented by a long unique number

What you could do is on the command line enter

snmpwalk localhost -c public .1.3.1.x.x.x.x.x.x.x

where -c is the community string (password) to query.

With this info you could create a set of queries and put them in a file to run frequently.

May be overkill, but using SNMP is one of those things that makes like a lot easier

---

### Post by t0p on 2009-02-14
Oh wow!  SNMP is a pretty big subject huh? I've just been looking at some stuff at [Wikipedia]("http://en.wikipedia.org/wiki/Simple_Network_Management_Protocol") and [O'Reilly Media]("http://www.onlamp.com/pub/a/bsd/2000/07/27/Big_Scary_Daemons.html"), and now my head hurts! :(

Still, I don't think it's going to be difficult.  Seems there's a bunch of tools in synaptic to choose from, some of which will do pretty well all of it and create pretty graphs and tables for me.  Wonderful! :)

---

### Post by jonobr on 2009-02-17
HEy,

SNMP is like having a car, when you dont have it, you dont need it, when you are used to having it, you wonder how you lived without it.

It sounds hugely complicated, but there is only a few things you need to remember,

For SNMP there is a client and a server, 
the client has an snmp agent which listens requests and responds.

ITs protected by use of read and read write passwords (called community strings)
Your querying machine (server) has an snmp program like snmpwalk.
(or you can use a fancy gui like mrtg, opmanager etc....)

SNMP can issue a get, a get next, or a snmp set.

With the get, you need to know the number you want to query.
Most Internet devices have these numbers already there, you just need to enable the agent.
Once enabled you can query the numbers and get a mountain of info.

The rest once you know that , is all fancy-ness.
However, synaptic probably has a bunch of tools which either use SNMP or use something similar to track what you need


Cheers

---

