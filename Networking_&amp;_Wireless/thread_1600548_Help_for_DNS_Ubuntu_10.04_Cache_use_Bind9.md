---
title: "Help for DNS Ubuntu 10.04 Cache use Bind9"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by yatyao on 2010-10-19
Hi all, i have setup a server Ubuntu to used DNS Cache. All finised, but now, i want to set up Bind Graph to monitor server. 
I can't find the document about how set up bindgraph on Ubuntu 10.04. It's all about the FreeBSD, Cacti,.. So can you help me? plz.. 
Tks so much!:(

---

### Post by yatyao on 2010-10-20
> **yatyao said:**
> Hi all, i have setup a server Ubuntu to used DNS Cache. All finised, but now, i want to set up Bind Graph to monitor server. 
I can't find the document about how set up bindgraph on Ubuntu 10.04. It's all about the FreeBSD, Cacti,.. So can you help me? plz.. 
Tks so much!:(
plz help meeeee...............

---

### Post by P4man on 2010-10-20
Ive never heard of bindgraph, but its in the repositories, so installing ought to be trivial (sudo apt-get install bindgraph). Setting it up and using it shouldnt be (very) different from any other distro, especially not debian.

---

### Post by yatyao on 2010-10-21
> **P4man said:**
> Ive never heard of bindgraph, but its in the repositories, so installing ought to be trivial (sudo apt-get install bindgraph). Setting it up and using it shouldnt be (very) different from any other distro, especially not debian.
tks for answer me ! bindgraph used to see the query to my DNS server (total, in a Day, in a Week, ..)
DNS statistics RRDtool frontend for BIND9 BindGraph is a very simple DNS  statistics RRDtool frontend for BIND9 that produces daily, weekly,  monthly and yearly graphs of the DNS server's activity (queries, errors,  etc.). 

it's example on FreeBSD: 
[http://www.cyberciti.biz/faq/freebsd-bind-named-bindgraph-installtion-configuration/](http://www.cyberciti.biz/faq/freebsd-bind-named-bindgraph-installtion-configuration/)
but i can't found how set up on Ubuntu :(!.. Please help me.. tks !

---

### Post by P4man on 2010-10-21
Install it from the repository. Most of the work is done for you. After installing you should already get some empty stats by going to 

[http://localhost/cgi-bin/bindgraph.cgi](http://localhost/cgi-bin/bindgraph.cgi)

The howto you linked to explains editing named.conf. On ubuntu its located in /etc/bind/named.conf. Edit that file to configure your logging.

From the readme, to start the collector run

```
nice -20 bindgraph.pl --daemon --logfile /var/log/query.log
```

(obviously change the log file to whereever you are logging).

---

### Post by yatyao on 2010-10-26
[IMG]http://i266.photobucket.com/albums/ii263/yatyao/bindgraph.png[/IMG]

plz help me, it's not show pictures? :-s

---

### Post by P4man on 2010-10-26
You did what I wrote in post 3. Now read post 5. I cant be more help than that Im afraid.

---

### Post by yatyao on 2010-10-26
thank you very much.. i'll try it again!..

---

### Post by yatyao on 2010-10-28
oh, yeah!.. i did it! so many thanks all!:D

---

