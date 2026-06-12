---
title: "Unable to scan DVB-S through diseqc switch"
date: 2007-12-13
forum: Mythbuntu
---

### Post by mymythtv on 2007-12-13
Hi

Having installed MythBuntu on a machine with a Hauppauge NOVA DVB-T 500 (dual) and a Hauppauge NOVA-HD-S2, I find myself having trouble tuning/scanning the DVB-S through a 4 port diseqc switch..
I have tried to tune outside Mythtv, and all ports/lnb's are woring. I can get picture withc kaffeine or dvbstream ( mplayer )

When I scan through Mythtv I only get the first switch position ?!
Setup is Mythbuntu 0710 with latest weekly build.
Config:
Capturecard: DVB-S with diseqc set to "switch+4lnb"
Videosource: One for each lnb ( astra1, astra2, hotbird and eutelsat )
Input connection: One for each lnb, and each with DiseqcSwitch set to correct port ..

Still - I'm not able to scan anything but first lnb, making me believe there is a bug, or setup is not so intuitive as it looks ?!?!?

Have to mention; living i europe where diseqc is quite common :)

Solved:
I got the latest driver from [http://dev.kewl.org/](http://dev.kewl.org/) for the Hauppauge Nova-HD-S2 ( Actually a HVR4000 lite ) which added DVB-S2 support and also fixed my diseqc problem. Seems odd as Kaffeine was working. Havent got time to test DVB-S2 yet, but hope to get some time in the new year.

---

