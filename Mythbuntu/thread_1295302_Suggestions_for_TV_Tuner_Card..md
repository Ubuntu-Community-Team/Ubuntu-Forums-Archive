---
title: "Suggestions for TV Tuner Card."
date: 2009-10-19
forum: Mythbuntu
---

### Post by mars76 on 2009-10-19
Hi All,

  I am trying to setup a mythtv box and i have the following TV Tuner Cards..

  1) PVR-150
  2) Avermedeia A180 (MCE Version with old chipset)

  So far i am unable to make them work. I am still experimenting. I think the issue might be because of the IR Blaster and will get a new IR Blaster and will test again.

  I also have the Dishnetwork provided dishes and wondering whether getting a DVB-T Card will help in getting any free channels.

 What's the best card that works with mythbuntu which is of type DVB-T.

Thanks
mars

---

### Post by tgm4883 on 2009-10-19
> **mars76 said:**
> Hi All,

  I am trying to setup a mythtv box and i have the following TV Tuner Cards..

  1) PVR-150
  2) Avermedeia A180 (MCE Version with old chipset)

  So far i am unable to make them work. I am still experimenting. I think the issue might be because of the IR Blaster and will get a new IR Blaster and will test again.

  I also have the Dishnetwork provided dishes and wondering whether getting a DVB-T Card will help in getting any free channels.

 What's the best card that works with mythbuntu which is of type DVB-T.

Thanks
mars

Well DVB-T would be Terrestrial, which isn't what you want, DVB-S would be for satellite, Although I don't think that would work with Dish Network.

---

### Post by bsntech on 2009-10-19
Are you only using these with Dish Network and do not have over-the-air or cable service?

over-the-air requires a digital card - which the PVR-150 is not.  However, the PVR-150 should work with the Dish Network box.  Ensure that you go into the MythTV Backend and setup the card - it should be listed as /dev/video0.

After setting that up, you will need to create a video source.  Now since you are using a dish box, when you scan for channels - you will only get a 'hit' on one channel - channel 3 or 4 - or whatever channel your Dish box is set to provide the signal on.

Lastly, ensure that you choose the input connection.  On the Tuner 1 selection, ensure you select your just created video source.

---

### Post by luigidk on 2009-10-19
I have the exact same tuner cards and just updated from a 7.10 ubuntu box built by Monolithmc.

When running 9.04 mythbuntu I am only able to run with the PVR-150 - the avermedia card kills any capture.

Is that what is happening with you?

I'm looking into hdhomerun to replace the avermedia a180.  Might be a decent solution for now - until I get a new box that can handle an HD-PVR.

---

### Post by mars76 on 2009-10-20
Hi All,

  Thanks for your responses..

  I no longer have Dish network and i am planning to use the OTA Receiver with these dishes. And i have FIOS HDTV STB which i am planning to connect to Aver media HDTV. 

  I tried with PVR-150 and AverMedia A180 MCE Version with no luck so far.  With PVR-150 the backend reports it cannot change the channel.

luigidk: When i added the AverMedia PCI Card the PVR-150 is no longer recognized so i am unable to make both cards work at the same time.

  I will post the detailed logs once i get back to home..

Thanks
mars

---

### Post by fenian on 2009-10-21
Both the PVR-15 and A180 cards are analog only.There are no more analog signals in the U.S.A. they have all switched to HD.In order to use those cards you need a set top box from a cable/satellite provider (you may also be able to use them with a hdtv converter box but I have no experience with that).If you want to grab OTA signals (ATSC) you need a HD card.

---

