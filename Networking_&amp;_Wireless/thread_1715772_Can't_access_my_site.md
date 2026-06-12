---
title: "Can't access my site"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by Necro5 on 2011-03-27
Hi,

When I'm trying to access my site using Firefox I get this error:

"Unable to connect

Firefox can't establish a connection to the server at *mysite.com*.


    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.
    *   If you are unable to load any pages, check your computer's network
          connection.
    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web."

Then I tried to access my site using Opera and Chrome but I get the same error, that the browsers couldn't connect to it.
The site to which I'm trying to connect is definitely up. (I ask a few people and they can access it and I looked at [http://www.downforeveryoneorjustme.com/](http://www.downforeveryoneorjustme.com/) and it says that my site it's up)

Does anyone know how can I solve this problem? Any reply will be highly appreciated.

---

### Post by tgm4883 on 2011-03-27
Can you get to your site by IP address? Could be a DNS issue.

---

### Post by Necro5 on 2011-03-28
No I could connect even with by IP, but now, after removing all from cache and doing messing with the firewall I am able to see my site again. :)

---

### Post by netopalis45 on 2011-03-29
have you made sure that you are connected to the internet? try using the ifconfig command in a terminal to see if you have a connection to anything except lo (loopback). if you do try pinging the site. if not you need to try connecting to your network

---

