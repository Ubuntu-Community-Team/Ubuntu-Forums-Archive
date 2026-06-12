---
title: "Proxy all Applications through Tor"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by Depravitus on 2011-09-07
Greets,

I've been wracking my brain trying to get my system set up to utilize a 'transparent proxy' of all applications through Tor, as described on their page here: [https://trac.torproject.org/projects/tor/wiki/doc/TransparentProxy](https://trac.torproject.org/projects/tor/wiki/doc/TransparentProxy) ... The goal being to, by default, force ALL outgoing traffic from the user on this system through the Tor network (speed is a secondary concern after security).

Admittedly, I am uncomfortable with IPTables at this point and how it works.

If anyone is familiar with running a user > privoxy > tor configuration and would like to help me, I would greatly appreciate it. Adding Squid to the chain before privoxy seems popular as well, and I am open to that possibility.

I was successfully able to set up Tor to work on a per-application level with applications that support SOCKS proxies, but again I want the proxying to occur on the OS level without having to configure apps (assuming they even support SOCKS which many dont). 

Thanks for reading, and sorry for the vague nature of my query.

---

### Post by Depravitus on 2011-09-08
Been a day or two and no response, so just giving this a light bump. :) 

Still no luck on my end.

---

