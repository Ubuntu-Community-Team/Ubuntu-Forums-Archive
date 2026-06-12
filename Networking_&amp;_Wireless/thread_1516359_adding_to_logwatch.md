---
title: "adding to logwatch?"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by jeff.sadowski on 2010-06-23
I would like some way to tell me when any program opens a network connection. What started it (cron, bash shell, other program) Is there a way I can do this?
Is there an existing log or a way to turn on logging. Besides each individual programs logs which might not exist if it is a malicious program.

I have some unexplained network events that my router says it blocked. As far as I know I have a clean machine. Its a pretty fresh install with minimal programs installed and I have it shored up where I think I need it.

It is an apache web server so I expect traffic from outside to port 80. It handles email with sendmail so I expect traffic from our filter to it on port 25 it sends email form some php pages so I expect outgoing mail on 25. It handles dns via bind so I expect incoming and outgoing on 53. I ssh to it and run shelter scripts to help block bad ssh attempts.
I get logwatch emails everyday from it and everything looks normal. It shows when I login via ssh and sudo as root to do maintenance. It shows normal web traffic and the like. I would like it to show when apt-get connects and does updates. I would also like it to show when emails are sent and from what programs. I would also like it to show when anything else opens a port for what ever reason. So that I can remove any offending programs or users.


===Update=========

I remember you can do logging with iptables although im not so sure it can tell what program was trying to make a connection. but I remember something about it being able to log I will go search for that.

---

