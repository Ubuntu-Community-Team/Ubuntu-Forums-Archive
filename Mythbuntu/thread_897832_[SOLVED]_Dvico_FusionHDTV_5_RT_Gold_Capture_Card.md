---
title: "[SOLVED] Dvico FusionHDTV 5 RT Gold Capture Card"
date: 2008-08-22
forum: Mythbuntu
---

### Post by dmdbdd on 2008-08-22
[LIST=1]
[*]In the Capture Card Setup window, under Card Type - what card type should I select? I have tried every selection that recognizes my card and have not been able to watch TV yet :(  I know that this card works very will with my PC configuration as I have been very successful using it with Sage TV, SnapStream and FusionHDTV. BTW, with all of these three XP based applications, I was able to setup in an hour or less and was watching TV. I have invested a minimum of 60 hours in Mythbuntu and haven't been able to watch one TV show :mad: I'm only resorting to Myth because none of the XP applications handle commercial skip very well or not at all.
[*]I don't see a option for OTA (antenna), so I'm assuming that Television is the correct selection for Default Input?
[/LIST]

Regards,

dmdbdd

---

### Post by newlinux on 2008-08-22
What types of signals are your trying to tune? If you are trying to tune ATSC (OTA digital) or QAM stations you should select DVB. If you want NTSC you should select V4L. I'm guessing you want ATSC OTA. If so, you'll want to scan using 8 VSB and broadcast in your scan settings.

---

### Post by dmdbdd on 2008-08-22
[LEFT]OK, I found this link [http://www.mythtv.org/wiki/index.php/DViCO_FusionHDTV5_Gold](http://www.mythtv.org/wiki/index.php/DViCO_FusionHDTV5_Gold), and the very first thing I see in the Mythtv Setup section is that in the General Setup window I should set the Type to ATSC. Now I have nothing in the General Setup screens labeled 'Type', so I'm assuming that this would be the TV Format entry. This leads to the next problem, as under the TV Format entry there is no ATSC. 

So I have been using the NTSC format (type). Is this correct?

Next I don't see any entry/display for 'Video Device' - the Frontend ID looks correct. I also do not have any Probed info displayed as this link shows - see below.[INDENT]     Frontend ID: DViCO v2 or Air2PC v3 or pcHDTV HD-5500 Subtype ...
 Analog Options
       Video device: /dev/video
[/INDENT][INDENT] Probed info: BT878 video (DViCO FusionHDTV 5 [bttv])
       VBI device: /dev/vbi
       Audio device: /dev/dsp1
       Audio sampling rate: (None)    (unchecked) Do not adjust volume
       Default input: Television
[/INDENT]In addition I don't have any of the input connection information displayed as this link shows - see below. In it's place is I have a 'DisEqc' entry.[INDENT]        [DVB]:0] (DVBInput) -> Digital
       ->[V4L:/dev/video0](Television)-> Analog
       ->[V4L:/dev/video0](Composite1)-> (None)
       ->[V4L:/dev/video0](S-Video)-> (None)
[/INDENT]So if Mythbuntu uses Mythtv why do I not see the same setup screens as Mythtv says I should?
[/LEFT]

---

### Post by newlinux on 2008-08-22
There will be some differences because the link you are using is from an older version of mytthv than mythbuntu uses (the input connections will be different, I think Analog options no longer exists in favor of using input groups and setting up the card as two different inputs to get analog and digital). Also, unless you have gone through all of the setup steps (capture cards, video sources, input connections) you won't see all of those "screens" because they are not all in the same menu in the old myth  (.20) or the new myth in mythbuntu (.21).

So can you confirm you are trying to tune digital over the air stations?
If so, all you need to do on the capture card setup screen is select the dvb driver.

then go to the video sources and define a source for your digital stations.

then go to input connection and associate the video source with the card (you should have an input of DVB[0] to select). Then scan for channels.

If you want analog stations as well create a another capture card using the V4L driver. Then you will need to setup your input groups to prevent the card from being used as an analog and digital tuner at the same time. but for now, you should just start with the digital OTA if that is what you want to tune.

---

