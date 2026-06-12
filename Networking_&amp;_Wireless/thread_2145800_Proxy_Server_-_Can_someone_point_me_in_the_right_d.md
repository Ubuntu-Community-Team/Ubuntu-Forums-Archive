---
title: "Proxy Server - Can someone point me in the right direction?"
date: 2013-05-16
forum: Networking &amp; Wireless
---

### Post by RedShoeRider on 2013-05-16
Good Day, All:

  I just need a little nudge in the right direction. :)

  What I want to do is set up a proxy server that I can access from anywhere (especially work), to port me though to the multitude of sites that are normally restricted*, and to give me a secureish link to the outside world when I'm on a public WAP. Simple user authentication is key, as this will not be an open proxy. In a perfect world, I'd type in https://www.<mysitehere>.proxy.com, and it would bring up a login and password screen. Type that in, and some kind of interface would come up that allows me to head out to the rest of the world. This isn't a strange request; I figure that there has to be a package (or set of packages) that can bring me in this direction. 

  I've found pages and pages of information about squid, but they all deal with setting up transparent proxies for an internal network. I figure someone has to be running exactly what I'm thinking of, and rather than spend the next 10 hours abusing Google, I could pick a brain and save some of those hours.
  
  If it matters, this is a Server 12.04 installation, no GUI. 


Thanks, all!
-Red

*= I know there are all sorts of legal/don't do it you'll be fired/questions about skirting corporate rules regarding blocked sites. We technically don't have such a policy, so I'm not overly worried about it.

---

### Post by linuxtechguy on 2013-05-17
You can do it with squid, apache or even a ssh tunnel with putty or other ssh client.

---

