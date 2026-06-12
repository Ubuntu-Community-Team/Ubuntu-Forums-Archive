---
title: "Software to administrate LAN?"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by goseph on 2010-08-06
Hi everybody!

I live in a house with 9 people in it all of whom like connecting to the internet and torrenting. Needless to say, this slows down the internet considerably, I am setting up a dedicated LAN file server (also http server for our new website) that will run Ubuntu server edition and would like to connect it by ethernet to our wireless router.

What I want is some way of dynamically allocating bandwidth on the LAN. For example, if several connections are active then I would like the bandwidth per connection to be capped at some fraction of the number of connections but this cap should grow and shrink. I would also like the website being served to always have 1st priority over any internal connections.

What is the best way for me to do this? Is there a software package that will run on Ubuntu or should I use a whole different OS (clearOS or something?)

Any advice or partial solutions very much appreciated.

---

### Post by pat_bateman on 2010-08-10
Hi,

Basically you want traffic shaping, I recommend you to look into that post
[http://ubuntuforums.org/showthread.php?t=26055]("http://ubuntuforums.org/showthread.php?t=26055")

-Pat

---

