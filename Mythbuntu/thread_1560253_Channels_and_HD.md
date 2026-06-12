---
title: "Channels and HD"
date: 2010-08-24
forum: Mythbuntu
---

### Post by Tteddo on 2010-08-24
Hello all!
I have a Ubuntu 10.04 box with MythTV (not Mythbuntu) and I bought a Hauppage HVR 2250 to work on it (digital only). I also put my old PVR-500 in it. I have the HVR-2250 card setup to use the SchedulesDirect Digital listings and the PVR-500 to use the Analog listings.
Now, apparently I am not doing something right. In MythWeb the listings all say No Data for all the channels that are digital in the format of 7_1. 6_2, etc. and I have no way of getting to those channels when I watch TV except through the on screen listings. If I do that though, then I can use the up/down arrow keys to navigate the digital channels. Also when I go to channel 7 for instance it is using the analog signal and not the digital one (i.e. there are 2 entries one is 7(WHDH) and 7(3007)). 
When I did the channel scan for the digital card it said there was conflicts (even before I put the analog card in) and made suggestions as to what to name them which I think is where the underscore channels are coming from. I can see why it would do that because channel 6 has like 4 different digital channels) I think that is the reason there is no data because the number doesn't match?
I know this must be blindingly obvious, but could someone point me to a tutorial so I can use the digital channels?

---

### Post by agamotto on 2010-08-24
I will toss in my 2¢ on what may have happened.  When you set up your sources for analog and digital, did you make sure in SD that you have two lineups, 1 for analog, 1 for digital.  When adding channels to the analog, fetch listings from source.  The digital channels usually have to be scanned manually.  If you can state where your digital channels are coming from, we can help you specify what settings to add to the digital search options.  

When you have the digital lineup set, the data set will do its best to match what is found when you scan for digital channels.

---

### Post by LowSky on 2010-08-24
I had a similar issue when I first started up.  The example of 7_1 is actually the way a channel should report for digital, so don't worry about that it is normal. For me channel 7 has 3 sub channels and channel 4 has 4, and it list like 4_1, 4_2, etc... As for no data showing up it could be an isse with schedules direct, try to run the mythfilldatabase again to see if it fixes itslef. but I would first go o schedules direct website and make sure you picked the corrct line up, then look through the line up to make sure you get the right channels. Then what you can do is go into Mythbackend do a new scan.... it should find channels just fine, and then maybe find channels it cant match. Tell the system to ignore those, trust me more than likely they are blank channels you cant watch anyway.


As for Live TV, MythTv uses whatever tuner is availible without conflicting recording. So its using your analog one. To switch tuners just press M on the keyboard and change the input.

Hope this helps

---

### Post by Tteddo on 2010-08-25
> **agamotto said:**
> I will toss in my 2¢ on what may have happened.  When you set up your sources for analog and digital, did you make sure in SD that you have two lineups, 1 for analog, 1 for digital.  When adding channels to the analog, fetch listings from source.  The digital channels usually have to be scanned manually.  If you can state where your digital channels are coming from, we can help you specify what settings to add to the digital search options.  

When you have the digital lineup set, the data set will do its best to match what is found when you scan for digital channels.

Yes, that's what I did. I added the digital lineup to SD and used that for the digital card and used the analog for the 500. I manually scanned the digital, and did click the "fetch listings from source" for the analog ones, although it didn't appear to do anything. I think I scanned then.
For "If you can state where your digital channels are coming from" do you mean 04076- Metrocast? I know it is QAM 256 from my stint playing with Mythbunu earlier.

---

### Post by Tteddo on 2010-08-25
> **LowSky said:**
> I had a similar issue when I first started up.  The example of 7_1 is actually the way a channel should report for digital, so don't worry about that it is normal. For me channel 7 has 3 sub channels and channel 4 has 4, and it list like 4_1, 4_2, etc... As for no data showing up it could be an isse with schedules direct, try to run the mythfilldatabase again to see if it fixes itslef. but I would first go o schedules direct website and make sure you picked the corrct line up, then look through the line up to make sure you get the right channels. Then what you can do is go into Mythbackend do a new scan.... it should find channels just fine, and then maybe find channels it cant match. Tell the system to ignore those, trust me more than likely they are blank channels you cant watch anyway.


As for Live TV, MythTv uses whatever tuner is availible without conflicting recording. So its using your analog one. To switch tuners just press M on the keyboard and change the input.

Hope this helps

M does work, thanks. The digital sound is quite faint but I'll work on that later (with a different post if necessary) unless you know a quick fix.

I thought of the SD thing and they do have a full lineup. I blocked the ones I don't get (above ~80). They are listed in there like normal though, i.e. 4,5,6,7 and there are no 6_1, 7_2, etc. So does that mean that Metrocast isn't giving them the data? I checked the ones that show no data and there are definitely things on those (like 7_1 is WHDH-HD for example- great picture!).

