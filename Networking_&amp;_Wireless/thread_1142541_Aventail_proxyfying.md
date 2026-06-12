---
title: "Aventail proxyfying"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by osha on 2009-04-29
Hey,

I have a question about the proxyfing of the network connections through multiple proxies (to customer locations /domains) . So here's the story:

Before I moved to ubuntu from windows, I was using "Aventail connect" utility to connect to other locations (customer domains) through proxies, usually more then one proxy. The aventail was running as a service and had automatically detected (by the ip range given in the configuration file) the network I needed. This all worked as 1 confif file for multiple neworks (different proxies).

Then I moved to Ubuntu and started to use proxychains, because any other way (proxy settings in browser or even the global proxy config in ubuntu) it only offered one proxy at a time, however as mentioned more proxies were needed. With proxychains I have no issues to connect where I want, but the thing is, that I allways have to use the command line to run the particular program I want to use, to have it proxyfied. That wouldn't be a problem if I didn't have to use multiple config files for every location I need to reach -> i.e create directory with every location config file and run the program (the one to be socksified) from there.

That makes me kind of upset so I'm wondering if there's any better solution of doing the chaining. Aventail also exists for linux, but there is also need of changing different configs and more over it does not support more then one proxy (no chain). I'm looking for something that would run in background, so that I don't have to care about the proxies any more and that would automatically use the correct proxy chain to a location but would still made me able to use the rest of the locations at the same time.

Hopefully that describes my problem enough :) Thanks in advance for any suggestions.

---

