---
title: "NHL Gamecenter in HD on Ubuntu 14.04.2 LTS:  Fine Tunning"
date: 2015-02-23
forum: Multimedia Software
---

### Post by MikeMecanic on 2015-02-23
How to Ubuntune NHL Gamecenter in HD


Minimum requirements (February 2015):
Cable Modem (no router): Thompson DCM475
High speed Internet: 10Mbs minimum with 150Gig download a month: i**t's around 3 to 5 gig per game**
[B]Opera latest version: 27.0.1689.69 / Ubuntu 14.04.2 LTS (x86_64; Unity)
Google Chrome: Version 40.0.2214.115 (64-bit)[/B]
There is no lag issue on **Ubuntu 14.04.2 LTS** with 4GIG of RAM on a high speed connection (cable). Picture is crystal clear on a HD monitor.

If channel 2 does not open

Channel 2 requires a FLV player:  FOLLOW THE STEP IN GOOGLE CHROME: download it (.exe file) and install the FLV architecture via the terminal with **mono-runtime** (I don't use Wine).  The patch will be applied automatically to the Opera Browser: They both use Chromium Open Project
I'm not sure that the FLV or JW player is an issue no more.  Follow the link and enjoy your beer:

[http://www.hockeyreality.com](http://www.hockeyreality.com)

Because of regional restrictions, I don't know if it works outside East coast of Canada (East of Belleville Ontario).  But it should. Let me know?
If you experience lag problems or loosing the picture signal or sound : Clear browser cache (Clear browsing data/cache) and Ubuntu cache using the following command: 

sync; echo 3 | sudo tee /proc/sys/vm/drop_caches

Otherwise,buy a new computer and/or upgrade your Internet connection to High Speed.

All the best,

Acts like a first class O/S on the Montreal Teksavvy Server

---

