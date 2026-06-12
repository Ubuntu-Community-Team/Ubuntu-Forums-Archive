---
title: "system setup and planning power management"
date: 2011-01-28
forum: Mythbuntu
---

### Post by simonnev on 2011-01-28
I am trying to setup the system so I have master-backend to centralize all our media, I was sick of buying dvd's and cd's for the kids only to watch them scratch and abuse them. So I had the idea of ripping the music dvd's to disk and putting the physical disk safe. I was running this with the server I have, just storing the files and using xbmc to access them, but I always wanted to try and setup myth due to the pvr functions and database hopefully all in one box solution.

I have now got to the stage of the the myth master-backend being setup and is playing ball and running fine, music, videos and recording.But it is live tv that gives me hassle due to lack of tuners, its has one dual dvb-s2 card in it, so this causes problems when the kids want to watch tv, I set the card up with 4 virtual tuners each hoping that the muxes may cross and the kids and the wife in that fact can watch live tv, so I built another frontend\backend to be used as a slave-backend in the lounge.

I have a couple of problems with this set up at the min, hoping someone could shed some light on it and hopefully have the same setup as what I am trying to achieve.

Have got the slavebackend running but I am having problems with the master not seeing the tuners(not connected)I believe this is caused when you shut it down and the master does not know it can wake it! So I have looked at the wol and that works from the cmd line.
I do not want the slave backend to be running all day as in all the boxes tbh, just at certain times when needed, can anyone shed any light on power management for this type of setup for all the boxes? 

Can you use the remote to close\wake a slavebackend?

Also How many tuners would be needed? to satisfy this system of 4 people in the house? (also have pay tv in the UK but no need to mention that side, that all works)on my tuners.

I also have a older dvbs card lying around and a dvbt-card but I am stuck on the video sources, for the dvb-t card, I take it I have to have a new source set up? But would this then make scheduling shows a bit messy?
Is it possible to have the dvb-t2 card just for live-tv and not for recordings? I'm sure there is a way in priorities etc but I am not sure..

Can you actually edit the numbers for the channels ie BBc1 = 1 bbc2 = 2 etc ?  (using xmltv with rt grabber)

All the rooms have been fitted with a single sat feed and cat5, so I could in theory add a tuners at a later stage to all the frontends and use them as slaves, anyone got this setup? 


thanks for any input simon


myth .24
masterbackend in cupboard 1 * dvb-s2 card can also add a Dvb-t card I have

slave-backend\frontend in lounge 2 * single dvb-s2 cards 

bedroom1 frontend
bedroom2 frontend
bedroom3 frontend
lounge2 frontend

---

### Post by alien878 on 2011-01-28
I'll take a shot (someone may want to add more):
[LIST=1]
[*]You may already know this, but each tuner needs it's own SAT feed.  Alternatively, you can get a multiswitch, but that still requires 4 SAT connections.
[*]I believe there are some scripts floating around that allows the MBE use WOL to control the SBE.  Try searching with those keywords.
[*]How many tuners?  You need one for each show that may be watched/recorded at the same time.  Ex. If you want to watch/record 4 shows at once, you need 4 tuners.  Virtual tuners may reduce this, but only if some of the shows are on the same multiplex.
[*]Mixing DVB-T and DVB-S will require two channel sources to be created.  It works and you can do a lot with prioritization.  However, I expect unless EIT info matches exactly on both, you will occasionally get a double recording.
[*]You can change the channel numbers in mythweb.  Note that if you re-scan, you will get double entries (at least last time I tried, maybe this has been fixed).
[/LIST]

---

