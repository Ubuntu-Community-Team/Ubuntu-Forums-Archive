---
title: "Package download rate drops off"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by marshmallow1304 on 2009-07-21
When I download a package through Synaptic, it starts off with a download rate of about 40-65 kB/s (normal range for my DSL), but after a few seconds it drops down and starts alternating between very low speeds (about 450 b/s) and 'unknown'.  If I click 'Cancel' then restart the download, the download will again start with normal speeds then die.  Sometimes changing the repo mirror helps, sometimes it doesn't.
  
I'm fairly sure this isn't a router issue because the same thing happens when I'm plugged straight into my DSL modem/router.  I think my connection is fine because an online speed test done while this is happening shows normal speeds.



Ideas?


Edit: I just checked on Synaptic, and it appears that the download that I had left sitting at slow/unknown speed picked back up again.  I still don't know why the download speed doesn't stay constant though.

---

### Post by recentcoin on 2009-07-29
I've been seeing EXTREMELY slow download speeds when I go to update my servers.  I suspect that one of the mirrors is misbehaving or under attack.  2+ hours for a 20MB file is a bit ridiculous.  It's been happening to me for a few days now.  I'm on a really fat pipe and nothing else is having speed issues so I'm not sure why this is a problem, but I'm glad that I'm not the only one seeing it.

---

### Post by superprash2003 on 2009-07-29
go to system->admin->software sources and try another server

---

### Post by House101 on 2009-10-03
Mine is also extremely slow. normally the download rate is 200-300 kb/s and and now it's 30 b/s-55 kb/s. My internet/e-mail is fine, but any package downloads within the system is really slow.

---

### Post by CHFFriday on 2009-10-03
Same problem here. Just started this week.

---

### Post by kaleidoskop on 2009-11-15
Same problem here. The downloads start fast at 200kb/sec and after 5 seconds or so it drops down very fast to 0.00. This behavior occurs not only with synapic but also with firefox, opera and so on. In Ubuntu 8.04 everything was working fine, with introduction of 9.04 synaptic got the above mentioned problem and kept it until now, but Firefox still worked fine. Now with 9.10 Firefox waits a long time and suddenly it loads the pages fast, but downloads drop off. Same with Opera. I tried with activated and deactivated IPv6, DHCP and static mode, no success. When I boot windows on the same machine, Internet is fast as it should be, with every program.

Can anybody help? Ubuntu is not funny without fast internet!

**Tech information:**
Mainboard: ASUS K8V SE DELUXE
Ethernet: Onboard Marvel Yukon
CPU: AMD Athlon 64 3000+
Router: Simens Gigaset SE361 (WLAN)
PC is connected to router over ethernet cable 
Modem: Motorola (Cable)
Driver: skge

---

### Post by kaleidoskop on 2009-11-15
Update: I connected my computer now direct to the modem and download speed is now high with every application. Are there any known issues about router settings and Ubuntu internet speed?

---

### Post by kaleidoskop on 2009-11-22
Isn't there anyone who can help? There seem to be other Users having this problem, but no solution is to find in the Internet. In the meantime, I reset the router, but without success. 

I like Ubuntu much more than Windows, but I'm now forced to use Win cause the connection works fine there. Fixing this problem would be great!

I'm thankful for every advice!

---

### Post by Arrizqi on 2010-05-14
Maybe this could help you

[http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html](http://www.debianadmin.com/simple-package-management-with-synaptic-package-manager-in-ubuntu.html)

---

### Post by lajfi on 2010-08-18
is there anyone who found out why it is happening?
i am having the same issue on Ubuntu 10.04

might it have something to do with the fact i have added some repos in the sources.list?

---

### Post by lucius.antonius on 2011-05-27
I'm experiencing something similar. Large file downloads usually stop after a couple of megabytes. Same for FTP file transfers. I noticed that I have the same router, Siemens Gigaset SE361 (WLAN), so I'm suspecting that it may be the culprit. Siemens doesn't produce routers anymore these days, so the chance of getting an updated firmware is zero :(

The issue may be connected to some IPv6 related changes, possibly related to [this bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/417757") ...?

---

