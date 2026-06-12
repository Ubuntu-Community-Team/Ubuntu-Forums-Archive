---
title: "Need a bit of help setting up Squid"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by Matamane on 2009-11-29
I really could use some step by step, basic english instructions.

all i've done so far is

**sudo apt-get install squid** **squid common**


and before I start screwing around with my proxy, I would like a direction.

---

### Post by headvampyre@hotmail.co.uk on 2009-11-29
what do you want the proxy for coz usually they are only used in webservers to bypass filtering

---

### Post by Matamane on 2009-11-29
Trying to bypass country restrictions on youtube, and hopefully play online games at school.

---

### Post by pdc124 on 2009-11-29
deliberately trying to bypass your school internet security is almost certainly a disciplinary offence .
If you think you know more about it than the IT guys  at school feel free to have go.

I would configure your firewall to prevent access to squid from the outside ( otherwise you are running an open proxy which will get abused ), start it and then see if you can connect to it from a browser on your LAN. 

once youve got that sorted, add some security and once that  is in place , open it up to the outside

---

