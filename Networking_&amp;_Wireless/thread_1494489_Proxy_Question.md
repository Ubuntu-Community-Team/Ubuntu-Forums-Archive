---
title: "Proxy Question"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by Whisp3r on 2010-05-27
I have SSH setup on my home computer for my laptop to proxy through. 

When I setup Firefox manually to use the SSH server as a proxy, I have no problem passing my traffic through and browsing the web (IE, 127.0.0.1, port 8080). However, when I set up FoxyProxy to use the exact same settings, it acts like a sink hole and I can't connect to anything. The page doesn't load. If I try to QuickAdd the site, it just says that it already matches my pattern (IE, *). The page just sits there and is white. There is no error message. The little blue foxy symbol is up and running, so I know it's using all URLs and isn't an access problem. Any thoughts?

Update: I enabled FoxyProxy logging and it does show my attempt to connect to the site. I'm just stumped thy the settings don't work with Foxyproxy, but if I enable them manually, it does.

Update 2: I figured out the problem. I hadn't checked the box "Socks Proxy?" under the settings. I'm a doofus. Sorry for wasting the space. :)

---

