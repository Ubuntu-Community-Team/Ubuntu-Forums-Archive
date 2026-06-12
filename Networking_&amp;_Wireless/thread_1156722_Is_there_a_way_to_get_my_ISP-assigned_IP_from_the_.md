---
title: "Is there a way to get my ISP-assigned IP from the commandline?"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by dwasifar on 2009-05-12
My IP address from my ISP is dynamic, and changes periodically, usually for no visible reason and on no set schedule.  I would like to set up my server to run a script that will notify me of this change by emailing me the new IP.  So the script needs to do two things:  1) obtain the current IP address and  2) email me if it's different than last time.  I can handle part 2, but I don't know how to get the upstream address for part 1.  All I can figure out how to get is the local network address, i.e. 192.168.x.x.

(Please don't suggest I get a static IP from my ISP; this is not an option.)

---

### Post by cariboo on 2009-05-12
There are several free services that take all the work out of dealing with dynamic ip addresses. Noip and dyndns are two that come to mind. Check out [dyndns]("http://www.dyndns.com/") here, and [no-ip]("http://www.no-ip.com/") here.

---

### Post by Keithhed on 2009-05-12
whatismyip.com   sorry its not command line

---

### Post by netJackDaw on 2009-05-12
whatismyip.com is a not so bad idea after all. Although you shouldn't hit their default start page with scripts. Instead follow their guidelines for automation. Check this out: [http://forum.whatismyip.com/f14/our-automation-rules-t241/](http://forum.whatismyip.com/f14/our-automation-rules-t241/) and check out other parts of their forums as well... You might find a solution there.

---

### Post by mobilediesel on 2009-05-12
Try this:```
wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'
```
or even:```
wget www.whatismyip.com/automation/n09230945.asp -O - -q
```

---

### Post by lisati on 2009-05-12
[www.whatismyisp.com](www.whatismyisp.com) is quite neat: it often gets my location correct within a few kilometres. I checked the IP for a few incoming emails from people I know who live in the Auckland area: what was spooky is that the map zoomed in on Mount Eden prison!

---

### Post by dwasifar on 2009-05-12
Outstanding!  Just what I needed.  Thanks all :)

---

