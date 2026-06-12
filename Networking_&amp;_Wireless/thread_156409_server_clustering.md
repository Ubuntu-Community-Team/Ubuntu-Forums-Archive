---
title: "server clustering"
date: 2006-04-07
forum: Networking &amp; Wireless
---

### Post by newbie_jhay on 2006-04-07
hi guys, 

i just want to ask, can 2 desktop pc's running on ubuntu be clustered (like windows servers)? and one more question, how many pc's can an ubuntu server handle when it is just running from a desktop pc with these basic specs:

pentium4 1.6 Gig
256 mb sdr
80 Gigs hdd

well, here's the case... i've been planning to setup an ubuntu server on a small office with about 30 computers. the server would be configured with both samba and apache. but the problem is that the only pc's available (for both ws and server) have the specs i've stated above.... 

because of this, i wanna know if clustering 2 of these pc's to act as server would be possible so it could handle the load. i also want to know how much load can a pc with the said specs handle. if the office would allow it, i'll be able to run a test next week but sadly, my test might only be limited to about 6 pc's - 5 ws and 1 server....

i really hope u guys could give me an idea regarding these things coz it will be my first time to do this stuff.... 

thanks a lot in advance!!!

---

### Post by nanotube on 2006-04-07
unless you are planning on like thousands of simultaneous users, just one server with those specs running samba and a web server will be quite sufficient.
back in the day i ran a ftp/web server supporting 100s of simultaneous users 24/7, on a p2 266mhz with 128 megs of ram. so your specs are quite ok. just dont bog it down by running Xorg on your server, and it will be good to go.

---

### Post by newbie_jhay on 2006-04-07
ei, nanotube, tnx 4 d reply.... it really helps... it just really got me worried coz its my first time doing this and i was wondering if a pc with those specs handle that server load. its just because a friend of mine tried using a pc with the same specs (except her pc uses 1 gig of ddr) and ran a windows 2003 server on it (on a small office with about 20 pc's)and she's having some problems with it.... well, enough of that.... once again, thanks for the help! =)

---

