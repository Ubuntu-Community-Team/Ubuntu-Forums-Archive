---
title: "TV channels different in Mythbuntu"
date: 2009-12-09
forum: Mythbuntu
---

### Post by cmadooly on 2009-12-09
Hi,

I just built my mythbuntu system. Everything works great but there is one small problem that is confusing me with the channel setup. I have a HVR-1250 and my frontend and backend is on the same box.

I don't have 'cable' or satellite. I have a cable modem for my internet through NY Time Warner and I just have a splitter that goes to my TV. This allows me get internet and I get basic channels (CBS, NBC, FOX, ABC, etc.) but also gives me some channels that I would need cable for (NY1, TBS, SPIKE, FOODTV). I think this is called 'Cable Ready'.

Also, the channel numbers are a little different from what I would get OTA. CBS OTA is 2 but on my TV it comes as 12. NBC is 4 OTA but my TV gets it as 14, etc.

I have an account with schedulesdirect and I set up my subscription with 'Time Warner Cable Ready'. The subscription is on point with the channel numbers and their names (NBC is 14, CBS is 12, NY1 is 3, etc.).

Now when I scan for channels, regardless of what the Frequency Table or Modulation is, Mythtv detects channels as if it's OTA. NBC is 4, CBS is 2, and no NY1, TBS or FOODTV. It also gives me 4 channels of HBO.. which is weird and I would typically love this but I need FOODTV otherwise the project is a failure as my wife can't live without FOODTV.

I've tried all different variations of Frequency Table and Modulation settings but can't get the same channels on my MYTHTV that I get on my regular TV. I am also clueless as far as what the different types of signals there are. I tried reading up on it but it was just super confusing and overwhelming.

So, ideally what I would like is to have both, the channels I get OTA and the 'Cable Ready' channels. I'll manually delete the duplicates. But I'll still just be happy with the 'cable ready' channels. Please advise.

EDIT: I also don't care for TV Listings although that would be nice. I just want to get the 'Cable Ready' channels working then I'll figure out the schedule listings from that point on.

---

### Post by jlagrone on 2009-12-09
NY1, TBS, FOODTV and similar channels are likely analog cable channels and last time I checked there was little or no support available for the analog capture capabilities of the HVR-1250 (hopefully this has changed, but a quick searh didn't turn up anything promising).  So that's probably why you're not seeing some channels. 

As for the channels being different numbers, there are several potential causes, but in the end it doesn't matter, just go into the channel editor on the backend setup and change the numbers to whatever you want them to be.

---

### Post by azmyth on 2009-12-09
Sounds like you didn't create two sources in schedules direct. I have three sources 1) OTA (SD type LocalBroadcast) 2) Digital Cable (type Digital) and 3)Analog Cable (type Cable) for a three tuner card system.  You'll probably want 1 and 3. You then have to make sure you tie your video source with the proper tuner card.

I think you still have to setup sources with different zip codes so in my case three adjacent zips did the trick.

---

### Post by cmadooly on 2009-12-10
azmyth: I did create 2 sources in schedules direct and I tied my tuner card to the source. One sources is just 'Cable' and the other is 'Cable Ready'. When I click the 'Retrieve' button after entering my SD username/pw in mythtvbackend setup, it pulls down both sources. I select the 'Cable-Ready' sources, and then scan with QAM(256) with HIGH HRC and it resulted with either no channels found or the same basic channels found without the TBS/FOODTV stations. Trying different combinations doesnt work either.

jlagrone: I don't really care for the channel numbers, but just thought it was related to my card not detecting these channels. If they are analog stations and I believe you are accurate when you say that HVR-1250 doesn't support them, then that stinks and I guess I'm SOL. How can I determine if those channels are analog or not? and weren't all channels converted to digital a few months ago (in the US)?

The only reason why I don't need to spend $50/month on cable is because I get FoodTV for free- damn you Rachel Ray and Paula Dean. I have a ATI TV Wonder (not tv wonder PRO) lying around, maybe I can somehow configure that to capture the analog stations.

---

### Post by matt06 on 2009-12-10
> **cmadooly said:**
> I don't have 'cable' or satellite. I have a cable modem for my internet through NY Time Warner and I just have a splitter that goes to my TV. This allows me get internet and I get basic channels (CBS, NBC, FOX, ABC, etc.) but also gives me some channels that I would need cable for (NY1, TBS, SPIKE, FOODTV). I think this is called 'Cable Ready'.

Are these channels perhaps digital Clear-QAM channels that your TV is picking up but your card is not?  Since you say you are not supposed to get any TV channels through Time Warner (except maybe for locals), is it possible that Time Warner screwed up and you aren't supposed to be getting the extra ones at all but somehow your TV can tune them?

What kind of TV and can you tell if the channels are digital or analog when tuning them?

---

