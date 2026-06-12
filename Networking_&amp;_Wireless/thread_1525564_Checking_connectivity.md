---
title: "Checking connectivity"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by mattlezeay on 2010-07-06
Ok, so I am not sure where to post this so I figured I would try here and see what my mileage is. I am trying to find a simple way to test if a webserver is up and if it fails to respond, it emails me. I have a server that has been going down and I don't know about it until one of my clients call me. Thats not working. I have a server that is always on in my house running ubuntu server and I want have it run something every so often and check if a list of domains are responding and then let me know if they don't. I know there are paid services and there are web services out there but I would prefer it being local. Any ideas? Thanks!

---

### Post by Brandon Williams on 2010-07-07
Checking whether the domain is responsive: "HEAD -t 5 <url>". This command line will make a HEAD request for the specified url, timing out the request after 5 seconds. If the HEAD command is not present on your system, install libwww-perl.

Doing this periodically: "crontab -e". View "man 5 crontab" to learn about how to formulate a crontab entry to schedule the running of your tests.

Sending e-mail to yourself on failure: "sendmail <e-mail addr>". View "man sendmail" to learn about using sendmail to send an e-mail. With the simple command line I indicated, it will read from stdin and use that input as the e-mail text. You can include headers, such as "Subject: HEAD failed for <url>".

---

### Post by mattlezeay on 2010-07-07
Thanks, exactly what I needed, now to go and have some fun!

---

