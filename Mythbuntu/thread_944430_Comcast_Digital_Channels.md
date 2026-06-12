---
title: "Comcast Digital Channels"
date: 2008-10-11
forum: Mythbuntu
---

### Post by Just4Fun20 on 2008-10-11
I've tried to get this properly configured, but haven't succeeded yet.  

I've been using MythBuntu for over a year, through a couple versions/revisions, and have been very happy with it.  I use a Hauppauge WinTV (150) tuner card for analog channels.  

I picked up a cheap digital (it's a hybrid and will apparently also tune analog)  tuner card from woot.  It's a Pinnacle PCTV HD 800i card.  For these tests I removed the WinTV card.  

I have virtually no OTA available.  I have Comcast cable.  I live north of Boston in NH.  I've never used their digital services and have no set top boxes, but I don't think that matters, or is the issue.  

I installed the card's drivers ([http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)) using the mercurial stuff.  I grabbed the .gz file, then 'tar -zxvf', then 'make' and finally 'sudo make install' and reboot.

I installed the firmware ([http://www.steventoth.net/linux/xc5000/](http://www.steventoth.net/linux/xc5000/)) using the extract.sh to pull and place the appropriate files.  

The backend setup sees the card and I can set it up as DVB (sorry, forgot the details here).  

I can't get the channel scan to work.  Well, let me rephrase that.  I can't find channels.  The MythBuntu scans do find many encrypted channels and perhaps one or two that are not.  This leads me to believe I'm still not looking in the right  place.  

MythTV has a long writeup in their wiki on finding channels ([http://www.mythtv.org/wiki/index.php/Adding_QAM_Channels_For_HDTV_Tuner_Cards](http://www.mythtv.org/wiki/index.php/Adding_QAM_Channels_For_HDTV_Tuner_Cards))  I installed these utilities and did the scans.  I think it found channels, but not without problems.  

That wiki page specifically discusses some "weird" output which looks like this (This is the first portion of my output.  The full file is 332 lines long.): 
```
[000a]:243012500:QAM_256:2112:2113:10
[000c]:243012500:QAM_256:1984:1986:12
[000b]:243012500:QAM_256:2048:2049:11
[0001]:351012500:QAM_256:1987:1984:1
[0002]:351012500:QAM_256:2048:2050:2
[0001]:369012500:QAM_256:0:1985:1
[0002]:369012500:QAM_256:2051:2049:2
[0002]:417000000:QAM_256:0:1985:2
[0001]:417000000:QAM_256:0:2049:1
[0001]:489000000:QAM_256:0:1985:1
[0002]:489000000:QAM_256:0:2049:2
[0001]:513000000:QAM_256:0:1985:1
[0002]:513000000:QAM_256:0:2049:2
[0003]:513000000:QAM_256:0:2113:3
[0004]:513000000:QAM_256:0:2177:4
[0005]:513000000:QAM_256:0:2241:5
[0006]:513000000:QAM_256:0:2305:6
[0007]:513000000:QAM_256:2369:2368:7
[0008]:513000000:QAM_256:0:2433:8
[0009]:513000000:QAM_256:0:2497:9
[000a]:513000000:QAM_256:2560:2561:10
```

They point to another page ([http://www.mythtv.org/wiki/index.php/DVB_search](http://www.mythtv.org/wiki/index.php/DVB_search)) to resolve this but it's mostly about MPlayer and the channel.conf file so I'm not sure it's important.  

Could someone tell me if I'm doing this right?  This table appears to be good channels but I don't know how to "use" them.  I actually picked them up with both the "standard" scan as well as with the "IRC" scan.  I don't seem to have picked them up with the MythBuntu scan (or perhaps these are the "encrypted" channels and Comcast encrypts everything.  I wouldn't put it past them).  

Thanks in advance for any help.

---

### Post by agamotto on 2008-10-12
> **Just4Fun20 said:**
> I've tried to get this properly configured, but haven't succeeded yet.  

I've been using MythBuntu for over a year, through a couple versions/revisions, and have been very happy with it.  I use a Hauppauge WinTV (150) tuner card for analog channels.  

I picked up a cheap digital (it's a hybrid and will apparently also tune analog)  tuner card from woot.  It's a Pinnacle PCTV HD 800i card.  For these tests I removed the WinTV card.  

I have virtually no OTA available.  I have Comcast cable.  I live north of Boston in NH.  I've never used their digital services and have no set top boxes, but I don't think that matters, or is the issue.  

I installed the card's drivers ([http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)) using the mercurial stuff.  I grabbed the .gz file, then 'tar -zxvf', then 'make' and finally 'sudo make install' and reboot.

I installed the firmware ([http://www.steventoth.net/linux/xc5000/](http://www.steventoth.net/linux/xc5000/)) using the extract.sh to pull and place the appropriate files.  

The backend setup sees the card and I can set it up as DVB (sorry, forgot the details here).  

I can't get the channel scan to work.  Well, let me rephrase that.  I can't find channels.  The MythBuntu scans do find many encrypted channels and perhaps one or two that are not.  This leads me to believe I'm still not looking in the right  place.  

MythTV has a long writeup in their wiki on finding channels ([http://www.mythtv.org/wiki/index.php/Adding_QAM_Channels_For_HDTV_Tuner_Cards](http://www.mythtv.org/wiki/index.php/Adding_QAM_Channels_For_HDTV_Tuner_Cards))  I installed these utilities and did the scans.  I think it found channels, but not without problems.  

That wiki page specifically discusses some "weird" output which looks like this (This is the first portion of my output.  The full file is 332 lines long.): 
```
[000a]:243012500:QAM_256:2112:2113:10
[000c]:243012500:QAM_256:1984:1986:12
[000b]:243012500:QAM_256:2048:2049:11
[0001]:351012500:QAM_256:1987:1984:1
[0002]:351012500:QAM_256:2048:2050:2
[0001]:369012500:QAM_256:0:1985:1
[0002]:369012500:QAM_256:2051:2049:2
[0002]:417000000:QAM_256:0:1985:2
[0001]:417000000:QAM_256:0:2049:1
[0001]:489000000:QAM_256:0:1985:1
[0002]:489000000:QAM_256:0:2049:2
[0001]:513000000:QAM_256:0:1985:1
[0002]:513000000:QAM_256:0:2049:2
[0003]:513000000:QAM_256:0:2113:3
[0004]:513000000:QAM_256:0:2177:4
[0005]:513000000:QAM_256:0:2241:5
[0006]:513000000:QAM_256:0:2305:6
[0007]:513000000:QAM_256:2369:2368:7
[0008]:513000000:QAM_256:0:2433:8
[0009]:513000000:QAM_256:0:2497:9
[000a]:513000000:QAM_256:2560:2561:10
```

They point to another page ([http://www.mythtv.org/wiki/index.php/DVB_search](http://www.mythtv.org/wiki/index.php/DVB_search)) to resolve this but it's mostly about MPlayer and the channel.conf file so I'm not sure it's important.  

Could someone tell me if I'm doing this right?  This table appears to be good channels but I don't know how to "use" them.  I actually picked them up with both the "standard" scan as well as with the "IRC" scan.  I don't seem to have picked them up with the MythBuntu scan (or perhaps these are the "encrypted" channels and Comcast encrypts everything.  I wouldn't put it past them).  

Thanks in advance for any help.

Comcast does scramble most of their stuff now.  Try this however, as it may work.  Set your freq. table to QAM-256, scan the Cable High range, and don't be surprised to see alot of encrypted channels.  It seems that most of the DTV pass-through channels are put here, if they aren't encrypted.  Oh, and use 0 as the channel separator.  This will make picking out the DTV channels easier on the remotes.

---

### Post by Just4Fun20 on 2008-10-23
I couldn't get any viewable channels.  I detected many that were encrypted and there's one that's supposed to be viewable but it's not really.  

I've come to the conclusion that Digital is not to be.  The idea of a set top box on each TV really galls me and that will be the single biggest item that drives me away from Comcast.  Well, that and the fact that I can't stand them.  

I did call Comcast and they said they'll have analog for "three more years".  Who knows how much they'll degrade it and remove channels in the meantime.  

I know, I'm preaching to the choir.  Digital is supposed to be an improvement but instead they're using it to restrict and control our viewing habits as well as to extort more money.  Then they wonder why torrents are so popular, where we can actually choose what we want to watch and when.  What an amazing concept freedom of choice. Oh well.  

Thank you for the help.

---

### Post by jaakan on 2008-10-23
I have Comcast Digital Cable ( Baltimore/DC area in MD ). About 90% of the channels are encrypted here. which still leaves me with enough channel that are watchable. But your local HD channels ( must-carry ones ) should not be encrypted as well as the "retransmission consent" channels both you could call "free-to-view broadcast television." 



you might want to read this review for that card

[http://www.fastsilicon.com/graphics-card-reviews/pinnacle-pctv-hd-card-800i-review-4.html](http://www.fastsilicon.com/graphics-card-reviews/pinnacle-pctv-hd-card-800i-review-4.html)

---

### Post by klc5555 on 2008-10-23
> **Just4Fun20 said:**
> I couldn't get any viewable channels.  I detected many that were encrypted and there's one that's supposed to be viewable but it's not really.  

I've come to the conclusion that Digital is not to be.  The idea of a set top box on each TV really galls me and that will be the single biggest item that drives me away from Comcast.  Well, that and the fact that I can't stand them.  

I did call Comcast and they said they'll have analog for "three more years".  Who knows how much they'll degrade it and remove channels in the meantime.  

I know, I'm preaching to the choir.  Digital is supposed to be an improvement but instead they're using it to restrict and control our viewing habits as well as to extort more money.  Then they wonder why torrents are so popular, where we can actually choose what we want to watch and when.  What an amazing concept freedom of choice. Oh well.  

Thank you for the help.


All "local" (whatever that means) stations ought to be provided in clear QAM by Comcast. Just outside Boston where I am this includes the SD versions and HD (except for a couple of the smaller locals) versions of all OTA Boston stations. Also Comcast's own CN8, and a few of the cable-only stations (History, Style, BET, and the various extra PBS feeds). And occasional ad hoc feeds like two extra HD channels added for the recent Olympics. Everything else is encrypted, of course.

So I'd be surprised if there were really nothing at all provided in clear QAM in your area of New Hampshire. Scan again in QAM 256 and also QAM 64 (Comcast seems to use that too) and check closely for the multiplexes scattered between about ch. 72 and ch. 96 on your digital scan (regular "Cable", therefore, and not "Cable High") as most of the clear QAM seems to be located in this  range. 

Good luck! :)

---

