---
title: "XMLTV uk_rt suddenly not working."
date: 2010-02-03
forum: Mythbuntu
---

### Post by bergqvistjl on 2010-02-03
Hi guys, ive noticed that whenever i try to download tv data from using tv_grab_uk_rt (as of today), it doesnt work. This is my xmltv config: 
```
encoding=utf-8
cachedir=/home/john/.xmltv/cache
title-processing=enabled
postcode=BS16
platform=freeview
channel=4music.channel4.com
channel=bbcfour.bbc.co.uk
channel=news.bbc.co.uk
channel=west.bbc1.bbc.co.uk
channel=parliament.bbc.co.uk
channel=interactive.sport.bbc.co.uk
channel=bbcthree.bbc.co.uk
channel=west.bbc2.bbc.co.uk
channel=bid.tv
channel=cbbc.bbc.co.uk
channel=cbeebies.bbc.co.uk
channel=channel4.com
channel=tsod.plus-1.channel4.com
channel=citv.itv.co.uk
channel=freeview.europe.cnn.com
channel=freeview.communitychannel.org
channel=dave.uktv.co.uk
channel=tsod.plus-1.dave.uktv.co.uk
channel=e4.channel4.com
channel=tsod.plus-1.e4.channel4.com
channel=uk.espn.com
channel=filmfour.channel4.com
channel=channel5.co.uk
channel=fiveusa.channel5.co.uk
channel=fiver.channel5.co.uk
channel=gold.uktv.co.uk
channel=home.uktv.co.uk
channel=idealworld.tv
channel=west.itv1.itv.co.uk
channel=itv2.itv.co.uk
channel=tsod.plus-1.itv2.itv.co.uk
channel=itv3.itv.co.uk
channel=itv4.itv.co.uk
channel=more4.channel4.com
channel=price-drop.tv
channel=quest.discoveryeurope.com
channel=qvcuk.com
channel=sky-news.sky.com
channel=news.sports.sky.com
channel=sky-three.sky.com
channel=dvb.teachers.tv
channel=freeview.1.virginmedia.com
channel=tsod.plus-1.freeview.1.virginmedia.com
channel=uk.viva.tv
channel=freeview.yesterday.uktv.co.uk
```

and this is the results (running the grabber manually) it gives me:
```
XMLTV library version: 0.5.56
tv_grab_uk_rt version: 1.220, 2009/08/09 04:00:57 

Retrieving channels: 100% [==========================================]D 0h00m00s


The Radio Times has usable data available for 299 channels which we
can use to generate TV listings for regular and some timeshifted
channels. The tv_grab_uk_rt software also has support for an additional
52 timeshifted, 5 part-time, and 2 part-time timeshifted channels
based on the Radio Times data.

In total, tv_grab_uk_rt currently supports 358 channels.


     +------------------------------------------------+     
     |  All data is the copyright of the Radio Times  |     
     |    and the use of this data is restricted to   |     
     | personal use only. <http://www.radiotimes.com> |     
     +------------------------------------------------+     


Will download listings for 45 configured channels

Retrieving listings:   0% [                                          ]



Processing listings for '4Music' (4music.channel4.com)
Retrieving listings:   2% [=                                         ]6m36s LeftProcessing listings for 'BBC Four' (bbcfour.bbc.co.uk)
Retrieving listings:   4% [=                                         ]5m22s LeftProcessing listings for 'BBC News Channel' (news.bbc.co.uk)
Retrieving listings:   6% [==                                        ]7m00s LeftNo listings data available for 'BBC One West' (west.bbc1.bbc.co.uk), skipping
No listings data available for 'BBC Parliament' (parliament.bbc.co.uk), skipping
No listings data available for 'BBC Sport Interactive' (interactive.sport.bbc.co.uk), skipping
No listings data available for 'BBC Three' (bbcthree.bbc.co.uk), skipping
No listings data available for 'BBC Two West' (west.bbc2.bbc.co.uk), skipping
No listings data available for 'Bid TV' (bid.tv), skipping
No listings data available for 'CBBC' (cbbc.bbc.co.uk), skipping
No listings data available for 'CBeebies' (cbeebies.bbc.co.uk), skipping
No listings data available for 'Channel 4' (channel4.com), skipping
No listings data available for 'Channel 4 +1' (tsod.plus-1.channel4.com), skipping
No listings data available for 'CITV' (citv.itv.co.uk), skipping
No listings data available for 'CNN' (freeview.europe.cnn.com), skipping
No listings data available for 'Community Channel (Freeview)' (freeview.communitychannel.org), skipping
No listings data available for 'Dave' (dave.uktv.co.uk), skipping
No listings data available for 'Dave ja vu' (tsod.plus-1.dave.uktv.co.uk), skipping
No listings data available for 'E4' (e4.channel4.com), skipping
No listings data available for 'E4 +1' (tsod.plus-1.e4.channel4.com), skipping
No listings data available for 'ESPN' (uk.espn.com), skipping
No listings data available for 'Film4' (filmfour.channel4.com), skipping
No listings data available for 'five' (channel5.co.uk), skipping
No listings data available for 'Five USA' (fiveusa.channel5.co.uk), skipping
No listings data available for 'Fiver' (fiver.channel5.co.uk), skipping
No listings data available for 'G.O.L.D.' (gold.uktv.co.uk), skipping
No listings data available for 'Home' (home.uktv.co.uk), skipping
No listings data available for 'Ideal World' (idealworld.tv), skipping
No listings data available for 'ITV1 West' (west.itv1.itv.co.uk), skipping
No listings data available for 'ITV2' (itv2.itv.co.uk), skipping
No listings data available for 'ITV2 +1' (tsod.plus-1.itv2.itv.co.uk), skipping
No listings data available for 'ITV3' (itv3.itv.co.uk), skipping
No listings data available for 'ITV4' (itv4.itv.co.uk), skipping
No listings data available for 'more4' (more4.channel4.com), skipping
No listings data available for 'Price-drop TV' (price-drop.tv), skipping
No listings data available for 'Quest' (quest.discoveryeurope.com), skipping
No listings data available for 'QVC' (qvcuk.com), skipping
No listings data available for 'Sky News' (sky-news.sky.com), skipping
No listings data available for 'Sky Sports News' (news.sports.sky.com), skipping
No listings data available for 'Sky3' (sky-three.sky.com), skipping
No listings data available for 'Teachers' TV (Freeview)' (dvb.teachers.tv), skipping
No listings data available for 'Virgin 1 (Freeview, Not Wales)' (freeview.1.virginmedia.com), skipping
No listings data available for 'Virgin 1 +1 (Freeview, Not Wales)' (tsod.plus-1.freeview.1.virginmedia.com), skipping
No listings data available for 'VIVA' (uk.viva.tv), skipping
No listings data available for 'Yesterday (Freeview)' (freeview.yesterday.uktv.co.uk), skipping



Finished, but listings for some channels are missing. Check error log.
```
I find it highly unlikely that all apart from 3 channels are invalid. I can view the correct xmltv data on the radio times xmltv site for each channel. the xmltv ids were provided automatically when i set up my channels in mythtv. Any ideas? if the xmltv IDs have all been changed, how can i find them/scan for new ones?

---

