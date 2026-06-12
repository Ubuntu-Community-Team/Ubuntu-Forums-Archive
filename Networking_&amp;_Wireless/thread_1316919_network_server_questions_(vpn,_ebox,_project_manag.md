---
title: "network server questions (vpn, ebox, project management)"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by silvernewt on 2009-11-06
i'm not sure if this belongs here or in the server platform forum..? (mods please move at your discretion)

i've setup ebox with ubuntu 8.10 server on an old desktop machine to create a home samba & print server to share my canon ip2000 printer.

firstly, a minor(ish) issue:

ebox didn't support my printer properly so i bypassed that and configured it in cups using the web interface on port 631.

i checked openprinting.org & selected the closest drive i could. when connected to the server printing from the windows machines at home seems to work ok (not tested it fully yet with more complex printouts like photos or large images) but when printing from my ubuntu 9.10 machine it's evident that the wrong drivers are being used (text is stretched horizontally, only one page prints & only a quarter of that is filled up). the windows machines warned me the wrong driver was in use & required me to download the canon driver. i never had issues with connecting the printer directly to my machine running 8.10, 9.04 or 9.10 desktop editions, thus i presume that system-config-printer had guessed & downloaded the correct compatible driver.

so, is there a way of downloading an updated driver list through ssh to my ebox server & selecting a better driver? even more important is the ability to rollback the changes in case it breaks for the other machines in the household...?

i'm going to be looking at getting an hp laserjet printer anyway as i believe they've got better linux printing support?


second question:

i'll also be opening up the server for web based access so i can share work with my business partner. what are the best VPN systems out there (must be able to run with dyndns)? i've looked at openVPN, does anyone have any advice / experience with working with VPNs & how to secure them nicely? it will have to play nicely with ebox (ie no port conflicts).


third question:

can anyone recommend any good project & customer management software which will also run on the same server? i need to be able to add customers, track invoices, add services, auto generate invoices, track due payments, etc. i've not got enough time to build one from scratch!

many thanks,

Neal.

---

