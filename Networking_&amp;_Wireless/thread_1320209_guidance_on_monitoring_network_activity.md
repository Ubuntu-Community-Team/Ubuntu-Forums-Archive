---
title: "guidance on monitoring network activity"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by thinking on 2009-11-09
what i try to do:
currently i want to log timestamps of events during a tcp connection
those events are for example:
first packet
connection initialized
first packet which can be read by the application
first packet sent by the app
last packet read
last packet sent

im mostly interested in http(s) connections
i tought about using iptables, but i need to know 2 things:
will it be possible to log the events given on a keep-alive connection?
which means for tracking a http packet (request/response) i also need the first read after the last write and such.

how does such logging affect server performance?
i dont think there would be better options on performance, but some estimates on this would be great like
will the kernel block networking cause of the logging of those iptables rules cause he waits till the data is written on disk or such?

why i try to do:
pretty often we (devel department) get a request to investigate why our web apps are slow. mostly those problems are one timers. maybe a peak on the network or such. so its neither easily nor sometimes possible to know what was slow at that time

i want to know if the network was slow or the application is slow (difference between last read and first write, e.g. caused by cpu peak)

to know this i want exclude the lowest layer so we know
we have to investigate our application (e.g. using sprites or more/better JS)
thats why i want try getting data on the timing of our http applications used on the network

the question is:
is iptables the right direction? any hints on options which could be help would be great
are any tools available which already cover my needs?

thx

---

### Post by Lars Noodén on 2009-11-09
tcpdump 'tcp and dst port 80'

---

### Post by thinking on 2009-11-09
well
tcpdump would indeed be the easiest solution
i already thought about that

the thing is that tcpdump is a user space application and thus
it is possible that it dosnt log all packets cause of much load

thats why i thought about creating very specific iptables rules
to capture only what is needed and not everything

but for both apps i dont know how specific the rules can be and if im
able to create such specific rules without the need for
user space parsing and extraction after logging everything

---

