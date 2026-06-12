---
title: "Prep for Mythbuntu and Building DVR - A few noob questions"
date: 2013-07-10
forum: Mythbuntu
---

### Post by vlper on 2013-07-10
I'm going to build my first DVR and plan to use Mythbuntu. Just a few questions:

1. To enjoy all of my cable channels, will I need to first run my cable cord through a cable box before connecting it to a TV Tuner on my desktop?
2. I've read that mythbuntu allows for remote control through a smart phone. Just want to confirm that is possible?
3. Is there any way to deliver / stream cable content from my mythbuntu box to any device with an internet connection (e.g., to my smartphone?). If not, anyone have a solution for this?
4. To deliver cable content from one back-end mythbuntu server, do I just need to install and network multiple front-ends?


Thank you! Looking forward to this project.

---

### Post by alien878 on 2013-07-12
1. The ability to record cable channels depends on where you live and who your cable provider is.  See [http://www.mythtv.org/wiki/Recording_Digital_Cable](http://www.mythtv.org/wiki/Recording_Digital_Cable) for more information.

2.  There is an iphone app, but I was never able to get it to work.  Admittedly, I haven't tried recently as running the backend on anything other than 127.0.0.1 as required caused other problems on my system (long story).

3.  Supposedly, mythweb will stream flash although I haven't tried it ( [http://www.mythtv.org/wiki/Stream_mythtv_recordings_from_mythweb_using_flash_video](http://www.mythtv.org/wiki/Stream_mythtv_recordings_from_mythweb_using_flash_video) ).  What I find more useful is streaming from my iphone to mythtv using airplay ( [http://www.mythtv.org/wiki/AirTunes/AirPlay](http://www.mythtv.org/wiki/AirTunes/AirPlay) )

4. Correct.  However, I would suggest you start out with a combined BE/FE to first see how things work as this is a much easier setup.  Additional FEs can be added later.

---

### Post by uteck on 2013-07-12
1. Most likely yes.  Many cable cos are encrypting all channels so a digital tuner will not be able to decode them.  Even ones that are not (like Wide Open West) you still need a tuner to get premium channels like HBO, or HD channels.

2. I used the remote app once, and it worked okay, but a standard universal remote works better in my opion and the batterys last longer.

3. Mythweb will do it, once you configure it properly.  But it is not an easy to use iterface and it opens up a lot of other options that you may not want people to play with.  It is not designed for the average person to browse and play.

4. That is correct.  Alien878 has the best suggestion since you can easly add front ends to a combined unit, and latter on turn the combined unit into a dedicated back end. I did my setup this way by adding a frontend to the bedroom, then eventually moved the combined unit and the cable box into the basement and put quite low power system in the front room.

---

### Post by cpnbnanamn on 2013-07-19
I've got some questions about this myself, and am also noob to this, and I'm about to do the same thing.  I want to build my own DVR as well, and I've got a few questions of my own.  
[LIST]
[*]I've been looking at the Hauppauge Collossus ( [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=9152&CatId=3493](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=9152&CatId=3493)) as a means of doing the video capture for recording to MythBuntu's PVR service on a dedicated backend.  My thinking is that the capture card will work in place of a TV, (I'm intending to use either cable or likely Directv box with this setup)  Am I thinking correctly, or have I missed 
[*]I also wanted to know if I can have just a dedicated backend server, and use something like a Raspberry Pi (or similar, and I know there is one that doesn't do the whole DRM thing, but for the LIFE of me, cant remember what it is) on each of my TV's to play movies, music, shows, etc.  My thought is use this similar to the Hopper that Dish has now.  One DVR, and can play it in any room in the house. 
[/LIST]

At this point, I could use all the guidance I can get.  I've been reading over the wiki, and it's a little vague in a few areas, so I'm hoping you guys can help fill in the blanks.  Thanks!

-Roger

---

### Post by uteck on 2013-07-20
1. Yes, you can use the card on dedicated back-end that is not attached to a TV, if I understand your question correctly.  The back-end will change channels on the cable or satellite box (once you set up a change channel script), which is connected to the capture card, and the back-end will record it, or pass the live TV feed to a front-end.

2. Yes, you can use a small computer like a Pi for a front end, but Pi is slow and you may have to buy the codex to play some media files, but recorded shows should work fine.  Try to avoid one with an AMD video card as getting Myth to play smoothly is a pain.  Using Nvidia and the VDPAU renderer is soooo much easier to set up.

---

### Post by lwlamont on 2013-08-11
If you have not purchased a tuner card for your MythTV you should look at [http://www.hdhomerun.com/](http://www.hdhomerun.com/). I have an HDHomerun Prime ( and 2 of their original non-cablecard tuners) and could not be happier. In a nutshell, I can record up to 7 channels at the same time while watching a prerecorded favorite on my Mythfrontend. Yes, I'm a registered, card carrying couch potato! Anyway, have a look, I think you will be impressed.

---

### Post by cpnbnanamn on 2013-08-11
> **uteck said:**
> 

1. Yes, you can use the card on dedicated back-end that is not attached to a TV, if I understand your question correctly.  The back-end will change channels on the cable or satellite box (once you set up a change channel script), which is connected to the capture card, and the back-end will record it, or pass the live TV feed to a front-end.

[COLOR=#ff0000]I think you have the gist of my question..  I want to use the MythTV as a server, use the capture card to change the channels, and use a small form-factor device [/COLOR][COLOR=#ff0000]at each of my TV's to stream recorded or live content, probably via wireless.  The server is hardwired to the network, but the Pi's (or something better) are wireless.  I can diagram this if it'll help demonstrate what I'm thinking, and asking.[/COLOR]

2. Yes, you can use a small computer like a Pi for a front end, but Pi is slow and you may have to buy the codex to play some media files, but recorded shows should work fine.  Try to avoid one with an AMD video card as getting Myth to play smoothly is a pain.  Using Nvidia and the VDPAU renderer is soooo much easier to set up.

[COLOR=#ff0000]Got any suggestions here?  While I like the *idea* of the Pi, I'm not happy about the DRM issues, and now with the codecs and poor video performance you're mentioning, that just drives me further away from it.  [/COLOR]

I can use all the help I can get.  Once done, I might be able to help complete the wiki for other noobs...

---

### Post by cpnbnanamn on 2013-08-11
> **lwlamont said:**
> If you have not purchased a tuner card for your MythTV you should look at [http://www.hdhomerun.com/](http://www.hdhomerun.com/). I have an HDHomerun Prime ( and 2 of their original non-cablecard tuners) and could not be happier. In a nutshell, I can record up to 7 channels at the same time while watching a prerecorded favorite on my Mythfrontend. Yes, I'm a registered, card carrying couch potato! Anyway, have a look, I think you will be impressed.

It's a cool idea..  Which version are you using?  How are you set up?
Also, I'd want it to work with MythTV to perform PVR functions..  Is that possible??

---

### Post by lwlamont on 2013-08-12
> **cpnbnanamn said:**
> It's a cool idea..  Which version are you using?  How are you set up?
Also, I'd want it to work with MythTV to perform PVR functions..  Is that possible??

I have a rather involved home network but the HDHomeruns are attached to the cable via a 6 port distribution amplifier. On the network side there is a 10/1000 backbone connecting NAS, HDHomerun's, Mythtv FE/BE combo and a few other things. Everything else in the house runs on 802.11ac/gn WiFi. The older HDHRs pick up all the locally available channels right off the cable without any extra parts. I lease a cable card ($4.99/mo) from Verizon for the HDHR Prime which can pick up any of the channels I'm paying for. You will need a subscription to schedules direct for your program guide data too. I guess there are other places to get the data, but the guys at Schedules Direct have been most reliable for the years I've been with them. 

The Myth box is a little antiquated. It is an Intel Core 2 duo E8400 with an older Intel MOBO with DVI output, 3.75 TB of drives running 12.04 Mythbuntu. Between that and the NAS, it never gets full and we record everything. Other than live sports, we simply don't watch live TV. Myth loves the HDHRs. They are easy to configure. You can maintain them on Linux, but I find it easier doing updates and management with my Windows machine. I'm going to build a Front end with a Raspberry PI for our back room TV too.

---

