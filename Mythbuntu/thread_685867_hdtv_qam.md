---
title: "hdtv qam?"
date: 2008-02-02
forum: Mythbuntu
---

### Post by RJ Hythloday on 2008-02-02
I understand that this will work in theory, but I"m hoping to hear from some one that is using this in practice.

I'm told that my basic cable ($10 a mo) has the qam hd basic channels that I would be able to access through a capture card where as I"m not able to straight into the tv. 

I hope to build a htpc on the cheap and am considering mythbuntu but am also considering just adding myth to kubuntu.

---

### Post by newlinux on 2008-02-02
Whether this is true or not depends on your provider and location. But most people are able to get their local HD stations via a QAM tuner with just basic cable. Your TV could get them if it had a QAM tuner.I am able to in my area (although now I subscribe to more than just basic cable).

---

### Post by RJ Hythloday on 2008-02-02
When I had basic cable I could get a couple local channels through the dtv input but a couple were only 480i and didn't look nearly as good as when I had full cable and a hd-dvr they were full 720p then. I'm kind of wondering if it would be a different feed? I didn't even get all the locals on dtv just a few.

---

### Post by tedder on 2008-02-02
Where I am, with my provider (Portland, OR, Comcast), we get HDTV over cable via QAM. It includes all the local channels (ABC/NBC/FOX/WB/etc) and a few others. There are a handful of cable-style channels that come over the clear too, but they are just poorly digitized 480i feeds.

Still, it is very nice to get the network channels in hi-def. I use the HDHomeRun, though there are a few other options.

---

### Post by newlinux on 2008-02-02
> **RJ Hythloday said:**
> When I had basic cable I could get a couple local channels through the dtv input but a couple were only 480i and didn't look nearly as good as when I had full cable and a hd-dvr they were full 720p then. I'm kind of wondering if it would be a different feed? I didn't even get all the locals on dtv just a few.

It should be the same feed. They send both the digital and analog station over the same line. This is one of the reasons cable companies are slowly getting rid of analog stations (so they can make room for more HD stations, since the analogs take up more bandwidth). Heck, in Chicago they got rid of all cable analog a while ago (no tuning cable at all without a digital box or digital TV). 

I get the locals in HD and in SD via QAM. Maybe you just didn't pick them all up in a scan. Also, some cable companies don't provide them in some regions unencrypted, and some even put them on QAM64 instead of QAM256 (on mine 2 are QAM64, the rest QAM256). Supposedly not providing the HD locals unencrypted via QAM is against the law, but cable companies sometimes do it anyway.

Point is, there is no guarantee, but in most cases you do get the HD locals.

---

### Post by theacoustician on 2008-02-03
> **RJ Hythloday said:**
> I understand that this will work in theory, but I"m hoping to hear from some one that is using this in practice.

I'm told that my basic cable ($10 a mo) has the qam hd basic channels that I would be able to access through a capture card where as I"m not able to straight into the tv. 

I hope to build a htpc on the cheap and am considering mythbuntu but am also considering just adding myth to kubuntu.

If your TV has a QAM tuner, it will get the same channels as any QAM capture card will.

Chances are, you will not be getting anything in HD via QAM that you couldn't just pull OTA.  You might get a few more basic cable channels digitally, but they'll be SD.  Almost every cable operator is locking HD channels to a separate package outside of basic cable in order to charge customers more.  The case for HD OTA is stronger when you consider that most OTA stations aren't compressed to the same level cable operators compress their content to fit it all on one piece of coax.

---

### Post by RJ Hythloday on 2008-02-03
> **theacoustician said:**
> If your TV has a QAM tuner, it will get the same channels as any QAM capture card will.

Chances are, you will not be getting anything in HD via QAM that you couldn't just pull OTA.  You might get a few more basic cable channels digitally, but they'll be SD.  Almost every cable operator is locking HD channels to a separate package outside of basic cable in order to charge customers more.  The case for HD OTA is stronger when you consider that most OTA stations aren't compressed to the same level cable operators compress their content to fit it all on one piece of coax.

That's very intersting, I've considered buying a ota hd antenna but am concerned it will be no better quality than old fashioned rabbit ears w/ lots of adjusting and snow.

Do you use an ota had antenna?

---

### Post by newlinux on 2008-02-03
Check out [http://www.antennaweb.org/](http://www.antennaweb.org/)

I have an OTA antenna (indoors). I do have to adjust it a little for some stations (It is used rimarily as a backup when cable is out for this reason). but I live out in the suburbs, a ways away from the transmissions.

---

### Post by RJ Hythloday on 2008-02-03
> **newlinux said:**
> Check out [http://www.antennaweb.org/](http://www.antennaweb.org/)

I have an OTA antenna (indoors). I do have to adjust it a little for some stations (It is used rimarily as a backup when cable is out for this reason). but I live out in the suburbs, a ways away from the transmissions.
Thanks, that's some good info. I'll use that site again when I move.

---

### Post by twkisner on 2008-02-04
> **RJ Hythloday said:**
> That's very intersting, I've considered buying a ota hd antenna but am concerned it will be no better quality than old fashioned rabbit ears w/ lots of adjusting and snow.

Do you use an ota had antenna?

I use OTA for HD.  Since the signal is digital, you either get a perfect picture or nothing at all (never any snow).

I have a nice antenna in the attic and get all of the local channels in the area without having to adjust anything.

---

### Post by theacoustician on 2008-02-04
> **RJ Hythloday said:**
> That's very intersting, I've considered buying a ota hd antenna but am concerned it will be no better quality than old fashioned rabbit ears w/ lots of adjusting and snow.

Do you use an ota had antenna?

Digital OTA is not the same as analog OTA.  If you get signal, its crystal clear.  If not, you get frame dropping like you might see on a streaming video.  There is no "snow".  By spec, ATSC broadcast channels are 19.76 Mb/s.  The broadcaster can choose whatever they'd like to do with that bandwidth, but typically if they're running HD programming, all or most of it goes towards that limit.  Cable, you get no such guarentees.  Most HD stations are capped down to around 15Mb/s or less.  I can tell you for fact that DirecTV is broadcasting most of their MPEG2 HD streams at 10Mb/s and only using 1024x1080 resolution with aspect ratio signaling to trick it back out to 16:9 on the playback end.  Quite literally, the quality of video being broadcast OTA in most areas surpasses that of cable and satellite.

Yes, I use an antenna and in A/B tests, I can tell you it surpasses the quality of cable in my area for the stations broadcast with both methods.

---

### Post by RJ Hythloday on 2008-02-04
> **twkisner said:**
> I use OTA for HD.  Since the signal is digital, you either get a perfect picture or nothing at all (never any snow).

I have a nice antenna in the attic and get all of the local channels in the area without having to adjust anything.

That's good news!

---

### Post by newlinux on 2008-02-04
> **theacoustician said:**
> Digital OTA is not the same as analog OTA.  If you get signal, its crystal clear.  If not, you get frame dropping like you might see on a streaming video.  There is no "snow"....

I should have been clear, that I was talking ATSC signals. I have to adjust my indoor antenna for some stations to get them at all, but when I get them they are of great quality. If I had an outdoor antenna with wire running everywhere to every room in my house with a tuner I'd  capture OTA all the time instead of QAM...

---

