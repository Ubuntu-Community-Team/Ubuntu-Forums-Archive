---
title: "2 tuners question"
date: 2010-08-11
forum: Mythbuntu
---

### Post by jrhartley on 2010-08-11
I use to use mythdora 5. My setup included 2 HD tuners .1 was a Dvico fusion 5 and the other a ati. everything worked great.
Then I had a hardware(motherboard) problem and now I have switched to the latest mythbuntu. I cannot get both tuners to work at the same time no matter what I do. If I pull 1 out the other works fine.It doesn't matter which one.so I reinstalled mythdora 5 and they both work.then I went to the latest version of mythdora 10 and they didn't work in there either.did something change in myth tv from mythdora 5 to mythbuntu 12?I know of course they use different flavors of linux but after all my experimentation I believe something had to change in myth tv. can anybody help?

---

### Post by ozybushwalker on 2010-08-11
It would probably help if you gave some more detail on "can't get tuners to work at the same time" and gave some details of your configuration.

I have a dual tuner configuration on a Mythbuntu 10.04 system: Winfast DTV-1000T and Winfast DTV-2000H. RFin of DTV-1000T is connected to the antenna, RFout of the DTV-1000T is connected to RFin of the DTV-2000H. A channel scan on the DTV-1000T picks up a few more channels than a channel scan on the DTV-2000H. I have successfully recorded two shows that ran concurrently on two different "channel groups". I wouldn't be able to record two shows concurrently if they were broadcast on channels seen only by the DTV-1000T. I have also successfully recorded two shows broadcast concurrently on the same digital multiplex and I believe that only one tuner was used for that.

I suspect (but don't have any evidence to back this up) that the reason the channel scan on the DTV-2000H missed a few channels is reduced signal level on the DTV-2000H.

---

### Post by jrhartley on 2010-08-11
thanx for the reply. what mostly happens is when im in mythtv setup,capture cards it will not find them or it says failed to open. when I do this in mythdora 5 card 0 will say dvico and card 1 which is the ati will say air2pc then i go ahead and finish the setup. defining input connections and so forth.now if I only use the dvico it will show up as dvico or if I use the ati it will show up as air2pc.either way they both work one at a time. but if i put them both in I have pthe problems

---

### Post by bance on 2010-08-12
HI jr, 

I am running mythbuntu 10.4, and I had a similar problem, My tuners were different of course (avermedia super 007 / hauppage HVR 4000).

I had to do quite a bit of work to get the avermedia card to work. eventually got it working with mplayer then tried to incorperate it into mythbuntu.

But I could not get them to play nicely together, when both cards were in the machine, the avermedia card came back with errors about incorrect firmware version (in dmesg).

I had to have something working so I've put it aside for the moment, but I've just ordered two new cards.
should get them tommorrow, hopefully they'll all work together!

I remember reading somewhere, that it's a good idea to give the cards specific ID's in the /dev. Can't remember the rational for it , but that was the next route I was going to take in an attempt to solve my issues.

Sorry I haven't been of much help, good luck!

Steve

---

### Post by bance on 2010-08-12
Ok, have found something interesting.....  not where I originally read it but...

> 2010-06-25: My experience with this card is in stark contrast to the  users below. I purchased one of these PEAK cards from a friend at work. I  have installed it in a system with a Nova-T500 and a Nova-S2-HD card. I  have no issues with this card on a new installation of Ubuntu 10.04  with Mythbuntu daily builds running on 0.23-fixes. Occasionally the card  locks up and this has not occurred (in the last few days) since I have  increased the tuning delay on the card from 0ms to 250ms just like the  Nova-T500 card. Firmware activation was prompted when I installed the  card and[COLOR=Green] I locked the card to a DEV location using the options  modprobe.d/options.conf file adding adapter_nr= to the relevant lines  ((options dvb-usb-af9015 adapter_nr=5,6 in my case) to ensure the  multiple cards are always allocated the same logical position for MythTV  to address[/COLOR]. This comes from [[COLOR=Red]_here._[/COLOR]]("http://www.mythtv.org/wiki/Kworld_DVB-T_PC160-2T")

---

### Post by ozybushwalker on 2010-08-13
I don't know the internals of MythtV but it appears likely that it keeps certain information indexed by the device name of the tuner (/dev/dvb/adapter0, /dev/dvb/adapter1 etc). If the tuners are PCI (or PCI Express or Cardbus etc) devices they will always have the same device name unless they are put into different slots. However USB tuners can change their device name depending on what other USB devices are plugged in and when they are detected on the bus. Hence if you have multiple USB tuners it would be a very good idea to use the suggested technique to "lock" the device name to a particular tuner. (This could be a challenge if you are using multiple identical USB tuners - tuner devices with the same USB id codes. A USB device with two tuners in the same package might assign different codes to the two tuners to help distinguish them.)

It could be important to be able to accurately distinguish between different tuners if software needs to take some tuner specific action (e.g. load firmware).

I'm not familiar with the bus type of any of the tuners mentioned so far so I'm uncertain of the relevance of this observation.

---

### Post by jrhartley on 2010-08-17
been gone for a few days....they are both pci and yes i know they get assigned different addresses the problem is when I choose the 1st tuner /dev/dvb/adapter0 then find the card type ati air2pc then lock it in everything is fine so far.then I select the 2nd tuner and set it to /dev/dvb/adapter1 it wont let me.it still says /dev/dvb/adapter0 and device busy. it wont let me change to adapter1

---

### Post by winewood on 2010-08-19
I have also had problems where the logs stated that it could not init the cards upon bootup. I had to stop the frontend, and restart the backend. The hardware was not fully initializing before the box loads the backend, therefore would error out.
 
I can tell you hands down that the BEST and most easy dual tuner to use has been my HDHomerun. I simply plugged it to the antenna, and plugged in a cat5 network cable. Mythbuntu has native support installed. The HDHomerun tuners are already powerd up, and they are availiable at startup for the software. The only software config I had to do was define the adapter0 and 1 as a tuner card.  You can find the dual tuner for $140 retail.
 
If the cards cannot work at the same time, one possible mistake could be defining the same card 2 times with the same string.  Each tuner will have either a different adapter number or tuner number in the device string in capture card setup.  Usally these are numbered "adapter0 and adapter1" (for my install anyway).  I do not have your exact card, but if you have 2 adapter names, look on the next setup window and see if you have a 2 for number of recordings allowed per card, perhaps change that to 1 (suggestion, not definite)

---

### Post by Erlander on 2010-08-22
I recently found that although I have 2 tuners I was only using one.  A second frontend could only tune to channels in the same transport stream as the first frontend was tuned to.

In the backend setup the two tuners were correctly recognised as /dev/dvb/adaptor0/frontend0 and dev/dvb/adaptor1/frontend0

However in Video Sources I needed to setup 2 sources.  I called them Source 1 and Source 2.  In hindsight I should have called them tuner 1 and tuner 2.
Then in Input Connections I had to setup twice.  Once for each source and scan for channels etc twice. ( Once for each source).

Now when watching TV to switch tuners I press M for menu and select Switch Source.  Then I can tune channels in transport streams other than that being used by the first frontend.

---

