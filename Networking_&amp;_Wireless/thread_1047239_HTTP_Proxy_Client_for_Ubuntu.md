---
title: "HTTP Proxy Client for Ubuntu?"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by kwisatz h on 2009-01-22
Relatively new to Ubuntu (actually running Eeebuntu Standard on my Eee PC)... a very recent convert to linux from Windows environments...

One thing I need in order to get many things working while at work is a proxy client as my workplace funnels *everything* through workproxy:80. :/

I've found two options which look promising, but frankly I dont seem to have the linux skills to even know what to do with them...
**a) HTTP Proxy Client ([http://httppc.sourceforge.net](http://httppc.sourceforge.net))**; how on earth do I even install this? I've read the notes but just dont get anywhere with the 'make' commands, etc...?
**b) Proxy Tunnel ([http://proxytunnel.sourceforge.net](http://proxytunnel.sourceforge.net))**; but again, I just dont get it... what do I do to install and use this?

Anyone have some insights to share? I have more than 12+ years of IT in Windows and Networks, but completely baffled by my week of experience with linux...

Thank you to anyone who can me understand what I need to do...

Cheers,
Dustin H

---

### Post by sfjohnsen on 2009-05-02
Kwistaz Haderach, can't you divine the answer to your question?
Only kidding... libHTTPPC replaces certain system library functions such that you can use programs that are not really designed for proxy use through a proxy, so if you only want to surf the internet with a commonplace browser like firefox, then it's complete overkill. If you use firefox, google up a proxy list, pick one that appears suitable for you (based on your location) and then, in firefox, click "edit" in the menu bar then go to "preferences", next choose the "advanced" tab, then choose the "network" subtab, there click on the "settings" button. In the window that pops up, choose "manual proxy configuration" and enter the data you got from the proxy list, i.e. the url and the port. If you use another browser than firefox a quick google search of "<your browser's name> proxy configuration" will surely give you the right instructions.
HTH, Good luck.

---

