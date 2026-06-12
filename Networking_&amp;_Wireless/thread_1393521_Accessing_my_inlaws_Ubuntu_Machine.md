---
title: "Accessing my inlaws Ubuntu Machine"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by mvalenti on 2010-01-29
I installed ubuntu on my inlaws machine, they seem to enjoy it. Occasionally when we visit, 1 hour away, I am being asked to fix something, like install flash or something... What would be the best way to remote access that machine from my house to perform these tasks? Tutorials on this stuff is a biiig help....


Thanks all!

-Mark

---

### Post by llawwehttam on 2010-01-29
If you set up their router with port forwarding then ssh is very good.

---

### Post by Swagman on 2010-01-29
Remote Desktop

But good luck with that. I've never been successful connecting to anyone on a WAN.

I've been talking to a mate on irc  who's on ubuntu.. followed all the procedures and still no luck. Obviously we are both behind a router but it must be possible otherwise no-one would ever get hacked.

Plus... Remote support on windows always work without needing to faff about in your router.

Unless that's our "My Wings are like a shield of steel" cloak of invincibility ?

---

### Post by Skaperen on 2010-01-29
> **Swagman said:**
> I've been talking to a mate on irc  who's on ubuntu.. followed all the procedures and still no luck. Obviously we are both behind a router but it must be possible otherwise no-one would ever get hacked.
Once the router is listening on a port and forwarding it properly, and the ISP is allowing incoming connections to the selected port, it should be good to go.

There are a number of ports I recommend to no leave open, and the default ssh port number 22 is one of them. In the case of ssh, lots of "kiddies" are trying to crack them, usually by password dictionary attacks. Even if you use strong passwords and/or keys, this can still waste some traffic and flood logs (annoying when you need to find details about some issue).

ISPs may be blocking 22 and 23 for reasons like this.

My point is, pick a non-standard port for ssh and configure the router to forward that port number to the computer's port 22 (or even change that, too, just to be sure). Then you use the -p option on ssh/scp to select the port.

It's still possible for the ISP to be blocking all incoming TCP connections. I don't know of any doing that, but there might be some. Also be sure your outgoing connections are getting through.

---

