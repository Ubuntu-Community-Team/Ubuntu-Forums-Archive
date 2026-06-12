---
title: "No internet....but have wireless connection"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by PDA1 on 2010-05-20
I'm using 10.04

Here's an odd one for you-

I tried to connect to a free WiFi connection.  I had the password for it too.  I had been able to access the connection 2 weeks ago with no real trouble.  Now, the thing at the top of my screen indicates I'm connected BUT I can't get Firefox to access any sites.  I can't download email using Thunderbird.  Pretty strange isn't it?

Any ideas what might be wrong?

---

### Post by Peter09 on 2010-05-20
A lot of free wifi sites these days want you to login or register through your browser before they allow access, are you sure that this is not whats happening.

---

### Post by PDA1 on 2010-05-20
I left certain details out to make the situation more understandable to me.  It's not really a free WiFi site.....I just couldn't think of the proper term for it.  It was a business I visited that had web access and I was trying to connect to their system.  No one at the business could figure out why I couldn't connect today

Your Terminal command stuff is meaningless to me.  What are you talking about?

---

### Post by Peter09 on 2010-05-20
Sounds very much like a routing problem to me, may be no DNS server access.

---

### Post by PDA1 on 2010-05-20
What does that mean?

---

### Post by Peter09 on 2010-05-20
When you log on your computer is given the address of a DNS server (Domain Name Server) it is responsible for providing the ip address (computer speak) of the site you want.

When you try to go to [www.google.com](www.google.com) (people speak) your computer asks the DNS server what the ip addres (computer speak) of google is. Its through ip address the computers navigate the web.

No DNS server no internet connections

---

### Post by sanderd17 on 2010-05-20
EDIT: sorry, no answer.

I suggested to go to the ip-adres of google but it seems to change from time to time.

---

### Post by jlaki on 2010-05-20
> **sanderd17 said:**
> EDIT: sorry, no answer.

I suggested to go to the ip-adres of google but it seems to change from time to time.

Lol, imagine whole internet on one server. That must be super-fast!

---

### Post by StonedRaider on 2010-05-20
Could be that your firewall is blocking it. That's what happened to my. 


Download firestarter form software manager. Open it and go to edit>preferences>network connections and change both connections to eth0

Should work after that and fire wall won't block


Tobin

---

