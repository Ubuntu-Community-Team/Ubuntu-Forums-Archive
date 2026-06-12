---
title: "curl python urllib bigpond router 3G9WB australia ubuntu linux"
date: 2013-04-04
forum: Networking &amp; Wireless
---

### Post by l5nrr on 2013-04-04
Suddenly on 31/3/2013, I started getting lots of wierd download errors using curl and python urllib, in well used, tried & tested scripts.

After isolating parts of the system, turn out that this combination fails.

py or curl
+
precise or natty or lucid
+
(Bigpond router Netcomm 3G9WB and  Bigpond)

If any of the following are substituted in, it works. 

firefox
Win Vista  
Win 7 
(Hungry Jack WiFi and IPrimus(?))

After lots of searching & scratching, this fixed it:-

"Did you ever try the '-4' switch to force it to use IPv4 only? (Just to
rule out some IPv4/IPv6 weirdness?)
And conversely the '-6'  switch to force it to use IPv6 only?"

For me, -4 made the difference in curl. 
curl -4   --o "${dest}" --url "${URL}" --connect-timeout 30

I haven't found a cure for python urllib yet, I can substitute
subprocess.Popen(['curl'...   so it's a "might do one day" job

if you want to test here are 2 scripts
[https://dl.dropbox.com/u/23269836/downloadTest.py](https://dl.dropbox.com/u/23269836/downloadTest.py)
[https://dl.dropbox.com/u/23269836/downloadTest.sh](https://dl.dropbox.com/u/23269836/downloadTest.sh)

downloadTest.sh carries the same 4 requests twice, w/wo -4

If you have the failing combination above, I'll be interested if you test and report.

The dropbox links will stay for a while, if they're gone, email me [email]garrytreth@gmail.com[/email]

HTH someone

regards Garry

---

