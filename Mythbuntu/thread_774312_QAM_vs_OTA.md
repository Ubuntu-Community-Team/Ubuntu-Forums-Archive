---
title: "QAM vs OTA"
date: 2008-04-29
forum: Mythbuntu
---

### Post by bah1976 on 2008-04-29
I'm not sure if this is the best place to post this, but I'm pretty sure the experience in this forum can answer.

I currently have Comcast HSI & Digital Cable with PVR service.  At the end of my myth project, I intend to only have HSI & drop the cable/PVR (since I'm building my own).  I plan on using OTA to get all my Chicago networks, but I'm wondering how QAM works.  Since I will still have a feed to Comcast for the internet, will that cable be able to pick up QAM if I plug it into a QAM tuner?  I am not trying to steal cable - my focus is OTA.  I'm just wondering, how does Comcast "know" if I have a QAM tuner?  Would I have to call Comcast and 'authorize' my tuner with their network somehow?  If so, any idea of cost?

These are the idle wonderings of my mind as I work through all my options.  Any thoughts?

Thanks!!!

---

### Post by murchball on 2008-04-29
I have a similar setup: Hauppauge x50 tuners for analog cable, an HDHomeRun for OTA and an HD-5500 for QAM. AFAIK, my cable company has no idea that I have a QAM tuner; everyone gets the signal, but only those with an appropriate tuner can tune it. However, I'm guessing that if you're only paying for internet service, your entire cable tv service gets turned off, both QAM and analog. In my area, there is only one station (fox) that comes over QAM that I cannot get OTA, otherwise I wouldn't even bother with QAM .

HTH

---

### Post by jhfry on 2008-04-29
I am currently using QAM, but I will be stopping soon as OTA has some advantages to QAM in my area.

Currently I do not pay for cable, however because I had experienced some issues with my cable internet service I managed to convince the cable tech to remove the filter they had on my line to allow the television signals through.  So I get free basic cable (free if you consider $50/mo for basic cable + Internet free, I think it's more reasonable).

However I recently discovered that I could wrap the center conductor of a cheap push-on-connecer peice of RG59 (the thinner coax) around a coat hanger and still pull perfect HDTV OTA.  This made me consider the advantages and disadvantages of both.

OTA Advantages:

More channels - My cable company does not broadcast as many QAM channels, for example no CW.  Additionally with the right antenna I might pull in channels from other nearby cities (Ontario Canada is about 25mi away (I live outside Detroit).

Fewer Channels - I realize that this is the exact opposite of the last advantage... my cable provider puts all kinds of music channels and video-on-demand channels across QAM.  This is great if I want to scan the channels for someone who purchased a good movie, or listen to music... but adds a bunch (about 100) Unknown channels to my mythtv config and it makes for a messy program guide.

Rumours of recompression - I heard a rumor (though I doubt it) that some cable companies are reducing the quality of HD channels to reduce bandwidth.  I suppose it's possible but it doesn't make much sense as a channel is a fixed bandwidth... any manipulation of it would require a non-standard tuner.  Though I wouldn't be surprised if Satellite providers do this.

Faster tuning - I don't know for a fact that OTA tunes faster, but it does seem to.

Less chance of changes - Cable companies are known to drop or modify channels.  I suspect that this is slowing down and will eventually stop happening so frequently, it could be an annoyance.


Disadvantages of OTA:

Weather sensitivity - I don't suspect this to be much of an issue for me... if I can use a coat hanger and pull nearly flawless HDTV in clear weather, I don't suspect many channels I watch will have issues during a hurricane once I connect a decent antenna.

Potential of missing out on good cable channels - I suspect that as HD QAM tuners become more common, cable companies will begin to offer more channels in QAM.  Someday, all those 'basic' cable channels might be broadcast in QAM so that customers won't need a box and cable companies can consolidate multiple analog channels into one digital channel.  Of course I can always change my mind again.


Over all I would say that right now OTA is better for me, however QAM might eventually surpass it significantly.  I would try both and see if your in agreement.

As to if you will get QAM without basic cable... I don't know.  Typically they use a passive filter that blocks those frequencies that are not used by the internet service.  However the internet service uses frequencies (channel 108ish) near many/most of the QAM channels (channel 80+ in my area.  It's possible that the filters they used do not block all or even any of the QAM channels.

---

### Post by jmore9 on 2008-04-29
Here in Grand Rapids, MI Comcast is the provider for cable tv.  They allow folks to view the locals -- local tv stations -- on clear qam.  But you have to pay for some sort of tv package to get anything else.  The only difference between the clear qam and OTA here is that i can get channel 3's CW station on qam which i cannot receive OTA.  The OTA here is very good HD broadcasts come in very good also. BTW i live on the 2 floor of an 6 story apartment building with a lot of tall building around me and i get almost all the stations with the exception of 3's CW which i get on clear qam.

---

