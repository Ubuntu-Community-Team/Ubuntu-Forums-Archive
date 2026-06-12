---
title: "Tunnel Plone site through HTML page..or whatever"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by pietbuntu on 2010-10-21
My situation:

I am at a university which has an intranet. I have a Plone site running on my personal PC (with a static IP) in my office.

I need to access this Plone instance over the internet, but the university firewall keeps me from doing this.

I have another account on a public server which I am able to access from the outside. I was wondering if I could 'tunnel' (for lack of a better word) traffic to the Plone instance via HTTP through the accessible server?



I was thinking to maybe run a python script that reroutes the traffic through the website on the accessible server..

Any help would be appreciated!

---

### Post by tsanos on 2010-11-04
Hi,
I think that you need a proxy.
To publish your plone if you administer the public web server you can setup a proxy through apache mod or by an .asp script.
To override the firewall you could need something different. A http tunnel or a ssh tunnel.

---

