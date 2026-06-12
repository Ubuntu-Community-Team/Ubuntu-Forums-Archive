---
title: "Wireless card is connected but no internet..."
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by AlexBryan on 2006-06-08
I have a foxconn WLL-3350 which works out of the box. It connects as ra0, and it scans and picks up my network in ESSID. I entered my WEP key and activated it but firefox won't load any webpages. In the other network program under administration (i forget the name) i can see the ra0 is receiveng data etc. so why can't i connect to any web pages?

---

### Post by ComplexNumber on 2006-06-08
[quote=AlexBryan]I have a foxconn WLL-3350 which works out of the box. It connects as ra0, and it scans and picks up my network in ESSID. I entered my WEP key and activated it but firefox won't load any webpages. In the other network program under administration (i forget the name) i can see the ra0 is receiveng data etc. so why can't i connect to any web pages?[/quote] go to firefox and type in 'about:config' in the address bar. then do a search for "v6". set it to "true". you may notice that you can connect using firefox if you typoe in the adress in the form XXX.XXX.XX.XX (eg 216.259.45.75) but not when you type it in the form [www..]("http://www..")..

---

