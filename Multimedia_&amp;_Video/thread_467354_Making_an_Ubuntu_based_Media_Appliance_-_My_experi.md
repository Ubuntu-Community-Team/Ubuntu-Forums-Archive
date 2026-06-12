---
title: "Making an Ubuntu based Media Appliance - My experience"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by dannystaple on 2007-06-07
I spent a bit of time last week converting my desktop (already running Feisty, and still used for other tasks) to a living room media centre, with MythTV, DVD playback and a DVB-T card. 

I thought it might be valuable to share my experiences with the community.
Firstly - I had to obviously start lugging the gear into the living room, after managing to convince my wife. The promise of moving from wireless networks to wired (which she perceives as a health choice) was really the clincher there. Plus the idea of having a PVR setup worked for her too.

Next was to actually choose the hardware. This was a bit of a pain, and I first had a look around on the net, and thought I would go for a generic, cheap and cheerful freecom DVB-T USB Stick, but alas - that was not to be. I wanted to get it sorted there and then, so I visited a PC world we happen to have at the end of the road (I would normally wait for the Tottenham Court Road market or buy it online, but I had a holiday and was eager). I had checked their selection of DVB-T cards online, and they did stock this one. When I got there, there were only 2 Freecom sticks left, one of them "previously owned and missing adaptor" and the other with the package partially opened. I went for the second one, got it home, began to rig it up, and hen noticed that this one had its adaptor missing too - which makes it useless. The adaptor allows the tiny socket on the stick to be interfaced with a standard TV RF coax.

So I returned it with no problems, and bought instead the Hauppage HVR-950. This was a bad plan. Although Hauppage cards are supported under Linux, the HVR ones are not. Only half the chipset was supported - the EM2800, while the other, the drx3975d was not. This meant that it could be used to view analog TV, but not DVB-T - which was not really that useful for my proposed Myth setup. I faffed around for a day trying though before receiving that news. This was to the extent of downloading firmware, and compiling up a new v4L-experimental, then finding there was no /dev/dvb device. I mailed the EM2800 list, and subscribed, so maybe I will get to know when the drx3975d chipset gets some support, but as I understand it, the manufacturer cannot really be bothered. 

Okay - returned this one too. I made it clear that it didn't work in Linux, and was not fit for the purpose I bought it for. No problems - PC world even made a note on their system to that effect. I exchanged it for a partial refund, and the cheaper Hauppage USB2 Nova-T stick. This one is nice and easy - the Kernel already supported it - although it seems to overheat and need to be unplugged occasionally. The big disadvantage is that it comes with no remote.

I got on with setting up and configuring mythtv. I followed the guide at [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) after having installed much of the parts anyway - and managed to get it all up and running, with TV, live pausing, and rewind. It had the EIT information (TV Guide) and seemed to be okay. It sometimes took a while to get a lock though, especially on the non-BBC channels (which use a different modulation system and FEC setting).

However, the one problem I am still getting is the DVR synchronisation - when making recordings, it seems that BBC programs start about 2 minutes before the recordings started, and the ITV channels seem to record 5 or so minutes later. Annoying - I get the first few minutes clipped off from BBC programs (and UK TV) and the last few from other channels. I tried to tweak with the record before and after settings - which is okay, but produce conflicts if you try to record two consecutive items on a service.

I also used the Ubuntu guide to get DVD stuff set up - which was actually pretty simple. I have a wireless keyboard, with some media keys, but have not been able to find a remote on the high street. I will probably have to buy one online. This is even after trawling Tottenham Court Road (although I did not yet try the market). I realise though it might be cheaper to try and find another supported Hauppage DVB-T model with a remote and receiver, which would then give me two tuners too - hmm - record and watch? Hope my bus and hard drive are good for that..

While this was not entirely smooth, I will admit I like the result. Cannot get the mythweather app to run properly yet, but the rest looks good.

---

### Post by Kenji Mapes on 2007-06-07
Thanks for sharing your insights and experience with us.  Since I am a Yankee (;))  I had no idea what DVB was.  We have NTSC/ATSC here in the States.  I love Hauppage stuff, but as far as compatibility I have had better luck with Nvidia and ATI cards.

I have been using Windows MCE for a while, and am looking into Myth TV for my Ubuntu box.  How has your Myth TV experience been thus far?

---

### Post by dannystaple on 2007-06-13
Hi Kenji,
DVB is the Digital Video Broadcast, and is probably the equivalent of ATSC. It is broadly based on MPEG2 unless it is HD which then uses MPEG4. I have not heard of NVidia and ATI selling DVB-T tuner cards, but I would prefer them over the Hauppage stuff if I found them.

MythTV has been okay, but the Hauppage Nova-T stick still overheats and needs to be unplugged to cool down - not really great for a PVR set up to record overnight or while I am at work. 

The biggest problem with Myth itself is that I still have not got a remote for it, so I am having to learn shortcut keys for those things my media keyboard does not have. It has the buttons for Media, Play/pause, mute, volume, Favourites (which I assign to the guide), E-mail and WWW. Other than that, I quite like it, especially that I can sort out recordings from a web back end, and do not need to front end except to play back or watch TV. This means my computer can still be used as a general desktop when I am not actually watching TV.

I did tinker with getting my PDA set up as a remote via a web interface and wi-fi, but I will admit I got lazy and didn't finish the job when finding that the previous code someone had written to do it had been left unmaintained for a couple of years. I certainly know it is possible.

---

### Post by newlinux on 2007-06-13
just as an FYI, mythweather is currently broken due to changes in the web site it gets its data from.

And for those who want to install mythtv, I recommend the following tutorial:

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

Which is made by the ubuntu mythtv package maintainers. Also, keep an eye on [http://mythbuntu.org/](http://mythbuntu.org/)

---

