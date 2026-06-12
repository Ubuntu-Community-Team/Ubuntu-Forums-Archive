---
title: "No Luck Scanning For ClearQAM with HVR-1800"
date: 2009-08-26
forum: Mythbuntu
---

### Post by yonkiman on 2009-08-26
My situation in easy-to-digest bullet form:

[LIST]
[*]Comcast (in San Jose, CA) went digital a month or so ago and I lost all my analog basic cable channels.
[*]It is not clear to me whether or not Comcast in my area is transmitting anything in ClearQAM or not
[*]I have a Hauppauge HVR-1800 which I hooked up to the cable signal using the RF jack next to the svideo connector which is supposed to be for "ATSC / QAM digital TV"
[*]I configured it in Mythbackend as best I could (I successfully configured my PVR-150 and pcHDTV HD-5500 to work over a year ago, so I'm at least semi-competent)
[*]I scanned, playing with several settings (8-VSB/QAM64/QAM256, frequency tables, etc.), but never saw a single signal.
[/LIST]

So now I wonder:
[LIST]
[*]Is Comcast broadcasting anything in ClearQAM in San Jose?
[*]Did I misconfigure the HVR-1800 in Myth?
[*]Is my HVR-1800 broken?  I've never seen it work, and I've seen reports of the HVR-1800 arriving DOA...
[/LIST]

Having thought and done a bit of research as I wrote this up, I see two experiments I can try:
[LIST]
[*]Switch my pcHDTV HD-5500 from my OTA antenna to cable and see if ***it*** finds anything, and
[*]Switch my HVR-1800 to my antenna and verify it works for ATSC.
[/LIST]

While I'm doing that, if anyone has any tips for getting these cards to work with digital cable TV, please let me know.  If you know anything about whether or not Comcast in San Jose, CA is still broadcasting anything in clearQAM, please let me know that, too!

Thanks,
Fred

---

### Post by jaakan on 2009-08-26
I live on the other coast but I still have comcast.

The first thing I would try is just having HVR-1800 installed in your computer using DVB and no other tuners in the box.
Delete all tuners and just add the one. make sure you have the newest kernel you can get. the reason why is that one version of Mythbuntu i think 8.10 didn't have the drivers for my card ( Hauppauge HVR-1250 -- version 1196  ) if you install the CD without running the updates. after I ran the updates DVB v3 was listed for me...

QAM256 / US-brosdcast / cable full scan

Do you have comcast highspeed internet too? if you don't they might have a filter on your connection.

start here

[http://www.mythtv.org/wiki/Comcast_Users_And_scte65scan](http://www.mythtv.org/wiki/Comcast_Users_And_scte65scan)

[http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_(For_ATSC/QAM_Tuner_Cards_--_USA/Canada)](http://www.mythtv.org/wiki/Adding_Digital_Cable_Channels_(For_ATSC/QAM_Tuner_Cards_--_USA/Canada))

there is a command line scan to look for channels and a step after that to see if there is a "lock" which is good.

if nothing comes up you will need to call comcast, channels that are you can get OTA that they resend should not be blocked nor encrypted or they have a problem.

---

### Post by yonkiman on 2009-08-27
Well I swapped tuner assignments, and the HVR-1800 was able to pick up all the OTA stations the HD-5500 could, and the HD-5500 was able to find a few dozen clearQAM stations - mostly local broadcasts, though - no extended basic channels.

So that answers my questions!  Thanks for the support, jaakan!

-Fred

---

