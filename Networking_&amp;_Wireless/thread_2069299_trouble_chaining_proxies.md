---
title: "trouble chaining proxies"
date: 2012-10-10
forum: Networking &amp; Wireless
---

### Post by proxy error on 2012-10-10
**trouble chaining proxies** 			
 			 			 		   		 		 		hows it going?

i am having trouble chaining proxies.  i open terminal, run

[I]nano /etc/proxychains.conf

[/I]i add the list like this

[I][ProxyList]
# add proxy here ...
# meanwile
# defaults set to "tor"
socks4  127.0.0.1 9050
socks5  59.21.114.99    5577

[/I]i open a new tab, run

*proxychains firefox*
all i get is this

*ProxyChains-3.1 ([http://proxychains.sf.net](http://proxychains.sf.net))*

firefox opens but when i google my ip address it is not what it says in the list

pleaqse help

---

### Post by coffeecat on 2012-10-10
Yet another duplicate thread closed. One thread per topic please.

---

