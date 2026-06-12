---
title: "PDNS vs DNSmasq..vs nscd?"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by Diskdoc on 2009-11-19
It's a couple of years ago now since I first read about how to cache DNS responses locally to speed up internet access. The instructions I found described the usage of dnsmasq for this purpouse, but I'm not sure it is the best solution anymore.

Am I right in thinking dnsmasq only caches DNS responses per-session? (i.e. the cache is lost on reboot) Does this matter?

There seem to be a couple of other programs around for the same purpouse. pdns-recursor seems to be gaining popularity..but some instructions say you should use pdnsd - which would be better? One keeps the cache between reboots, the other doesn't?

And is nscd anything to consider?

I'm also curious about Ubuntu not coming with a local DNS cacher enabled by default..I read somewhere that browsers do their own DNS-cacheing nowadays but many other Internet applications don't. Wouldn't it be a good thing? And maybe an option during install to enable OpenDNS too?

---

### Post by gregsmith_to on 2009-11-29
I've just set up nscd and it appears it does not work at all, at all. Bell Sympatico DNS has degraded so DNS reqs are often 3-10 seconds now, so I tried nscd, but using wireshark (and socket.gethostbyname in Python) I find that nscd is seeing the requests (logs appear when using nscd -d) but all the requests go the network. Wireshark shows that the responses all have reasonable TTL (5 mins to 1 hr). I adding a 'log' option to the nscd.conf, and it creates the file, but hasn't written anything to it. Many of the messages in the 'nscd -d' output contain gibberish host strings so possibly there's an outright bug in nscd (this is a 64-bit machine). 'nscd -g' shows that there are sometimes a few values in the cache, but I think they are cached misses; I've never seen a non-zero value in the hit/miss count except for 'cache misses on negative entries'.

Here is some example output from nscd -d  (I've replaced unprintable characters with @ signs)

5198: handle_request: request received (Version = 2) from PID 5251
5198: 	GETHOSTBYNAME ([www.wikipedia.com](www.wikipedia.com))
5198: handle_request: request received (Version = 2) from PID 4862
5198: 	GETSERVBYPORT (@@@:@@/udp)
5198: Haven't found "@@@:@@/udp" in services cache!
5198: handle_request: request received (Version = 2) from PID 4862
5198: 	GETSERVBYPORT (@)
5198: Haven't found "@" in services cache!
5198: handle_request: request received (Version = 2) from PID 4862
5198: 	GETSERVBYPORT (@)

Ubuntu 8.10, nscd 2.7-10ubuntu5, X86_64

---

### Post by gregsmith_to on 2009-11-29
Actually, this issue with nscd not working *might* be because I'm not booting the latest installed kernel (which probably also explains why none of the net config programs will let me change anything, so I can't try changing the DNS). This is because I installed nvidia's latest official  driver several weeks ago in order to use CUDA, and after ubuntu pushed a kernel update, nvdia doesn't want to build against it, claiming that the headers aren't there (they are). Grrr. And to make things worse, whenever the display driver doesn't load, the network interface is also disabled (maybe it conflicts with VGA?). Fun. Project for today is to see if I can switch back to the ubuntu-approved (and far less buggy) display driver without gorking the machine.

---

