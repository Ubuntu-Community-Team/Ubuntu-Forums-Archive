---
title: "Is MythTV Right for Me?"
date: 2007-12-21
forum: Mythbuntu
---

### Post by Thund3rstruck on 2007-12-21
Hi guys,

Currently I have an HD DVR from DirectTV that meets all my needs for television and I'm currently using XBOX Media Center (XBMC) to stream my DVDs, mp3s, and family photos to the tv. 

For Christmas I purchased an [Optoma HD Projector]("http://www.bestbuy.com/site/olspage.jsp?skuId=8364897&type=product&id=1177717884387&ref=06&loc=01&ci_src=17588969&ci_sku=8364897") for my wife to use in the basement and act as our "movie theatre". I need a way to stream everything to the projector from our linux NAS. We're not going to be using it for TV, just for everything else. 

Is MythTV right for me? 

1) Is it easy to configure to just act as a streaming host and not use a traditional MySql backend? I just need it to connect to my NAS and stream existing content from the NAS to this appliance which I'll connect to the projector. 

2) As for 5.1 sound goes is there a sound card with coax or SPDIF out? My pc just has what looks like headphone jacks

3) All my DVDs are direct rips (complete VIDEO_TS/AUDIO_TS dirs) and XBMC automatically "stacks" the files so they play continuously as would any DVD player. Does MythTV do this as well?

4) Can I edit the MythTV menus so the Television and Recordings stuff is not there?

I noticed that there is a port of XBMC to linux underway but it's not stable and the devs cannot give an estimate as to when it will be ready. 

Thanks In Advance,
--T3

---

### Post by newlinux on 2007-12-21
You can use mythtv for this purpose, you will need to tweak the menus a bit (they are just xml files) and it will properly read your dvd rips. But you may be better off using Elisa. There are plenty of sound cards out their with SPDIF out. I can't comment on particular ones because I use onboard SPDIF for all my machines.

---

### Post by Thund3rstruck on 2007-12-21
Thanks for the response. I'm having a bit of difficulty connecting Mythbuntu to my Windows CIFS shares so I think I may just install a few blown version of ubuntu and load MythTV on top of it.

---

