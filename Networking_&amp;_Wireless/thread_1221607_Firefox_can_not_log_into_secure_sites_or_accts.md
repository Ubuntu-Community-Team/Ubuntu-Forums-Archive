---
title: "Firefox can not log into secure sites or accts"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by Tensaichen on 2009-07-24
I am a recent convert from Windows and having a problem with Firefox/Opera that I can not resolve from searching.  I can browse the web fine, but the moment I tried to log into a secure site with acct (Newegg, Amazon, Gmail, etc), the browser just hangs and eventually times out.

It seems like whenever the web address starts with https, then I would have problem logging in.  Running Firefox through WINE works for Amazon, but not Newegg or Gmail.  It's a bit ridiculous that I have to boot up Windows so I can make purchases.  Someone please enlighten me. 

thanks,

---

### Post by superprash2003 on 2009-07-24
try changing your MTU value ..
for reference : [http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html](http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html)

---

### Post by Tensaichen on 2009-07-24
I tried changing the MTU values, it didn't do the trick :(

Thanks for the suggestions though.  Any other ideas?

---

### Post by Tensaichen on 2009-07-25
It turned out the improperly configured firewall was the culprit.

---

