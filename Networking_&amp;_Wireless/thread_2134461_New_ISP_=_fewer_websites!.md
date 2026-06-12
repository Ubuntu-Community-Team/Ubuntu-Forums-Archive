---
title: "New ISP = fewer websites!"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by cooldot on 2013-04-11
Getting a bit sick and tired of the effort required just to keep Ubuntu usable now!

Earlier today everything was good with the world. We changed broadband provider, which meant our subnet changed from 192.168.1.x to 192.168.0.x and we have a new router.

I have laptops and tablets that are all working, but since the changeover the computer I use (which is wired network and uses Ubuntu 12.10) will only access some websites. Others just time out. I have checked /et/hosts and also /etc/NetworkManager/NetworkManager.conf but can't see anything wrong with them. I have also commented out dns=dnsmasq and restarted the whole computer. I use DHCP.

The ONLY things that have changed are my provider, the router and subnet. Output from ifconfig looks fine.
I can ping the websites that don't work in the browser.

Any ideas? :)

---

### Post by steeldriver on 2013-04-11
It's possible your new ISP has a 'black hole router' somewhere - try a ping test to see if a lower MTU will help:

[http://ubuntuforums.org/showthread.php?t=2071761&p=12302694#post12302694](http://ubuntuforums.org/showthread.php?t=2071761&p=12302694#post12302694)

or just lower the MTU value in the connection editor applet and see if that helps

---

### Post by kuifje09 on 2013-04-11
Do you have a real ethernet connection or PPPoE  or even different. Several protocols several packetlength.
Strange you have to take notice of, I would think it is an automatic process.

For some background search the web    (  tcp/ip  packets  mtu .. )

This might help in the first place.. [http://support.microsoft.com/kb/314496]("http://support.microsoft.com/kb/314496")

But anyway, this is very strange and should not happen. I would make a big complaint at my provider.

---

### Post by cooldot on 2013-04-11
Thanks for your replies, I'm just going to flatten everything and start again.

Paul :)

---

