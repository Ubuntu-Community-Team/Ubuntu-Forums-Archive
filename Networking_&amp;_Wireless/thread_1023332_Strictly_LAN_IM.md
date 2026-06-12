---
title: "Strictly LAN IM ?"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by randiroo76073 on 2008-12-27
I'd like to set up a local IM on my network(3 computers), does anyone have any suggestions on what to use & how to set it up.
Thanks for any info you can give.

---

### Post by PhrankDaChickenGeek on 2008-12-27
> **randiroo76073 said:**
> I'd like to set up a local IM on my network(3 computers), does anyone have any suggestions on what to use & how to set it up.
Thanks for any info you can give.


One idea is to setup a webserver on one of the computers (apache, php) and install the phpfreechat script - Then use a web browser on each computer to chat

$ sudo apt-get install apache2 php5

[http://www.phpfreechat.net/](http://www.phpfreechat.net/)

---

### Post by randiroo76073 on 2008-12-28
Thanks Phrank, that may be the way to go.

---

### Post by AnRa on 2008-12-28
Use the Bonjour protocol in Pidgin. :)

---

### Post by PhrankDaChickenGeek on 2008-12-28
> **AnRa said:**
> Use the Bonjour protocol in Pidgin. :)

Sweetness - Yes, this is the way to go!

And if you have Windows machines:
[http://www.pidgin.im/](http://www.pidgin.im/)
[http://www.apple.com/downloads/macosx/apple/windows/bonjourforwindows.html](http://www.apple.com/downloads/macosx/apple/windows/bonjourforwindows.html)

Tutorial - [http://ubuntu.online02.com/node/19](http://ubuntu.online02.com/node/19)

---

### Post by jerome1232 on 2008-12-28
> **AnRa said:**
> Use the Bonjour protocol in Pidgin. :)

That's what I was going to suggest :)

---

### Post by kevdog on 2008-12-28
Any other info about the Bonjour Protocol?

---

### Post by randiroo76073 on 2008-12-28
Thanks all, I'm gonna try Pidgin as y'all suggested, been with the "U" for a while but 1st time I've gotten into home networking LOL! 1st time I've had to.

---

### Post by Dr Small on 2008-12-28
> **kevdog said:**
> Any other info about the Bonjour Protocol?
Yeah, what is the Bonjour Protocol? I was going to suggest a jabber server.

---

### Post by cb951303 on 2008-12-28
I was looking for the same thing, I tried bonjour right away. it works really really great!

For LAN chatters: If you want to start pidgin minimized, install pidgin-extprefs plugin package from repos. Activate the plugin and check "hide buddy list"

---

### Post by PhrankDaChickenGeek on 2008-12-28
> **Dr Small said:**
> Yeah, what is the Bonjour Protocol? I was going to suggest a jabber server.

Already posted this link, but didn't label it - Bonjour for Windows downlaod

[http://www.apple.com/downloads/macosx/apple/windows/bonjourforwindows.html](http://www.apple.com/downloads/macosx/apple/windows/bonjourforwindows.html)

It's by Apple - [http://www.apple.com/macosx/technology/bonjour.html](http://www.apple.com/macosx/technology/bonjour.html)

---

### Post by kevdog on 2008-12-28
that page is for bonjour for windows -- which is helpful.  what about for linux?

---

### Post by PhrankDaChickenGeek on 2008-12-28
> **kevdog said:**
> that page is for bonjour for windows -- which is helpful.  what about for linux?

sorry - Linux uses Avahi - same thing basically: 
[http://en.wikipedia.org/wiki/Avahi_(software)](http://en.wikipedia.org/wiki/Avahi_(software))

It should already be installed and running. It can be enabled/disabled in "System -> Administration -> Services"

---

### Post by jerome1232 on 2008-12-28
?? Pidgin has the bonjour plugin installed out of the box in Ubuntu

---

### Post by randiroo76073 on 2008-12-28
Once again thanks LOL! My wife is drivin me crazy with it tho :D

---

