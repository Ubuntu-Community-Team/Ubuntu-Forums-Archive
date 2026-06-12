---
title: "Can't access some sites using mobile broadband"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by Nevon on 2009-06-03
I'm currently using one of those mobile broadband modems to connect to the internet. It's working fine for the most part, but for some reason there are two sites that I can't seem to access: [www.ungdomar.se](www.ungdomar.se) and Wikipedia.

I don't get any error messages, and it doesn't say "site can't be found" or anything. The sites just never stop loading. I know they're not down, as other people have no problem accessing them.

I've tried downloading the pages using wget, to see if the problem is with the browser, but wget also fails. With ungdomar.se it says:
"--2009-06-03 07:25:34--  [http://www.ungdomar.se/](http://www.ungdomar.se/)
Resolving [www.ungdomar.se](www.ungdomar.se)... 62.181.238.54
Connecting to [www.ungdomar.se|62.181.238.54|:80](www.ungdomar.se|62.181.238.54|:80)... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://ungdomar.se/](http://ungdomar.se/) [following]
--2009-06-03 07:25:37--  [http://ungdomar.se/](http://ungdomar.se/)
Resolving ungdomar.se... 62.181.238.54
Reusing existing connection to [www.ungdomar.se:80](www.ungdomar.se:80).
HTTP request sent, awaiting response... 403 Forbidden
2009-06-03 07:25:37 ERROR 403: Forbidden."

And with Wikipedia it gets to about 97% and then just stops (when surfing it stops when trying to download something from meta.wikipedia.org). 

It's very, very annoying. Does anyone know what the problem could be?

---

### Post by superprash2003 on 2009-06-03
try changing your DNS servers to opendns - 208.67.222.222 and 208.67.220.220 [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by markvdm on 2009-06-03
I have (I guess) the same sort of problem. I use ICS from my Windows Mobile phone, but there are a whole heap of sites I cannot access. Just stays on the loading screen. It sometimes times out, but only after about 5 minutes. I have tried the OpenDNS settings, but still cannot access the sites.

---

### Post by Nevon on 2009-06-03
The weird thing is that I've been able to connect to the site before. It just started acting this way yesterday. Wikipedia has been a bitch for the last couple of months though.

---

### Post by markvdm on 2009-06-03
I also don't understand why I can browse certain sites, and others not at all. I've run every network tool I can find to try and figure out a way forward, but at the moment I'm completely dead in the water. Vista will have to hang around my HDD for a while longer it seems.

---

