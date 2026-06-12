---
title: "Xubuntu and Wifi Radar on Startup"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by lexicon59 on 2009-10-09
Hi All-

I've been dabbling w/ Xubuntu 8.04 (Hardy) for a little while on an old (2003) Sharp Mebius laptop (196MB Ram, 20GB HDD, Pentium III CPU). I've been frustrated by the fact that I could only get my wireless card to connect to wireless networks by going into wifi radar and manually hitting the connect button. I can't remember what thread I read it on but I was able to solve the issue by editing the wifi-radar.conf file (found here - /etc/wifi-radar.conf) to the following:

ifup_required = TRUE
auto_profile_order = wifi
speak_up = TRUE
scan_timeout = 5
interface = eth1
commit_required = FALSE

If you look, yours should say FALSE where I have TRUE. This small change allowed my wfi radar to startup with firefox every time. 

I also edited the interfaces configuration file in the network folder and commented out the # sign for the wireless card so that firefox wouldn't start in offline mode.

If anyone knows of issues using these changes, I'd appreciate a heads up. Good luck, and I hope this helps.

---

