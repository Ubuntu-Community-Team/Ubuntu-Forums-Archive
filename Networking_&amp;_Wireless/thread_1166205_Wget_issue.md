---
title: "Wget issue"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by rlopes528 on 2009-05-21
Hello folks, I have a dynamically generated sitemap 
([http://www.noticie.com.br/index.php?...l=1&lang=pt-BR]("http://www.noticie.com.br/index.php?option=com_sefservicemap&task=xmlmap&no_html=1&lang=pt-BR")), 
and I need to make a Cron job that copies this sitemap every hour to /sitemap.xml.

I'm trying to do this with Wget, but it doesn't seem to download dynamically generated pages correctly. Any ideas??

---

### Post by mrog on 2009-05-21
Put the url in quotes:

wget "http://www.noticie.com.br/index.php?option=com_sefservicemap&task=xmlmap&no_html=1&lang=pt-BR"

BTW, should the sitemap at [http://www.noticie.com.be/sitemap.xml](http://www.noticie.com.be/sitemap.xml) be different? The server doesn't seem to be updating it in a timely manner.

---

