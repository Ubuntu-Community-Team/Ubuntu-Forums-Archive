---
title: "Crossing over from Windows/Sagetv to Mythbuntu. Recommendations?"
date: 2011-11-26
forum: Mythbuntu
---

### Post by sasamsen on 2011-11-26
Here is my existing setup in basement.


Backend/frontend:

Antec Three hundred ATX tower
ASUS M4A89GTD PRO AMD 890GX Motherboard
AMD Phenom II X3 Triple Core 2.5 Ghz 
SeaSonic S12II 430B 430W ATX12V V2.3/EPS12V 80 Power Supply
2 Hauppauge HVR-2250 tuners
6 GB Ram
250 GB Hard drive for operating system
2- 2TB Hard drives for storage

Was looking at this--- EVGA 01G-P3-1303-KR GeForce 8400 GS 1GB 64-bit DDR3 PCI Express 2.0 x16 HDCP Ready Low Profile Ready Video Card ---from newegg for $39.00

Would that card work good?  I want 1080p video.  I didn’t pick it for price I picked it figuring it used less power than the big ones.

This will get plugged into my Onkyo receiver via HDMI.  Will I get 5.1 or higher?

I’m also looking to build a Diskless front-end only machine from scratch.  Any recommendations on parts would be great!

Would Mythbuntu run well on a new Mac Mini and provide 1080p?

Thanks,
Scott

---

### Post by nickrout on 2011-11-27
> **sasamsen said:**
> Here is my existing setup in basement.


Backend/frontend:

Antec Three hundred ATX tower
ASUS M4A89GTD PRO AMD 890GX Motherboard
AMD Phenom II X3 Triple Core 2.5 Ghz 
SeaSonic S12II 430B 430W ATX12V V2.3/EPS12V 80 Power Supply
2 Hauppauge HVR-2250 tuners
6 GB Ram
250 GB Hard drive for operating system
2- 2TB Hard drives for storage

Was looking at this--- EVGA 01G-P3-1303-KR GeForce 8400 GS 1GB 64-bit DDR3 PCI Express 2.0 x16 HDCP Ready Low Profile Ready Video Card ---from newegg for $39.00 yes but there are limitations with the 8400. Better to buy a 22oGT or a 430> 

Would that card work good?  I want 1080p video.  I didn’t pick it for price I picked it figuring it used less power than the big ones.

This will get plugged into my Onkyo receiver via HDMI.  Will I get 5.1 or higher?
 you will get 5.1 with 5.1 source material (ac3 or dts)> 
I’m also looking to build a Diskless front-end only machine from scratch.  Any recommendations on parts would be great! better to buy an ion machine like a revo etc> 

Would Mythbuntu run well on a new Mac Mini and provide 1080p?

Thanks,
Scott

dunno, what are the specs, particularly processor and graphics

---

### Post by romanyiv on 2011-11-27
You need to do your homework on how you are going to bring your content into myth.   The HD-PVR is the only way to bring "HD" - via component out of a set-top box - into myth (via USB) - and it can be a bit buggy.  The HD Homerun for un-encrypted content works great for OTA HD (or cable).   Outside of those devices you are very limited as far as HD is concerned.   And there is a steep learning curve if you are not familiar with linux - and how mythtv is set up.  It is not for the faint of heart.  Not trying to discourage you - I've been very happy with myth - been using it since around 2006 - but it can be pretty demanding to set up - and in a DRM world your options are pretty much limited to a HD-PVR connected to a set-top box.  I'm currently looking at Microsoft media center connected to a HD Homerun Prime device.   Not anywhere close to making a call on THAT  yet - just looking.  What I really really like about myth is that it's a client/server model - the server brings in the content - and the clients streams from that server.  Throwing up a cheap client is pretty trival - the real challenge is the server end.   I also like PIPs - you can have 4 PIPs - and the main show - going at the same time in myth.  Yeah - overkill - but you can't do PIPs in MMC.

---

### Post by sasamsen on 2011-11-27
Thanks nickrout,  I'll check out the Revos.


romanyiv,

I'm only looking for OTA HD.  Are you saying the 2250s won't bring OTA HD into Myth or you talking cable?  I live in the boonies and can't even get cable.

I've used Windows Media Center.  I didn't like it.  I didn't find it completely stable.  Got tired of going into the basement having to reset the machine.  Ditched it and went to sagetv backend with extenders.  Worked flawlessly 99% of the time.  Now I'm looking to add another tv to the household and can no longer buy the Sage HD300 extenders so I'm looking to change.  Since Linux is known for it's stability I figured why not.  Once you get everything set up right its stable I assume?

I've played with Linux on and off over the years.  Nothing deep though.  Hence going with and integrated distro.  I like tinkering.


Thanks for the replies!!

---

### Post by nickrout on 2011-11-28
> **sasamsen said:**
> Thanks nickrout,  I'll check out the Revos.


romanyiv,

I'm only looking for OTA HD.  Are you saying the 2250s won't bring OTA HD into Myth or you talking cable?  It will, provided the channels are not encrypted. Many are, and the only way to get HD in that case is to get a set top box and then capture the STB output with an HDPVR (which captures component video and compresses it to nice unencrypted h264 video). However if windows has worked with your local channels, I believe myth will.>  I live in the boonies and can't even get cable.

I've used Windows Media Center.  I didn't like it.  you are welcome here :) >  I didn't find it completely stable.  Got tired of going into the basement having to reset the machine.  Ditched it and went to sagetv backend with extenders.  Worked flawlessly 99% of the time.  Now I'm looking to add another tv to the household and can no longer buy the Sage HD300 extenders so I'm looking to change.  Since Linux is known for it's stability I figured why not.  Once you get everything set up right its stable I assume?

 providing you don't futz with it too much> 
I've played with Linux on and off over the years.  Nothing deep though.  Hence going with and integrated distro.  I like tinkering.


Thanks for the replies!!

---

### Post by sasamsen on 2011-12-03
Well I managed to get mythbuntu installed today!  I'm running the onboard graphics right now as the new GTS 460 was causing errors when i was installing.   I havent attemped to install it since.   Been to busy playing and tinkering!  Both 2250s are installed and running fine.  Have a mac mini running an OSX Mythtv frontend only setup.  Tomorrow hopefully im going to get remotes and the video card up and running!  


Quick question,  I've been trying to figure out if there is a setting to record only new episodes(first run) of tv shows?  I havent come across anything of the sorts yet.

---

