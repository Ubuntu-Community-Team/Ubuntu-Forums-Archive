---
title: "Scanning for QAM in 0.22 difficulties"
date: 2009-11-01
forum: Mythbuntu
---

### Post by Boppy3125 on 2009-11-01
I am having real troubles.  In 0.21 it was pretty easy, just scan for QAM-256 and it finds my channels plus some that I delete, then label and add XMLTV ids.  Not so easy in 0.22.

What is this "Found 1 old SCTE"???  Then "Found 21 new non-conflicting SCTE channels."  Then "Found 2 new conflicting ATSC channels."  And then "Found 2 conflicting old ATSC channels."  And then it was more conflicting SCTE and then "Found 13 unused transports."

Through trial and error I have figured out which transports I need.  (A combination of Silicon Dust website and futzing around with scanning on individual transports.)  I need to be able to look for channels on these specific frequencies but I can't figure it out.  I can do a Scan Type of single transport, but it only lets me choose from a small list of them.

How do I add a transport to scan?

---

### Post by Boppy3125 on 2009-11-01
In case you are wondering, my backend has a Dvico FusionHDTV5 RT Gold.  I also have a Hauppauge PVR150 for my lower channels in SD, but that is working just fine.  I am connecting to Time Warner cable.  I should have all my locals which comes to something like 13 channels when you count all the weather sub-channels and whatnot.  Right now, I have 6 configured with 2 transports it managed to get right.  I have 4 other transports currently giving me garbage and there are 4 that I am trying to get to for my remaining channels.  Any ideas on adding transports?

Boy, from my perspective, 0.22 is a big step down from 0.21 for tuning QAM channels.

---

### Post by Boppy3125 on 2009-11-01
I have made some progress but still have some serious issues.  Once I had my list of all the known QAM channels via SiliconDust.com/hdhomerun/channels_us, I worked out that channel 83 was on 570 MHz and each channel is 6 MHz apart.  So I knew which transports to use, and set those up in the backend setup, channel editor.  Now I had the transports I needed, I did individual scans one transport at a time, adding the SCTE or ATSC channels it found.  Then I made my best guess which channels it added each time and edited them giving the desired channel and XMLTV ids.

Now I have two problem.  On one of my transports I am expecting probably two channels (NBC HD channel plus a multiplexed weather channel.)  I could imagine they dropped the weather channel, but I need to find the HD channel.  It works on my Toshiba TV upstairs that uses QAM.  Well, when I scan this transport I only get 1 MPEG channel.  This is only only place I see MPEG.  When I go back to the frontend and try to tune it, it looks like it is trying and finally fails.  I could get the specific errors if that would help.  Anyone seen anything like this before?

Next problem, adding the channels this way seems to have broke something.  None of these channels show up in the channel guide.  I can type the numbers and they tune in, but I can't use the EPG and I can't use up and down to change channels.  This only started when I add my own transports.  That doesn't add up to me though.  I had the guide working for the 4 or 5 channels I was finding earlier today.

---

### Post by Boppy3125 on 2009-11-01
The reason they weren't in the guide is after the MPEG channel, it caused all the existing channels to get their "Visible" box un-checked.  So guide is back and channel up/down is working.  Of course now all my recording that I had previously on these channels are orphaned.  Anyone know how to fix them and update the channel for them?

---

