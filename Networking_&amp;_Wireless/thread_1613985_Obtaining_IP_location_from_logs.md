---
title: "Obtaining IP location from logs"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by KonfuseKitty on 2010-11-05
I've signed up with a hosting company and have access to logs of visits to my website.  How can I process these logs to obtain the geographic location of visitors from their IP number?  If there's a way of bash scripting this, it would be ideal, or a dedicated softare that could read in the log file and output the location for each visit.


Any pointers in the right direction will be greatly appreciated.

---

### Post by sully101 on 2010-11-05
this might help [http://manpages.ubuntu.com/manpages/intrepid/man3/Geo::IP.3pm.html]("http://manpages.ubuntu.com/manpages/intrepid/man3/Geo::IP.3pm.html")

---

### Post by TSJason on 2010-11-05
Or if you're looking for something a little more pretty, checkout awstats: [http://awstats.sourceforge.net/](http://awstats.sourceforge.net/)

You can install it from the ubuntu repos.

---

### Post by KonfuseKitty on 2010-11-06
Thanks, but I need something simpler. Is there a program that lets me open a log file and output IP locations? Or not even a log file, just a list of IPs. Awstats doesn't seem to be a desktop application, it needs a server as far as I can tell from its setup instructions, it's too complex for me.


All else failing, I'll just grep my logs down to a list of IPs and manually input them into an online tool, such as the one Maxmind offers. But it would be easier to have a local solution.

---

### Post by lykeion on 2010-11-06
There's a PHP API for geoip. You can write a simple PHP script like this example: [http://20linesorless.com/code/php-geoip-command-line-script/](http://20linesorless.com/code/php-geoip-command-line-script/)

You can parse the logs with PHP also and extract the IPs. There are lots of examples around. Like this: [http://stackoverflow.com/questions/2812150/parsing-raw-apache-logs](http://stackoverflow.com/questions/2812150/parsing-raw-apache-logs)

---

