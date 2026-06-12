---
title: "Serve Website to Home Network Only"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by lancealbertson on 2011-03-05
I would like to serve websites to my home network only. 

It's a simple network - half a dozen clients running through a WRT54G2 (that also connects to the internet). I have a server with a static IP set up (running apache2).

    1) I would like to be able to access those sites from other machines on the network.

    2) I don't have a domain name, I just want to be able to access something locally, such as having "Homesite" resolve to 192.168.1.2:80. I would prefer to have single word names, but having my own artificial TLD (like .home) that would be okay, too.

    3) I would like the site names automatically detected rather than hand-editing a file to get them on the system. In other words, when I enable a site on apache, I don't want to edit another file in order for the site to be visible from other computers on the network.

    4) I do not want the site to be visible outside my home network.

My assumption is that I need to set up some sort of DNS service on the server and add the server as the first DNS server on the router.

However...

I have looked at BIND and dnsmasq and, though I have a general understanding of DNS, there are so many options and combinations that it all dissolves into gobbledygook. I don't want complicated. I don't want DNS maintenance. I want to spend my time working on the sites, not DNS.

Any thoughts? What should I use (BIND, dnsmasq, something else)? And *MOST IMPORTANTLY*, what settings should I use?

Thanks so much!

---

