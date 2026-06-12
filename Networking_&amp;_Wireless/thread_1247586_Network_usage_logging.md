---
title: "Network usage logging"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by buntunoob21 on 2009-08-23
Hi Everyone,

my first post, been using ubuntu full time for about two months now. I am wanting to make a logging program that will log my network usage as i believe my service provider is over charging me. I really like the resource graphs that appear on the system monitor for Jaunty. Can anyone please guide me as to how i can get started making a script that will monitor the network usage and write to a file the usage per day. perhaps even graphing the usage. I am not that keen on implementing anything heavy like cactus, as the pc is only a everday laptop.


Thanks

---

### Post by Jimmy9pints on 2009-08-23
I can't be of much help here, but would perhaps a python script used with [http://oss.oetiker.ch/rrdtool/index.en.html]("rrdtool") would be a quick solution.

---

### Post by kreggz on 2009-08-23
Hey, if you Router supports SNMP you can use "Cacti" to graph you traffic. It will show how much you uploaded and downloaded over a specified period of time.

Google Ubuntu Cacti and you should find some good guides out there

---

### Post by buntunoob21 on 2009-08-23
Hi, Thanks for the reply,  my understanding is that cacti requires a apache and mysql server running, i really dont have to have those running all the time on my laptop. also the internet is through mobile broadband. On a search i found something called Conky, anyone an expert in Conky?

---

### Post by cariboo on 2009-08-23
Have a look at bandwidthd, it is in the repositories. It can track network usage of all of your computers.

---

### Post by SolarOnline on 2009-08-24
[ipMonitor]("http://tinyurl.com/q9crts") can track you network usage. So will be able to tell you how much traffic is going between your router and your box.

---

