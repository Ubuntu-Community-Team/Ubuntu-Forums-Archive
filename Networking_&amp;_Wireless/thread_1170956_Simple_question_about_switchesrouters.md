---
title: "Simple question about switches/routers"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by Vunutus on 2009-05-26
I'm just trying to get a better grasp of networking technology found in many small offices. 

From what I know of the OSI model, switches are a layer 2 device and therefor cannot handle IP/Internet data. Routers are a layer 3 device and and therefor DO handly IP/Internet data.

Now the particular network I'm having trouble understanding is set up with all 30 or so workstations connected to a switch (and servers too I'd imagine but am unsure). All of these workstations have internet access. How can this be possible? Is my knowledge of networking flawed or am I missing a piece of the puzzle?

---

### Post by doas777 on 2009-05-26
> **Vunutus said:**
> I'm just trying to get a better grasp of networking technology found in many small offices. 

From what I know of the OSI model, switches are a layer 2 device and therefor cannot handle IP/Internet data. Routers are a layer 3 device and and therefor DO handly IP/Internet data.

Now the particular network I'm having trouble understanding is set up with all 30 or so workstations connected to a switch (and servers too I'd imagine but am unsure). All of these workstations have internet access. How can this be possible? Is my knowledge of networking flawed or am I missing a piece of the puzzle?

if they have internet, then there is a router in there somewhere. most newer switches are capable of processing L3 information (look into VLANs for instance) for advanced features, but some special ones are capable of acting as both switch fabric and routing node.

the internet is like any internetwork. in order to get from one network to the next, you need a router. it's there somewhere. easiest way to find the router is run 'route' (lin) or 'route print' (win) and look for the gateway IP for the Default or 0.0.0.0 route. thats the interior interface of your router.

another thing to check for is a proxy server. are the browsers configured to use one? many proxies act as routers, in that they forward outbound requests onto the internet and relay responses back to the client.

---

