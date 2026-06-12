---
title: "How can I edit my &quot;Unknown&quot; channels and get guide data?"
date: 2008-09-21
forum: Mythbuntu
---

### Post by bmwman on 2008-09-21
I have a few channels which appear as Unknown in the guide and no data is downloaded. I just use the regular EIT or whatever comes on he air. I tried editing the channel in the backend but it still didn't get any data. For example I had channel 43#13 which is actually FOX. I changed the name and it downloaded the icon, but still no info in the guide. I have quite a few other ones as well. I've heard that i can manually add the channels but how do I know the frequencies and all that stuff? BTW i use COX cable but i don't have a STB and the cable is directly connected to my HDhomerun.I get whatever channels work without the box.

---

### Post by bmathis on 2008-09-21
I saw a post similar to this a few days ago. I think that you also need to log into your SD account and change the info there as well. I could be wrong though.

---

### Post by bmwman on 2008-09-22
Well, i don't use Shedules Direct, or at least i'm not trying to. I don't think $20 per year membership is that big of a deal but it kinda defeats the purpose of Linux, open source and free.

I would prefer to get it to work with just EIT (the info that comes with the channel over the cable) but if it's impossible I would go to SD.

---

### Post by ian dobson on 2008-09-22
Hi,

Do you see anything interesting in your /var/log/mythtv/mythbackend.log?

You might need to add eit to the command line parameter for myth by editing the /etc/default/mythtv/mythtv-backend.

Have you enabled OTA EPG for your channels? What tuner card do you have? Have you enabled EIT for you tuner card?

Regards
Ian Dobson

---

### Post by bmwman on 2008-09-22
> **ian dobson said:**
> Hi,

Do you see anything interesting in your /var/log/mythtv/mythbackend.log?

You might need to add eit to the command line parameter for myth by editing the /etc/default/mythtv/mythtv-backend.

Have you enabled OTA EPG for your channels? What tuner card do you have? Have you enabled EIT for you tuner card?

Regards
Ian Dobson

I have a Silicondust HDhomerun which is a dual HD tuner, network attached. I believe I have the EIT enabled because I do have some info on most channels in the Guide. Probably like 30% of the other channels though appear as Unknown and no data. That's what I'm trying to fix. If there is an easier way to add all the channels via manual lineup i'm willing to try that, but I have no idea how to do that.

---

