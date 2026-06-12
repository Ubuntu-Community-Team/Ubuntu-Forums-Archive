---
title: "&quot;The connection has timed out&quot; - no connection!"
date: 2012-12-12
forum: Networking &amp; Wireless
---

### Post by lsg0316 on 2012-12-12
Hi,
I recently installed a fresh Ubuntu 12.04 LTS on a desktop, and the installation itself was successful (other than 'grub rescue' issue that I encountered but fixed) but this connection problem is really giving me a headache.

Symptoms:  
1. When I open the FireFox browser and try to connect to a website, it just hangs for a while saying "Connecting..." but eventually loads an error page "The connection has timed out".
2. It's not a browser problem (and I tried setting ipv6 thing to "true" at about:config) because running "sudo apt-get install [some-random-package]" at terminal fails ("E: Unable to locate package [package]") too. All other operations that need internet access are not working.
3. I certainly see a wired network (called "eth1") at the Network Manager, and it says "Connection Established" after disconnecting and then connecting again.

I have tried almost everything that could be found from google search results still no luck. Their problems slightly differ from mine or the solutions just don't work.

By the way it didn't have internet access when installing Ubuntu 12.04. (I ignored the message that I need internet to install Ubuntu) Could this be a problem? I'm sorry I don't remember if internet worked or not on the previous version of Ubuntu.:sad:

I would really appreciate your help... I don't even know what more to do if this fails too..
Thanks!!

---

### Post by lsg0316 on 2012-12-12
Problem solved!
Sorry, I just had to set the Network Proxy to some address my boss told me. I should've asked him earlier haha...
Thanks anyway!

---

### Post by sammiev on 2012-12-12
Please go up to Thread Tools and mark this as solved for the next folk. :)

---

