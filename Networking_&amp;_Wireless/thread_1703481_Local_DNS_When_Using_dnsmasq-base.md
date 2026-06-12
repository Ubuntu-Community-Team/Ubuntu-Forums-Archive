---
title: "Local DNS When Using dnsmasq-base?"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by aaaantoine on 2011-03-09
Hello.

Due to a television failure, I was forced to set up my Xbox 360 in my office.  I have it plugged into my monitor, I have sound routing to a pair of headphones, and I have it getting a network connection from my desktop computer.

I had an issue at first setting up a shared connection.  It turns out I had dnsmasq installed, and this conflicts with dnsmasq-base which is required by NetworkManager.  Once I removed dnsmasq I was able to get a network connection to my Xbox.

But now, I no longer have a local DNS cache.  And I don't know what the deal is with my DNS server, but it can take 5-10 seconds to resolve an address.  When I have a local cache, page responses often come back nearly instantaneously.

I want my local cache back, but I don't want to break the shared connection with my Xbox.  What is the best way of doing this?

Thanks in advance.

---

