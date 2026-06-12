---
title: "Can't ping google.com but can ping www.google.com"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by AngelsJinx on 2010-01-21
As the title says, I'm capable of accessing [www.google.com]("http://www.google.com") from firefox, but I can't go to google.com
This applys to all websites, and normally wouldnt be such a big problem EXCEPT, I can't even ping google without the www. in front.. and so the repositories can't connect (mine attempt to connect to nz.ubuntu, which doesnt work because theres no www infront of nz)

I'm running a fresh install of Ubuntu 9.10 desktop edition on a dell studio laptop. The problem is there whether I'm using wired or wireless networking, so its not just related to one or the other.
Any help would be greatly appreciated.

---

### Post by x33a on 2010-01-21
Try changing the dns servers for starters.

try google dns:

[http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

or opendns:

[http://www.opendns.com/](http://www.opendns.com/)

---

### Post by AngelsJinx on 2010-01-22
Well.. I changed the dns settings on my router. And that seems to have worked.
Though I'm now having trouble installing the 64 bit version, but thats another problem altogether. Hangs after selecting the install option just after booting to a cd, infact it freezes selecting any option.
Ah well, I'll hit google, though any responses would be greatly appreciated

---

### Post by x33a on 2010-01-22
Try downloading a new iso, and burn it at slow speed, then check the md5sum and match it with the original. also try the cd check built into the live cd.

if it doesn't work out, create a new thread for that issue, as the topics are unrelated.

note: creating a new thread for separate issues helps others searching for similar problems.

---

