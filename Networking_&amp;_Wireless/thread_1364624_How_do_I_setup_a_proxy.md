---
title: "How do I setup a proxy?"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by Captain_Glen on 2009-12-26
I am trying to listen to last fm for free buy using a us or uk or German proxy.

I have found a bunch at [http://www.proxy4free.com/page1.html](http://www.proxy4free.com/page1.html).

But when I goto System -> Preferences -> Network Proxy and select Manually proxy configuration and enter the proxy url and click Apply System Wide, I get an error in firefox:

The proxy server is refusing connections

Firefox is configured to use a proxy server that is refusing connections.

    *   Check the proxy settings to make sure that they are correct.

    *   Contact your network administrator to make sure the proxy server is
          working.


I have tried entering the following in HTTP proxy:

proxfilter.info
proxy.virtuaos.com

How do I setup a proxy?

Any help would be appreciated.

Thanks,
Glen.

---

### Post by Barriehie on 2009-12-26
Try telling only FF to use the proxy.  Edit > Preferences > Advanced > Network > Settings.

Barrie

---

### Post by Captain_Glen on 2009-12-26
I have tried setting up the proxy only in fire fox but I get the same error.  What do I put in the boxes???  I must not be filling it out properly.

Anyway.  Even if it did work, which it didn't, it is not what I want.  I want a proxy for Rhythmbox so I can listen to last fm.

---

### Post by Barriehie on 2009-12-26
> **Captain_Glen said:**
> I have tried setting up the proxy only in fire fox but I get the same error.  What do I put in the boxes???  I must not be filling it out properly.

Anyway.  Even if it did work, which it didn't, it is not what I want.  I want a proxy for Rhythmbox so I can listen to last fm.

I tried in Rhythmbox and it wanted a username and password.  It worked fine listening to it through FF.  I don't know about external proxies, I'm running squid locally on my machine so I am my own proxy.  Squid is a bit to setup but you can check it out at [it's homepage](http://www.squid-cache.org/).

Barrie

---

### Post by Captain_Glen on 2009-12-26
If I use squid, can I fool websites into thinking I am in the USA?  Or will they still think I am in Australia as my squid server is in Australia.

I have worked out that I need to know the IP address and port number of the proxy server in the USA to get a USA IP address.  I have found a bunch at [http://www.hidemyass.com/proxy-list/]("http://www.hidemyass.com/proxy-list/") but none of them seam to work.

---

### Post by Barriehie on 2009-12-26
> **Captain_Glen said:**
> If I use squid, can I fool websites into thinking I am in the USA?  Or will they still think I am in Australia as my squid server is in Australia.

I have worked out that I need to know the IP address and port number of the proxy server in the USA to get a USA IP address.  I have found a bunch at [http://www.hidemyass.com/proxy-list/]("http://www.hidemyass.com/proxy-list/") but none of them seam to work.

I don't think there are any guarantees as to where you'll be detected at.  I tried using tor with FF and just about everytime I went to google I ended up in a european country; i.e. I can't read swedish!  I don't have squid setup to hide, I'm using it as a net filter to block sites.

Barrie

---

