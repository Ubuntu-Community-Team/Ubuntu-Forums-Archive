---
title: "Ceton PCIe"
date: 2012-05-12
forum: Mythbuntu
---

### Post by speed32219 on 2012-05-12
I can cat the video using mplayer from the various tuners and channels.  I can access the WEB Gui from any device on the network.  I have downloaded the latest 12.04 lte Mybuntu version and selected upgrade .25 from the repo's using Mybuntu center.  I have configured the Ceton card, video sources, general with proper ID's (I believe) with no errors on screen except when I selected scan for channels it could not find the card.  After goggling I found that with the Ceton tuner card and m-card you do not need to search for channels.  I have setup the source input as Ceton input type mpeg2ts (I forgot where I did that, can't find it again in setup), but I am getting errors in the log. 

Here is the tail end of the log:

May 12 10:26:41 Myth-Box mythbackend[5856]: E CoreContext tv_rec.cpp:1697 (GetStartChannel) TVRec(6): Problem finding starting channel, setting to default of '3'.
May 12 10:26:41 Myth-Box mythbackend[5856]: E CoreContext channelbase.cpp:940 (InitializeInputs) InitializeInputs(): #012#011#011#011Could not get inputs for the capturecard.#012#011#011#011Perhaps you have forgotten to bind video#012#011#011#011sources to your card's inputs?
May 12 10:26:41 Myth-Box mythbackend[5856]: E CoreContext channelbase.cpp:1229 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device 192.168.1.150-0.1
May 12 10:26:41 Myth-Box mythbackend[5856]: E CoreContext main_helpers.cpp:196 (setupTVs) Problem with capture cardsCard 6failed init
May 12 10:26:41 Myth-Box mythbackend[5856]: E CoreContext tv_rec.cpp:1697 (GetStartChannel) TVRec(7): Problem finding starting channel, setting to default of '3'.
May 12 10:26:41 Myth-Box mythbackend[5856]: E CoreContext channelbase.cpp:940 (InitializeInputs) InitializeInputs(): #012#011#011#011Could not get inputs for the capturecard.#012#011#011#011Perhaps you have forgotten to bind video#012#011#011#011sources to your card's inputs?
May 12 10:26:42 Myth-Box mythbackend[5856]: E CoreContext channelbase.cpp:1229 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device 192.168.1.150-0.2
May 12 10:26:42 Myth-Box mythbackend[5856]: E CoreContext main_helpers.cpp:196 (setupTVs) Problem with capture cardsCard 7failed init
May 12 10:26:42 Myth-Box mythbackend[5856]: W CoreContext scheduler.cpp:206 (VerifyCards) Scheduler: Listings source 'Comcast' is defined, but is not attached to a card input.
May 12 10:26:42 Myth-Box mythbackend[5856]: E CoreContext scheduler.cpp:217 (VerifyCards) Scheduler: No channel sources defined in the database

It looks to be a setting somewhere to do with the IP, but I can not find much information on how to setup the Ceton card within Mythtv.  In the General section of Backend setup I have entered 192.168.1.150 (It was 127.0.0.1) and setup Ceton with that static IP and as stated I can load the Ceton web gui from any network machine. 

Any information would be greatly appreciated.

---

### Post by nickrout on 2012-05-12
> **speed32219 said:**
>  I can not find much information on how to setup the Ceton card within Mythtv. 

Clearly you haven't looked too hard:

[http://www.mythtv.org/wiki/Ceton_InfiniTV_4](http://www.mythtv.org/wiki/Ceton_InfiniTV_4)

---

### Post by speed32219 on 2012-05-12
Thank you nickrout, that was a good find.  Although I have been there 10 times and it was not the fix to my problem. The bottom of that page was Ron's stuff which is already incorporated into .25.  Most everything out there on the net  pertaining to setting up Mythtv has to do with dvb cards or OTA.  Very little on the ceton card when it comes to configuring it within  mythtv.  I have tried every config screen multiple times with still no joy.  Currently I am at this spot in my quest.  It finds the server but then drops off, over and over again.  It is not the seating problem other ppl have had, since I can also use it with Win7 and just plain mplayer streaming works like a champ.


May 12 19:18:12 Myth-Box mythbackend[2503]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.120:6543
May 12 19:18:12 Myth-Box mythbackend[2503]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully
May 12 19:18:42 Myth-Box mythbackend[2503]: E CoreContext mythsocket.cpp:534 (readStringList) MythSocket(9e084d8:28): readStringList: Error, timed out after 30000 ms.
May 12 19:18:42 Myth-Box mythbackend[2503]: E CoreContext mainserver.cpp:6146 (reconnectTimeout) MainServer: Failed to open master server socket, timeout
May 12 19:18:42 Myth-Box mythbackend[2503]: I ProcessRequest mainserver.cpp:1410 (HandleAnnounce) adding: Myth-Box as a slave backend server
May 12 19:18:42 Myth-Box mythbackend[2503]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9e084d8)
May 12 19:18:42 Myth-Box mythbackend[2503]: E ProcessRequest mythsocket.cpp:358 (writeStringList) MythSocket(9e084d8:-1): writeStringList: Error, socket went unconnected.#012#011#011#011We wrote 0 of 10 bytes with 1 errors#012#011#011#011starts with: 2       OK
May 12 19:18:43 Myth-Box mythbackend[2503]: N CoreContext mainserver.cpp:6090 (reconnectTimeout) Connecting to master server: 192.168.1.120:6543
May 12 19:18:43 Myth-Box mythbackend[2503]: N CoreContext mainserver.cpp:6108 (reconnectTimeout) Connected successfully

Also, when I do shutdown the backend and try a different conf.  upon exiting I get errors about the 13 and 14th card is set for wrong channels.  It just keeps incrementing by one, even though the ceton card is configured for card 0 tuner 0.

Any help would be appreciated.

---

### Post by speed32219 on 2012-05-27
Didin't want to leave the thread open.  I had finally got it working. I am going to write up a quick guide from start to finish on getting a Ceton PCIe 4 tuner working.  There is just so much info on the web from the inception of this product, that it makes it difficult to get something working with the latest releases.

Anyway, I now have a almost fully functional mytbuntu back-end.  Only thing left is the volume control on the remote I need to take a look at, otherwise it's just about perfect.

---

### Post by nickrout on 2012-05-27
> **speed32219 said:**
> Didin't want to leave the thread open.  I had finally got it working. I am going to write up a quick guide from start to finish on getting a Ceton PCIe 4 tuner working.  There is just so much info on the web from the inception of this product, that it makes it difficult to get something working with the latest releases.

Anyway, I now have a almost fully functional mytbuntu back-end.  Only thing left is the volume control on the remote I need to take a look at, otherwise it's just about perfect.

Please please do not write this up "somewhere on the web" or it will suffer the same fate as the other material you read. Edit the mythtv wiki page, make usre you identify the date of your material and the versions of everything used.

Volume on the remote - what's the problem there and how is your audio getting from your frontend to the speakers? (HDMI, analogue, spdif etc)

---

### Post by speed32219 on 2012-05-27
Good idea nickrout, I'll take a look at the wiki and make changes there.  It was such a pain trying to find something, but everything out there is outdated and much of it was causing me the problems with the newer release of Mythbuntu 12.04.

As far as the audio, the audio test works fine within Mythbuntu 12.04 setup.  Both from the IR/RF MCE remotes and the android app..
I can adjust the audible volume levels, which now is my problem, I can adjust the volume and see the visual graphic bar change but with no affect on the actual volume.  Go back into test mode during setup everything works. I should have created a new post.

---

### Post by nickrout on 2012-05-27
Are you using digital or analogue audio out?

---

### Post by speed32219 on 2012-05-28
Digital (HDMI) using alsa HW device 3 and also tried alsa dmix HW 3 and no joy there either using the HDMI cable.  

aplay -l
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[COLOR="Black"]**card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]**[/COLOR]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I guess I could take the analogue output with a set of rca cables and try that next.  The pass-through works fine, but I need to add'l use the TV remote for volume control.  I'll try that test next.

