---
title: "DNS resolv.conf comcast coopt"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by Alfie O'mega on 2010-02-26
I signed up for comcast internet last month.  This past week I noticed that when I mistyped a domain name it would come up with a comcast search page.  Some investigation indicates that comcast helpfully injected something into my resolv.conf file

domain hsd1.va.comcast.net.
search hsd1.va.comcast.net.
nameserver 68.xx.xx.xx
nameserver 68.xx.xx.xx
Who knows about DNS? 

Questions:

1.  Can I safely get rid of this and get a normal error page? 
2.  How do I get comcast out of my face and resolve to another DNS of my own choosing? Any suggestions on which ones I should choose?
3.  Comcast's network management page says they're going to go to DNSSEC soon.  From a pratical pov, what does this mean?
4.  Are there any dns tutorials around?

Thanks,

Al

---

### Post by Brandon Williams on 2010-02-26
I assume that you are getting your IP address using dhcp. If that's the case, then you can make your machine stop requesting the domain-name and domain-name-servers by editing dhclient.conf. Look for the request configuration. In my config, it looks like this:
```
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;
```
If I remove domain-name, domain-name-servers, and domain-search from the list, then the domain, search, and nameserver entries will not be added to resolv.conf. Then, if I add a line like this:
```
prepend domain-name-servers 8.8.8.8;
```
an alternate nameserver entry should show up in my /etc/resolv.conf (in this case, it's Google's DNS). I can't test it right now, since I don't want to break my connection, but if it doesn't work exactly as I described, this will hopefully at least point you in the right direction.

Having explained this, I will also say that I recommend against this approach. 25% (or more) of the internet goes through accelerated content delivery systems that rely upon trying to get a reasonable sense of your location from your DNS server. This includes commerce, media, and government sites, among others. If you use a centralized DNS server, like Google's DNS or OpenDNS, you are more likely to lose the benefit of such sytems by being mapped to a bad location. In my view, it's worthwhile putting up with the annoyance of these stupid error redirects to get better mapping that will make my online experience better.

I don't have response for your points 3 and 4. Hopefully someone else will.

---

### Post by Alfie O'mega on 2010-03-01
Thanks Brandon! I will try this.

Al

---

