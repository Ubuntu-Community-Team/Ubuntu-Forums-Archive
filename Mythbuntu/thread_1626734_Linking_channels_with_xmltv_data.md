---
title: "Linking channels with xmltv data"
date: 2010-11-20
forum: Mythbuntu
---

### Post by Billsputters on 2010-11-20
I have a setup which includes an analogue tuner pulling in channels off an old style cable network. So the frequency allocation of the channels is a unique on off situation. I can successfully tune into the 6 channels I wish to use from this source.

The channel listing I can get for the required channels from tv_grab_rt_uk, which I've configured and it quite happily grabs the listings.

Question is: How do I marry the 2 together? So the listing I have, go with the channels I've tuned?

---

### Post by dibuntux on 2010-12-02
I had written a guide back then, but now myth is changed...basically you have to run xmltv setup in source setup in myth backend setup; it will fill channels with data using LCN wich maybe different from the actual channel number assigned in your config... so you have to manually copy the data from the channels that have the schedule to the one you can actually tune. Look at the 2 and you will understand.
Hope it helps

PS: for your reference I include my old guide...

XMLTV grab_it 
New mod. version of grab_it by debian manteiner at [http://tonelli.sns.it/pub/mennucc1/xmltv/](http://tonelli.sns.it/pub/mennucc1/xmltv/)

1) save to disk libxmltv-perl_0.5.54-2_all.deb	xmltv-gui_0.5.54-2_all.deb xmltv_0.5.54-2_all.deb
and 	xmltv-util_0.5.54-2_all.deb
2) synaptic remove xmltv-util xmltv xmltv-gui libxmltv-perl
3) gdebi-gtk install libxmltv-perl from mod ver. saved on disk
4) gdebi-gtk install xmltv-util  from mod ver. saved on disk
5) gdebi-gtk install xmltv-gui from mod ver. saved on disk
6) gdebi-gtk install xmltv from mod ver. saved on disk
4) Run mythbackend configure & create input source named XMLTV set to grabber none (or set old one to none)
5) populate source XMLTV using scan tuned on France (it will grab all italian mux)
6) control channel numbers in Channel Editor -> remove &/or renumber what necessary
7) modify source XMLTV to use xmltv and tv_grab_it: it will run config
-- Point 8) & 9) not necessary in Myth 0.22 - just run configure grabber in Setup>Video Source window and select channels
-- after setting channels, just run mythfilldatabase when asked exiting setup

8) alt-tab to the terminal window and select the appropriate channels that will go into Xmltv.xmltv config file in your .mythtv dir
9) When mythbackend configure asks for run mythfilldatabase leave the window there & run in another terminal mythfilldatabase --manual
10) Reply to all questions (all your channel should be already set with correct IDs, so just Enter to accept default)
11) When the above is finished, you can finally click Yes to mythbackend configure window in point 9).

The guide should now be ok!
6) mythfilldatabase

---

### Post by nickrout on 2010-12-03
> **dibuntux said:**
> I had written a guide back then, but now myth is changed...basically you have to run xmltv setup in source setup in myth backend setup; it will fill channels with data using LCN wich maybe different from the actual channel number assigned in your config... so you have to manually copy the data from the channels that have the schedule to the one you can actually tune. Look at the 2 and you will understand.
Hope it helps

PS: for your reference I include my old guide...

XMLTV grab_it 
New mod. version of grab_it by debian manteiner at [http://tonelli.sns.it/pub/mennucc1/xmltv/](http://tonelli.sns.it/pub/mennucc1/xmltv/)

1) save to disk libxmltv-perl_0.5.54-2_all.deb	xmltv-gui_0.5.54-2_all.deb xmltv_0.5.54-2_all.deb
and 	xmltv-util_0.5.54-2_all.deb
2) synaptic remove xmltv-util xmltv xmltv-gui libxmltv-perl
3) gdebi-gtk install libxmltv-perl from mod ver. saved on disk
4) gdebi-gtk install xmltv-util  from mod ver. saved on disk
5) gdebi-gtk install xmltv-gui from mod ver. saved on disk
6) gdebi-gtk install xmltv from mod ver. saved on disk
4) Run mythbackend configure & create input source named XMLTV set to grabber none (or set old one to none)
5) populate source XMLTV using scan tuned on France (it will grab all italian mux)
6) control channel numbers in Channel Editor -> remove &/or renumber what necessary
7) modify source XMLTV to use xmltv and tv_grab_it: it will run config
-- Point 8) & 9) not necessary in Myth 0.22 - just run configure grabber in Setup>Video Source window and select channels
-- after setting channels, just run mythfilldatabase when asked exiting setup

8) alt-tab to the terminal window and select the appropriate channels that will go into Xmltv.xmltv config file in your .mythtv dir
9) When mythbackend configure asks for run mythfilldatabase leave the window there & run in another terminal mythfilldatabase --manual
10) Reply to all questions (all your channel should be already set with correct IDs, so just Enter to accept default)
11) When the above is finished, you can finally click Yes to mythbackend configure window in point 9).

The guide should now be ok!
6) mythfilldatabase

the easiest way to set up some of this is in mythweb: [http://media/mythweb/settings/tv/channels](http://media/mythweb/settings/tv/channels)

---