---

### Post by jrhartley on 2010-08-25
What I had to do is log in to mythweb from a different computer then click in the mythtv drop down and go to settings then channel info.you should see your channels listed and the box where xmltvid should have a number in it. if it doesn't then that's your problem. you'll have to do it manually go to schedules direct and and pull up channel line up you will be using. hover over the channel you need and you will see the xmltvid take that and populate the box in mythweb where you went to earlier.after you have done all of them go back to your myth box and re-run mythfilldatabase...hope this helps

---

### Post by Tteddo on 2010-08-25
> **jrhartley said:**
> What I had to do is log in to mythweb from a different computer then click in the mythtv drop down and go to settings then channel info.you should see your channels listed and the box where xmltvid should have a number in it. if it doesn't then that's your problem. you'll have to do it manually go to schedules direct and and pull up channel line up you will be using. hover over the channel you need and you will see the xmltvid take that and populate the box in mythweb where you went to earlier.after you have done all of them go back to your myth box and re-run mythfilldatabase...hope this helps

Ok, I went through all the channels and put in the actual xmlvid number on what they were (they were empty). Then I ran mythfilldatabase and it didn't update the "no data" ones. I went back in and noticed a checkbox called "useonairguide" that was checked for all the ones with no data. Tried unchecking a few of those but it didn't matter.
Bummer, this sounded totally like it was the problem!

Further question: For CH 6 for instance if I found that it was broadcasting CH 6 HD which is actually channel 706 (which I don't get) do I have to enable 706 at SD? I did do that.

---

### Post by jrhartley on 2010-08-26
Hey your on the right track. google mythfilldatabase. there are a couple switches you can add to start completely over.
I think its mythfilldatabase -refresh --all...try that. I use the OTA guide from schedules direct and not the cable one because all I can get clear qam are the locals. and if you do it manually it doesnt matter. it makes it a little easier (not as many channels to update in mythfilldatabase)

---

### Post by agamotto on 2010-08-26
The audio can be as simple as dropping to the XFCE interface, and making sure that your Master and PCM 'volume knobs' are set to 90% or better.  This usually solves most audio problems.  Depending on your sound card, you might also have to add the switch Master Front, and put that above 90%.

---

### Post by agamotto on 2010-08-26
> **Tteddo said:**
> 
Further question: For CH 6 for instance if I found that it was broadcasting CH 6 HD which is actually channel 706 (which I don't get) do I have to enable 706 at SD? I did do that.

My local cable system is Mediacom, and it sounds as if your cable operator is dropping/removing data.  We have several sub-channels OTA, with Mediacom only passing data for the 'main' channels, ie. 6_1.  The rest seem to be tossed around at random.  One tv will have 6_2 on 117-4, the other 114-3.  The only solution offered by Mediacom is to buy/rent one of their digital boxes.  

You may be in a similar situation.

---

### Post by JMcFly on 2010-08-27
So the only way to set cable QAM channels is manually scanning them and figuring out what channel each one is?

---

### Post by jrhartley on 2010-08-27
I have Time Warner cable. That is the only way to do the digital cable (qam). There are only about 10 or 12 clear qam channels worth doing anyway.

---

### Post by LowSky on 2010-08-27
> **JMcFly said:**
> So the only way to set cable QAM channels is manually scanning them and figuring out what channel each one is?

Schedules direct will give you  channel listings, so realistically all your doing is scanning to to get a channel lock, and the data the tuner get is matched to the data from schedules direct.

---

### Post by Tteddo on 2010-08-29
> **agamotto said:**
> The audio can be as simple as dropping to the XFCE interface, and making sure that your Master and PCM 'volume knobs' are set to 90% or better.  This usually solves most audio problems.  Depending on your sound card, you might also have to add the switch Master Front, and put that above 90%.

I am running Gnome, but I did think of that. The regular audio is fine, it's just when I am on a digital channel it's about 3/10ths the volume. This is the same even when the digital card is used across my network on all the other machines. Is there a separate setting just for the audio on the digital card inside MythBackend? I poked around, but didn't see anything.

---

### Post by Tteddo on 2010-08-29
> **jrhartley said:**
> Hey your on the right track. google mythfilldatabase. there are a couple switches you can add to start completely over.
I think its mythfilldatabase -refresh --all...try that. I use the OTA guide from schedules direct and not the cable one because all I can get clear qam are the locals. and if you do it manually it doesnt matter. it makes it a little easier (not as many channels to update in mythfilldatabase)

Ok, this filled in about 3/4ths of the digital, but not all. This is strange because I set the xmlvid numbers to what they were actually broadcasting (like 23_1 is WPFO-HD 723 and not QVC like the regular 23) but it still didn't update. I enabled the higher numbers in SD too. Maybe Metrocast just isn't giving info on those. I also noticed that they ditched the on-screen guide from Zap2It, nice huh?

---

