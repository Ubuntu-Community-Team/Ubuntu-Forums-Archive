---
title: "How do I block people from a specific site if they use my router?"
date: 2012-04-21
forum: Networking &amp; Wireless
---

### Post by HunterDX77M on 2012-04-21
Hey guys,

I'm a total noob when it comes to anything related to networking or wifi. I want to block access to Facebook for anyone using the internet connection from my router. My brother has been spending (correction -- wasting) too much time there and his school work is suffering. He has 0 will-power, so I've decided to do this. Is this possible and how can I do it? Thanks for the help.

---

### Post by lethalfang on 2012-04-21
> **HunterDX77M said:**
> Hey guys,

I'm a total noob when it comes to anything related to networking or wifi. I want to block access to Facebook for anyone using the internet connection from my router. My brother has been spending (correction -- wasting) too much time there and his school work is suffering. He has 0 will-power, so I've decided to do this. Is this possible and how can I do it? Thanks for the help.

Your router has to support it. 
Go to your router's configuration website (e.g., 192.168.1.1 or whatever it is), and see if it has an option to block a particular website.

---

### Post by newbie-user on 2012-04-23
There are several options to block websites. Using keyword blocking on your router is one way to do it. An alternative is OpenDNS, which is free for a personal account. A third option is setting up a squid proxy server, requiring all clients on your network to proxy through it, and blocking the sites on the proxy.

---

### Post by SeijiSensei on 2012-04-25
If your brother isn't too knowledgeable about computers, you could edit his "[hosts]("http://en.wikipedia.org/wiki/Hosts_%28file%29")" file one day when he isn't home and point [www.facebook.com](www.facebook.com) and facebook.com to the 127.0.0.1 address.  The link will tell you where the hosts file is stored on various computer platforms.

---

### Post by iponeverything on 2012-04-25
> **HunterDX77M said:**
> Hey guys,

I'm a total noob when it comes to anything related to networking or wifi. I want to block access to Facebook for anyone using the internet connection from my router. My brother has been spending (correction -- wasting) too much time there and his school work is suffering. He has 0 will-power, so I've decided to do this. Is this possible and how can I do it? Thanks for the help.

A good option might also be to limit access to just certain times.

---

