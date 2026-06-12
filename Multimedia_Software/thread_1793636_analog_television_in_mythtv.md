---
title: "analog television in mythtv"
date: 2011-06-29
forum: Multimedia Software
---

### Post by maryhigginsrice on 2011-06-29
[SIZE=2]Hi everyone.  I am trying to watch tv on my monitor with mythtv.  I had my card configured correctly.  The first half of the Hauppauge 1600 is for analog tuning, so I have to select ivtv from the dropdown menu.  I am receiving an error message stating that it cannot be opened.  An hour ago It was fine.  When It was working fine and everything was normal, I still could not receive any video on the tv. in mythtv.  I receive a red screen.  The coax cable is running from the wall into the card.  I do not want to run it through my cable box for it seems difficult to configure a remote.  I went to schedule direct and downloaded the correct guide for my region(which is the US).  What could be the problem?  I have searched forums and articles.  I really want to use mythtv and cease using Windows Media Center.  Does analog tv work in Mythtv.  I am using the 0.24 version.  My operating system is windows xp and I do not have a graphics card setup for tv-out yet.  [/SIZE]I have spent numerous days trying to get to work.  Any help will be appreciated.  mary:(

---

### Post by BicyclerBoy on 2011-06-29
As you have stated..Your tuner card has 2 separate components.
IVTV mpeg2 encoder & DVB DTV device.
This card is used for analogue NTSC RF Free-to-Air capture/encode & ATSC DVB receiver.

If you were using a cable box, do you not have use Clear QAM & DVB tuner ?
Quote from MythTV wiki:
"Some of the HVR-1600's (product code 74021 and 74041 found on the tuner  label) also support Clear QAM, which is most likely the stuff your cable  company uses for your local HD channels"

Can you go through this setup procedure..
[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

How could it have been working (1 hr ago) when you only had a red screen ?
Have you ran any system updates in the last few hours ?

There is a mythbuntu forum hidden right here at Ubuntu forums under "3rd party projects".
Those guys might be more able to help..

---

### Post by maryhigginsrice on 2011-06-29
Hi Bicyclerboy. In the configuration of the card one is suppose to pick ivtv instead of v4l.  An hour ago it was ivtv and the system could probe it.  Now I can not change it type of card to ivtv.  It is v4l and it is useless to the system.  mary.

---

### Post by BicyclerBoy on 2011-06-29
Hi Mary
Have you run any updates recently..kernel or mythtv ?

I'm not sure your problem is this..but

There have been some changes in the recent linux kernels with respect to the handling of the old v4l (1) support..
This is affecting analogue video capture where the drivers are still using video4linux (1) & not v4l2.

The card probing should be recorded kernel logs & in
dmesg

In that output you should find messages:
finding identify card
driver loading
firmware loading
tuners available
IR remote stuff.

---

