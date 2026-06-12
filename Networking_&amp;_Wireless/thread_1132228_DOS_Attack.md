---
title: "DOS Attack"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by ShinHadoken on 2009-04-21
I'd like to test out performing one or two DOS attacks on some test PCs I have set up here on my home network. Could anyone instruct me on how to perform one? (NO, I am NOT trying to use this knowledge for illegal purposes, or even a prank of some kind. I fully understand the consequences of DOS attacks, both technologically and legally. Last thing I need is black helicopters landing in my front lawn and the FBI breaking down the door) Seriously, just doing a little experimenting.

---

### Post by kidders on 2009-04-22
Hi there,

There's not a lot to it, really. Basically,  you need to craft a request that's unusually complex, and repeat it as many times as you possibly can, until the target service falls over.[LIST]
[*]Requests you know will cause errors are common choices, because error handling is typically relatively inefficient. 
[*]Malformed or illegal requests are also good choices, especially if you've read about a bug in a server you're running (eg a buffer overflow) that you'd like to try to trigger.
[/LIST]

One (old) network-level trick is to broadcast millions of over-sized ICMP packets with a spoofed source address. If the network is badly managed, every single machine on it will respond simultaneously to each ping, and flood the target machine with traffic.

Most of the time, application-level attacks are easier to get going in a test environment. You need to know the service you're attacking pretty well, though. For example, if you're running a web server, you could try to identify a page that meets as many of these criteria as possible ...[LIST]
[*]The web page isn't cached.
[*]Rendering it involves making a database request with complex subqueries, preferably including nasty operations like full table scans or sorting in opposition to a clustered index.
[*]The tables involved are big and/or badly indexed.
[*]The query involves constructing intermediate recordsets that are larger than the memory cache.
[/LIST]
The goal would be to trigger as much disk activity as possible, tie one of the web server's threads up for as long as you can, and lock a few database tables in the process. That way, it's easier to issue requests faster than the target service can fulfill them. If you've found an exploitable weakness, bombarding the web server with thousands of very slightly different requests will slow it down to the point that normal users can't use it productively.

Incidentally, I'm curious ... what in the world are you up to over there?!

---

### Post by ShinHadoken on 2009-04-24
Haha, just a little experimenting. Okay, so I know the principles behind it... what would be a practical implication on a home PC?

---

