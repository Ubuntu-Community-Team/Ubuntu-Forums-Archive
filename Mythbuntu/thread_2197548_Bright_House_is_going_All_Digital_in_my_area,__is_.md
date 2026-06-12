---
title: "Bright House is going All Digital in my area,  is my DVR now useless?"
date: 2014-01-04
forum: Mythbuntu
---

### Post by mcapaldo on 2014-01-04
I have a PC running Ubuntu 10.10 with Mythtv installed.

its a Quad core AMD 3.2GHz Cpu with 2 GB RAM.  It has two PVR-500's, and a HVR-2250.  Each allowing me currently to record up to 6 programs at once (all analog signals mind you).  

Just got the heads up from BH that they are forcing everyone to go all digital and require you to have a DTA (basically a stripped down cable box).  

Am I screwed?   What new hardware would I need to continue using my pc as a dvr.  

I looked into a Silicon HD Homerun Prime would I need 6 of them?

---

### Post by uteck on 2014-01-04
The Homerun Prime has 3 digital tuners, so you would need 2 of them and 2 cable cards if you want to do 6 shows at once.
Your provider needs to supple the cards and make sure they are configured to your account.

Also, it only works with MythTV over .25 according to [http://www.silicondust.com/products/models/hdhr3-cc/](http://www.silicondust.com/products/models/hdhr3-cc/)

---

### Post by aelfric55 on 2014-01-05
> **mcapaldo said:**
> I have a PC running Ubuntu 10.10 with Mythtv installed.

its a Quad core AMD 3.2GHz Cpu with 2 GB RAM.  It has two PVR-500's, and a HVR-2250.  Each allowing me currently to record up to 6 programs at once (all analog signals mind you).  

Just got the heads up from BH that they are forcing everyone to go all digital and require you to have a DTA (basically a stripped down cable box).  

Am I screwed?   What new hardware would I need to continue using my pc as a dvr.  

I looked into a Silicon HD Homerun Prime would I need 6 of them?

Each DTA will adapt a digital stream to allow you to record it to an analog tuner. Some cable providers allow you two DTAs without additional charge, the third and subsequent will cost a nominal rental ($1.99 for each per month from Comcast, for example). Each DTA on Mythtv will require running its own instance of LIRC, and its own IR blaster to allow Mythtv to change channels on the DTA. 

When Comcast in my area went all-digital years ago, I went with 3 DTAs to accomodate the 3 Hauppauge 1600s that I was using at the time for analog, adding LIRC and IR blasters for channel changing. Comcast digital clear QAM I continued to tune directly. When the company began to encrypt all its former clear QAM, I went to over-the-air for HD digital, but kept the 3 DTAs, the 3 analog tuners, and the Comcast account for all the expanded basic digital tier stations that aren't broadcast over-the-air. A simple enough solution that's been chugging along for four years now.

So you'll have some sort of transition, to be sure, but it shouldn't be all that burdensome whichever solution you opt for.

---

### Post by mcapaldo on 2014-01-07
For those of us with a dual tuner with one input the DTA (stripped down cable box) is not a viable option unless you get a IR blaster and have the AV output addon to the tuner card.  And then you will only get 1 channel to record.

Best thing I have come across is the Silicon Home Run Prime.  It is external and Ethernet based.   It features recoding 3 streams at once.  It ODES require a cablecard (looks similar to the old PCMCIA laptop cards) from your local cable Co.  Cll local Cable Co 1st to see if they have them and the costs per receiver/month.

---

### Post by newlinux on 2014-01-08
Before you purchase the HDHR Prime you should also double check that the channels you want are set to copy freely (CCI setting). Mythtv will only be able to record channels/programs marked copy free in your area with a cable card. The HDHR prime can also record unencrypted QAM without a cable card. Depending your channels desired and their QAM encryption setting this may work for you too (but comcast is moving to encrypting everything everywhere - so cable card is your best bet for now and the future).

---