---

### Post by speed32219 on 2012-05-28
Digital (HDMI) using alsa HW device 3 and also tried alsa dmix HW 3 and no joy there either using the HDMI cable.  

aplay -l
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[COLOR="Black"]**card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]**[/COLOR]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I guess I could take the analogue output with a set of rca cables and try that next.  The pass-through works fine, but I need to use the TV remote for volume control.  I'll try that next.

---

### Post by nickrout on 2012-05-28
If you want to control the volume of a digital out thru mythtv you need to set the mixer device to software. Simple, but it does mean your digital ac3 or dts stream is decoded and re-encoded in software, which may not be to your liking.

---

### Post by speed32219 on 2012-05-28
Thank you nickrout!  That did it, not to concerned on quality since this will be used for front-ends on a few flat screen TV's (bedroom/guestrooms).  My main server is attached HDMI to a AVR and pass-through on that works great.  I am now complete, now to read the Docs on trans-coding saved videos to H.264/mkv formats as well as setting-up/saving all my folders to the NAS devices.

The system is working great, I am very pleased to include video quality of HDTV live-tv feeds.

---

### Post by nickrout on 2012-05-28
Glad you got the volume working.

Transcoding is a tough proposition, particularly if you want to cut ads. I would buy a bigger hard drive, they are cheap after all.

---

### Post by wv5k on 2012-06-12
> **speed32219 said:**
> Didin't want to leave the thread open.  I had finally got it working. I am going to write up a quick guide from start to finish on getting a Ceton PCIe 4 tuner working.  There is just so much info on the web from the inception of this product, that it makes it difficult to get something working with the latest releases.

Anyway, I now have a almost fully functional mytbuntu back-end.  Only thing left is the volume control on the remote I need to take a look at, otherwise it's just about perfect.

I see you've not done anything with the wiki yet. I wish you would, as I am about to embark on this voyage myself. Thanks In Advance if you actually follow through on this...

---

### Post by Yeahmeat on 2013-01-29
Bumping this thread.  I have the same issue as the OP and can't seem to get Myth to grab channels.  I am able to pull in channels from my Ceton Infinitv via Mplayer but Myth just refuses to fetch data.  If the OP can post how you resolved this or if anyone else has any suggestions please let me know!

Thanks!

---

### Post by Akriss on 2013-01-29
The Ceton card does not "fetch" channel data. 

You need to have a Schedules Direct account [([COLOR="Red"]SD site here[/COLOR])]("http://www.schedulesdirect.org") or some other way of obtaining scheduling data.

Hope that helps.

---

### Post by Yeahmeat on 2013-01-30
I've did set up a trial SchedulesDirect account last night but that didn't resolve the issue either.

---

