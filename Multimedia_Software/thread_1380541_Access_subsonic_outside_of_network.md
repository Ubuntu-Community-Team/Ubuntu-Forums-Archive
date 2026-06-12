---
title: "Access subsonic outside of network"
date: 2010-01-13
forum: Multimedia Software
---

### Post by suevy Suavae on 2010-01-13
First, I hope this is in the right place.

Now onto the problem.

For a while now I have been trying to get subsonic running on my laptop (ubuntu 9.10) for use over the Internet. I got the actual program downloaded and installed/started just fine. I can even access from my computer by going to 127.0.0.1:8080. I can also get to it from other computers on the same network with 192.X.X.X:8080.

Heres where the problems start. I currently have a dynamic ip address. This seemed like a problem until I found no-ip.com. I set up a host that redirects to what was my ip at the time (according to whatismyip.com) and the port I was using, gave it a few minutes to sync, and put in the site name I had chosen. But, it didn't work. I then changed the ip address to 127.0.0.1 and later 192.X.X.X, both of which worked fine. This led me to believe that the problem lie elsewhere.

The only thing I can think of is that I am having a problem with the port forwarding I've set up. I've never done it before, but it seemed pretty straight forward. I gave the router the external and internal ports, as well as the internal ip address of the computer I'm running subsonic on (the laptop). But when I go to X.X.X.X:YYYY (X being Internet facing address and Y being the port) nothing happens.

The router is a Linksys WRT160N.

If any other information is needed or a solution is proposed, please feel free to respond.

---

